---
title: Configurar um projeto
description: Saiba como configurar o seu projeto para gerenciá-lo e implantá-lo com o Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 94%

---


# Configurar um projeto {#setting-up-your-project}

Saiba como configurar o seu projeto para gerenciá-lo e implantá-lo com o Cloud Manager.

## Editar projetos existentes {#modifying-project-setup-details}

Os projetos do AEM existentes precisam seguir algumas regras básicas para serem compilados e implantados com sucesso com o Cloud Manager.

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

## Ativar perfis do Maven no Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Em alguns casos limitados, pode ser necessário variar um pouco o processo de criação ao executar no Cloud Manager, comparado à quando ele é executado em estações de trabalho de desenvolvedor. Para estes casos, [perfis Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) podem ser usados para definir como o processo de criação deve ser diferente em ambientes distintos, incluindo o Cloud Manager.

Para ativar um perfil do Maven no ambiente de build do Cloud Manager, é necessário procurar a `CM_BUILD` [variável de ambiente](/help/getting-started/build-environment.md#environment-variables). Por outro lado, um perfil destinado a ser usado somente fora do ambiente de build do Cloud Manager deve ser ativado procurando a ausência dessa variável.

Por exemplo, se você quiser gerar uma mensagem simples apenas quando o build for executado no Cloud Manager, faça o seguinte:

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

Se você quiser gerar uma mensagem simples somente quando o build for executado fora do Cloud Manager, faça o seguinte:

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

## Suporte ao repositório do Maven protegido por senha {#password-protected-maven-repositories}

Os artefatos de um repositório do Maven protegido por senha devem ser usados com cuidado, pois o código implantado dessa maneira não está totalmente sujeito às verificações de qualidade aplicadas pelos portais de qualidade do Cloud Manager. A Adobe também aconselha implantar as fonte de Java e todo o código-fonte do projeto junto com o binário.

>[!TIP]
>
>Artefatos de repositórios Maven protegidos por senha devem ser usados somente em casos raros e para códigos não vinculados ao AEM.

Para usar um repositório Maven protegido por senha do Cloud Manager, especifique a senha (e, opcionalmente, o nome de usuário) como uma [Variável de pipeline](/help/getting-started/build-environment.md#pipeline-variables) secreta e depois faça referência a esse segredo dentro de um arquivo chamado `.cloudmanager/maven/settings.xml` no repositório Git. Esse arquivo segue o esquema do [Arquivo de configurações Maven](https://maven.apache.org/settings.html).

Quando o processo de build do Cloud Manager é iniciado, o elemento `<servers>` desse arquivo é mesclado com o arquivo `settings.xml` padrão fornecido pelo Cloud Manager. Servidores personalizados não devem usar IDs de servidor que comecem com `adobe` e `cloud-manager`. Esses IDs são considerados reservados. O Cloud Manager espelha somente os IDs de servidor que correspondem a um dos prefixos especificados ou ao ID `central` padrão.

Com esse arquivo definido, a ID do servidor seria referenciada de dentro de um elemento `<repository>` e/ou `<pluginRepository>`, que está dentro do arquivo `pom.xml`. Geralmente, estes elementos `<repository>` e/ou `<pluginRepository>` ficariam contidos dentro de um [perfil específico do Cloud Manager](#activating-maven-profiles-in-cloud-manager), embora isso não seja estritamente necessário.

Por exemplo, se o repositório estiver em `https://repository.myco.com/maven2`, o nome de usuário que o Cloud Manager deve usar é `cloudmanager` e a senha é `secretword`.

Primeiro, defina a senha como um segredo no pipeline:

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

Em seguida, faça referência ao seguinte no arquivo `.cloudmanager/maven/settings.xml`:

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

E, por fim, referencie o ID do servidor dentro do arquivo `pom.xml`:

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

### Implantar fontes {#deploying-sources}

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

### Implantar fontes do projeto {#deploying-project-sources}

É uma boa prática implantar toda a fonte do projeto juntamente com o binário em um repositório do Maven. Dessa forma, é possível reconstruir o artefato exato.

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

No Cloud Manager, as compilações podem produzir qualquer número de pacotes de conteúdo. Por uma variedade de motivos, pode ser desejável produzir um pacote de conteúdo, mas não implantá-lo. Por exemplo, essa abordagem pode ser útil quando você cria pacotes de conteúdo exclusivamente para teste ou quando outra etapa do processo de build refaz o pacote. Ou seja, na forma de um subpacote de outro pacote.

Nessas hipóteses, o Cloud Manager procurará por uma propriedade chamada `cloudManagerTarget` nas propriedades dos pacotes de conteúdo criados. Se essa propriedade for definida como `none`, o pacote será ignorado e não será implantado. O mecanismo para definir essa propriedade depende da forma em que o build produz o pacote de conteúdo. Por exemplo, com o `filevault-maven-plugin`, você configuraria o plug-in da seguinte maneira:

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

Em muitos casos, um mesmo código é implantado em vários ambientes do AEM. Sempre que possível, o Cloud Manager evita reconstruir a base de código quando detecta que a mesma Git commit é usada em várias execuções de pipeline de pilha completa.

Quando uma execução é iniciada, é extraído. o commit HEAD atual do pipeline do branch (ramificação). O hash do commit fica visível na interface e por meio da API. Quando a etapa de compilação for concluída com sucesso, os artefatos resultantes serão armazenados com base nesse hash de confirmação e poderão ser reutilizados em execuções de pipeline subsequentes.

Os pacotes serão reutilizados nos pipelines, se estiverem no mesmo programa. Ao procurar pacotes que possam ser reutilizados, o AEM ignora ramificações e reutiliza artefatos entre ramificações.

Quando ocorre uma reutilização, as etapas de compilação e qualidade do código são efetivamente substituídas pelos resultados da execução original. O arquivo de log da etapa do build listará os artefatos e as informações de execução que foram usadas originalmente para criá-los.

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

1. A execução do pipeline 1 primeiro criará os pacotes normalmente.
1. Em seguida, a execução do pipeline 2 reutilizará os pacotes criados pelo pipeline 1.

#### Exemplo 2 {#example-2}

Imagine que o seu programa tem duas ramificações: ramificação `foo` e ramificação `bar`.

Ambas as ramificações têm a mesma ID de confirmação.

1. Um pipeline de desenvolvimento compila e executa `foo`.
1. Posteriormente, um pipeline de produção criará e executará `bar`.

Nesse caso, o artefato de `foo` será reutilizado para o pipeline de produção, pois o mesmo hash de commit foi identificado.

### Recusar {#opting-out}

Se desejado, o comportamento de reutilização pode ser desabilitado para pipelines específicos, definindo a variável de pipeline `CM_DISABLE_BUILD_REUSE` como `true`. Se essa variável for definida, o hash de commit ainda será extraído. Os artefatos resultantes são armazenados para uso posterior, mas os artefatos armazenados anteriormente não são reutilizados. Para entender esse comportamento, considere o seguinte exemplo:

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
* [O manuseio de versão do Maven](/help/managing-code/maven-project-version.md) substitui a versão do projeto somente em pipelines de produção. Se o mesmo commit for usado para pipelines de desenvolvimento e produção, e o pipeline de desenvolvimento for executado primeiro, as versões serão implantadas no estágio e na produção inalteradas. No entanto, ainda será criada uma tag nesse caso.
* Se a recuperação dos artefatos armazenados não for bem-sucedida, a etapa de build será executada como se nenhum artefato tivesse sido armazenado.
* Variáveis de pipeline diferentes de `CM_DISABLE_BUILD_REUSE` não são consideradas quando o Cloud Manager decide reutilizar artefatos de build criados anteriormente.

## Desenvolver ódigo com base nas práticas recomendadas {#develop-your-code-based-on-best-practices}

As equipes de engenharia e consultoria da Adobe desenvolveram um [conjunto abrangente de práticas recomendadas para desenvolvedores do AEM](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/developing/bestpractices/best-practices).
