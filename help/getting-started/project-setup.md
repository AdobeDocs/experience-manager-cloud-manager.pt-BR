---
title: Configuração do projeto
description: Saiba como configurar seu projeto para gerenciá-lo e implantá-lo com o Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 100%

---


# Configuração do projeto {#setting-up-your-project}

Saiba como configurar seu projeto para gerenciá-lo e implantá-lo com o Cloud Manager.

## Modificação de projetos existentes {#modifying-project-setup-details}

Os projetos AEM existentes precisam seguir algumas regras básicas para serem montados e implantados com sucesso com o Cloud Manager.

* Os projetos devem ser criados usando o Apache Maven.
* Deve haver um arquivo `pom.xml` na raiz do repositório Git.
   * Esse arquivo `pom.xml` pode se referir a quantos submódulos (que, por sua vez, podem ter outros módulos derivados) forem necessários.
   * Você pode adicionar referências a repositórios de artefatos Maven adicionais em seu arquivos `pom.xml`.
   * O acesso a [repositórios de artefatos protegidos por senha](#password-protected-maven-repositories) é suportado quando configurado. No entanto, o acesso a repositórios de artefatos protegidos pela rede não é permitido.
* Pacotes de conteúdo implantáveis são descobertos pela varredura de arquivos de pacote de conteúdo (.zip) contidos em um diretório chamado `target`.
   * Qualquer número de submódulos pode produzir pacotes de conteúdo.
* Os artefatos do Dispatcher que podem ser implantados são descobertos ao verificar arquivos `zip` que continham subdiretórios de `target` nomeados como `conf` e `conf.d`.
* Se houver mais de um pacote de conteúdo, a ordem de implantação dos pacotes não será garantida.
* Se uma ordem específica for necessária, as dependências do pacote de conteúdo poderão ser usadas para definir a ordem.
* Os pacotes podem ser [ignorados](#skipping-content-packages) na implantação.

## Ativar perfis Maven no Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Em alguns casos limitados, pode ser necessário variar um pouco o processo de criação ao executar no Cloud Manager, comparado à quando ele é executado em estações de trabalho de desenvolvedor. Para estes casos, [perfis Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) podem ser usados para definir como o processo de criação deve ser diferente em ambientes distintos, incluindo o Cloud Manager.

A ativação de um perfil Maven no ambiente de criação do Cloud Manager deve ser feita procurando pela [variável de ambiente](/help/getting-started/build-environment.md#environment-variables) `CM_BUILD`. Por outro lado, um perfil destinado a ser usado somente fora do ambiente de criação do Cloud Manager deve ser ativado procurando a ausência dessa variável.

Por exemplo, se você quiser gerar uma mensagem simples apenas quando a build for executada no Cloud Manager, faça o seguinte:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Para testar esse perfil em uma estação de trabalho de desenvolvedor, você pode habilitá-lo na linha de comando (com `-PcmBuild`) ou em um ambiente de desenvolvimento integrado (IDE).

E se você quiser gerar uma mensagem simples somente quando a build for executada fora do Cloud Manager, faça o seguinte:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Suporte ao repositório Maven protegido por senha {#password-protected-maven-repositories}

Os artefatos de um repositório Maven protegido por senha devem ser usados com muito cuidado, pois o código implantado por meio desse mecanismo não é executado por todas as regras de qualidade implementadas nas portas de qualidade do Cloud Manager. É recomendável também implantar as fontes Java, bem como todo o código-fonte do projeto junto com o binário.

>[!TIP]
>
>Artefatos de repositórios Maven protegidos por senha devem ser usados somente em casos raros e para códigos não vinculados ao AEM.

Para usar um repositório Maven protegido por senha do Cloud Manager, especifique a senha (e, opcionalmente, o nome de usuário) como uma [variável de pipeline](/help/getting-started/build-environment.md#pipeline-variables) secreta e depois faça referência a esse segredo dentro de um arquivo chamado `.cloudmanager/maven/settings.xml` no repositório Git. Esse arquivo segue o esquema do [Arquivo de configurações Maven](https://maven.apache.org/settings.html).

Quando o processo de criação do Cloud Manager é iniciado, o elemento `<servers>` neste arquivo é mesclado ao arquivo padrão `settings.xml` fornecido pelo Cloud Manager. IDs de servidor que começam com `adobe` e `cloud-manager` são consideradas reservadas e não devem ser usadas por servidores personalizados. IDs de servidor que não correspondem a um desses prefixos ou a ID padrão `central` nunca serão espelhados pelo Cloud Manager.

Com esse arquivo definido, a ID do servidor seria referenciada de dentro de um elemento `<repository>` e/ou `<pluginRepository>`, que está dentro do arquivo `pom.xml`. Geralmente, estes elementos `<repository>` e/ou `<pluginRepository>` ficariam contidos dentro de um [perfil específico do Cloud Manager](#activating-maven-profiles-in-cloud-manager), embora isso não seja estritamente necessário.

Como exemplo, digamos que o repositório esteja em `https://repository.myco.com/maven2`, o nome de usuário que o Cloud Manager deve usar é `cloudmanager` e a senha é `secretword`.

Primeiro, defina a senha como um segredo no pipeline:

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

Em seguida, faça referência a isso no arquivo `.cloudmanager/maven/settings.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

E, por fim, referencie a ID do servidor dentro do arquivo `pom.xml`:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### Implantação de fontes {#deploying-sources}

É uma boa prática implantar as fontes Java junto com o binário em um repositório Maven.

Configure o `maven-source-plugin` no seu projeto:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### Implantações de fontes de projeto {#deploying-project-sources}

É uma boa prática implantar toda a origem do projeto junto com o binário em um repositório Maven. Dessa forma, é possível reconstruir o artefato exato.

Configure o `maven-assembly-plugin` no seu projeto:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## Ignorar pacotes de conteúdo {#skipping-content-packages}

No Cloud Manager, as builds podem produzir qualquer número de pacotes de conteúdo. Por uma variedade de motivos, pode ser desejável produzir um pacote de conteúdo, mas não implantá-lo. Isso pode ser útil, por exemplo, ao criar pacotes de conteúdo usados apenas para teste ou que serão “reembalados” por outra etapa no processo de criação, ou seja, como um subpacote de outro pacote.

Para acomodar esses cenários, o Cloud Manager procurará uma propriedade chamada `cloudManagerTarget` nas propriedades dos pacotes de conteúdo incorporados. Se essa propriedade estiver definida como `none`, o pacote será ignorado e não será implantado. O mecanismo para definir essa propriedade depende da forma como a compilação está produzindo o pacote de conteúdo. Por exemplo, com o `filevault-maven-plugin`, você configuraria o plug-in da seguinte maneira:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Com o `content-package-maven-plugin`, o processo é semelhante:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## Reutilização de artefato de build {#build-artifact-reuse}

Em muitos casos, um mesmo código é implantado em vários ambientes do AEM. Sempre que possível, o Cloud Manager evitará reconstruir a base de código quando detectar que a mesma Git Commit é usada em várias execuções de pipeline de pilha completa.

Quando uma execução é iniciada, a confirmação HEAD atual para o pipeline de ramificação é extraída. O hash de confirmação fica visível na interface do usuário e por meio da API. Quando a etapa de compilação for concluída com sucesso, os artefatos resultantes serão armazenados com base nesse hash de confirmação e poderão ser reutilizados em execuções de pipeline subsequentes.

Os pacotes serão reutilizados nos pipelines, se estiverem no mesmo programa. Ao procurar pacotes que possam ser reutilizados, o AEM ignora ramificações e reutiliza artefatos entre ramificações.

Quando ocorre uma reutilização, as etapas de compilação e qualidade do código são efetivamente substituídas pelos resultados da execução original. O arquivo de log da etapa de compilação listará os artefatos e as informações de execução que foram usadas originalmente para criá-los.

Veja a seguir um exemplo do log gerado.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

O log da etapa de qualidade do código conterá informações semelhantes.

### Exemplos {#example-reuse}

#### Exemplo 1 {#example-1}

Considere que seu programa tem dois pipelines de desenvolvimento:

* Pipeline 1 na ramificação `foo`
* Pipeline 2 na ramificação `bar`

Ambas as ramificações estão na mesma ID de confirmação.

1. A execução do pipeline 1 por primeiro criará os pacotes normalmente.
1. Em seguida, a execução do pipeline 2 reutilizará os pacotes criados pelo pipeline 1.

#### Exemplo 2 {#example-2}

Considere que seu programa tem duas ramificações:

* Ramificação `foo`
* Ramificação `bar`

Ambas as ramificações têm a mesma ID de confirmação.

1. Um pipeline de desenvolvimento compila e executa `foo`.
1. Posteriormente, um pipeline de produção compila e executa `bar`.

Nesse caso, o artefato de `foo` será reutilizado para o pipeline de produção, desde que o mesmo hash de confirmação tenha sido identificado.

### Recusa {#opting-out}

Se desejado, o comportamento de reutilização pode ser desativado para pipelines específicos, definindo a variável de pipeline `CM_DISABLE_BUILD_REUSE` como `true`. Se essa variável for definida, o hash de confirmação ainda será extraído e os artefatos resultantes serão armazenados para uso posterior, mas todos os artefatos armazenados anteriormente não serão reutilizados. Para entender esse comportamento, considere o cenário a seguir.

1. Um novo pipeline é criado.
1. O pipeline é executado (execução nº 1) e a confirmação HEAD atual é `becdddb`. A execução é bem-sucedida e os artefatos resultantes são armazenados.
1. A variável `CM_DISABLE_BUILD_REUSE` está definida.
1. O pipeline é executado novamente sem alterar o código. Embora haja artefatos armazenados associados a `becdddb`, eles não serão reutilizados devido à variável `CM_DISABLE_BUILD_REUSE`.
1. O código é alterado e o pipeline é executado. A confirmação HEAD agora é `f6ac5e6`. A execução é bem-sucedida e os artefatos resultantes são armazenados.
1. A variável `CM_DISABLE_BUILD_REUSE` é excluída.
1. O pipeline é executado novamente sem alterar o código. Como há artefatos armazenados associados a `f6ac5e6`, esses artefatos são reutilizados.

### Avisos {#caveats}

* Os artefatos de compilação não são reutilizados em diferentes programas, independentemente de o hash de confirmação ser idêntico.
* Os artefatos de build são reutilizados no mesmo programa mesmo se a ramificação e/ou o pipeline for diferente.
* [O manuseio de versão do Maven](/help/managing-code/maven-project-version.md) substitui a versão do projeto somente em pipelines de produção. Portanto, se a mesma confirmação for usada em uma execução de implantação de desenvolvimento e em uma execução de pipeline de produção e o pipeline de implantação de desenvolvimento for executado primeiro, as versões serão implantadas no estágio e na produção sem serem alteradas. No entanto, uma tag ainda será criada nesse caso.
* Se a recuperação dos artefatos armazenados não for bem-sucedida, a etapa de compilação será executada como se nenhum artefato tivesse sido armazenado.
* Variáveis de pipeline diferentes de `CM_DISABLE_BUILD_REUSE` não são consideradas quando o Cloud Manager decide reutilizar artefatos de build criados anteriormente.

## Desenvolver seu código com base nas práticas recomendadas {#develop-your-code-based-on-best-practices}

As equipes de engenharia e consultoria da Adobe desenvolveram um [conjunto abrangente de práticas recomendadas para desenvolvedores do AEM.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/bestpractices/best-practices.html?lang=pt-BR)
