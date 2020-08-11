---
title: Criar um projeto de aplicativo AEM
seo-title: Criar um projeto de aplicativo AEM
description: 'null'
seo-description: Siga esta página para saber mais sobre como configurar um projeto AEM ao começar a usar o Cloud Manager.
uuid: 7b976ebf-5358-49d8-a58d-0bae026303fa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 76c1a8e4-d66f-4a3b-8c0c-b80c9e17700e
translation-type: tm+mt
source-git-commit: e026c7232c2a848bb60ddbd7112a4a2755527921
workflow-type: tm+mt
source-wordcount: '1721'
ht-degree: 6%

---


# Criar um projeto de aplicativo AEM {#create-an-aem-application-project}

## Usando o Assistente para Criar um Projeto de Aplicativo AEM {#using-wizard-to-create-an-aem-application-project}

Quando os clientes são embarcados no Cloud Manager, eles recebem um repositório git vazio. Os clientes atuais do Adobe Managed Services (AMS) (ou clientes no local AEM que estão migrando para o AMS) geralmente já terão o código do projeto em git (ou outro sistema de controle de versão) e importarão seu projeto para o repositório git do Cloud Manager. Novos clientes, no entanto, não têm projetos existentes.

Para ajudar a iniciar novos clientes, o Cloud Manager agora pode criar um projeto de AEM mínimo como ponto de partida. Esse processo se baseia no [**AEM Project Archetype **](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Siga as etapas abaixo para criar um projeto de aplicativo AEM no Cloud Manager:

1. Quando você fizer logon no Cloud Manager e a configuração básica do programa for concluída, uma chamada especial para o cartão de ação será exibida na tela **Visão geral** se o repositório estiver vazio.

   ![](assets/image2018-10-3_14-29-44.png)

1. Clique em **Criar para** abrir uma caixa de diálogo, que permite ao usuário fornecer os parâmetros exigidos pelo AEM Project Archetype. Em seu formulário padrão, a caixa de diálogo solicita dois valores:

   * **Título** - por padrão, está definido como Nome do *Programa*

   * **Novo nome** da ramificação - por padrão, isso é *principal*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça em direção à parte inferior da caixa de diálogo. Em seu formulário expandido, a caixa de diálogo mostra todos os parâmetros de configuração para o Archetype. Muitos desses parâmetros têm valores padrão que são gerados com base no **Título**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Por exemplo, se o **Título** for ***We.Finance***, o parâmetro de Id de artefato da base de Maven é gerado como ***com.wefinance***. Esses valores podem ser alterados, se desejado.
   >
   >
   >Por exemplo, você pode alterar do ***valor gerado com.wefinance*** para ***net.wefinance***.

1. Clique em **Criar** na etapa anterior para criar o projeto inicial usando o arquétipo e confirmando o ramo git nomeado. Quando isso estiver feito, você poderá configurar o pipeline.

## Configuração do projeto {#setting-up-your-project}

### Modificando Detalhes de Configuração do Projeto {#modifying-project-setup-details}

Para ser criado e implantado com êxito com o Cloud Manager, os projetos AEM existentes precisam seguir algumas regras básicas:

* Os projetos devem ser construídos com o Apache Maven.
* Deve haver um arquivo *pom.xml* na raiz do repositório Git. Esse arquivo *pom.xml* pode fazer referência a quantos submódulos (que por sua vez podem ter outros submódulos etc.) conforme necessário.

* Você pode adicionar referências a repositórios de artefatos Maven adicionais em seus arquivos *pom.xml* . O acesso a repositórios [de artefatos protegidos por](#password-protected-maven-repositories) senha é suportado quando configurado. No entanto, o acesso a repositórios de artefatos protegidos pela rede não é suportado.
* Os pacotes de conteúdo implantáveis são detectados ao verificar se há arquivos *zip* do pacote de conteúdo contidos em um diretório chamado *público alvo*. Qualquer número de submódulos pode produzir pacotes de conteúdo.

* Os artefatos do Dispatcher que podem ser implantados são descobertos pela varredura de arquivos *zip* (novamente, contidos em um diretório chamado *público alvo*) que têm diretórios chamados *conf* e *conf.d*.

* Se houver mais de um pacote de conteúdo, a ordem de implantações de pacote não é garantida. Se uma ordem específica for necessária, as dependências do pacote de conteúdo poderão ser usadas para definir a ordem. Os pacotes podem ser [ignorados](#skipping-content-packages) da implantação.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Criar detalhes do Ambiente {#build-environment-details}

O Cloud Manager cria e testa seu código usando um ambiente de compilação especializado. Esse ambiente tem os seguintes atributos:

* O ambiente build é baseado no Linux, derivado do Ubuntu 18.04.
* O Apache Maven 3.6.0 está instalado.
* As versões do Java instaladas são o Oracle JDK 8u202 e 11.0.2.
* Existem outros pacotes de sistema instalados que são necessários:

   * bzip2
   * descompactar
   * libpng
   * imagemagick
   * gráfico

* Outros pacotes podem ser instalados no momento da criação, conforme descrito [abaixo](#installing-additional-system-packages).
* Cada obra é feita com um ambiente intocado; o container build não mantém nenhum estado entre as execuções.
* Maven é sempre executado com o comando: *mvn —batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* O Maven é configurado no nível do sistema com um arquivo settings.xml que inclui automaticamente o repositório público do **Artefato** de Adobe. (Consulte o Repositório [Adobe Public Maven](https://repo.adobe.com/) para obter mais detalhes).

>[!NOTE]
>Embora o Gerenciador de nuvem não defina uma versão específica do `jacoco-maven-plugin`, a versão usada deve ser pelo menos `0.7.5.201505241946`.

### Uso do Java 11 {#using-java-11}

O Cloud Manager agora é compatível com a criação de projetos de clientes com Java 8 e Java 11. Por padrão, os projetos são criados usando o Java 8. Os clientes que pretendem usar o Java 11 em seus projetos podem fazer isso usando o plug-in [](https://maven.apache.org/plugins/maven-toolchains-plugin/)Apache Maven Toolchain.

Para fazer isso, no arquivo pom.xml, adicione uma `<plugin>` entrada com a seguinte aparência:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-toolchains-plugin</artifactId>
            <version>1.1</version>
            <executions>
                <execution>
                    <goals>
                        <goal>toolchain</goal>
                    </goals>
                </execution>
            </executions>
            <configuration>
                <toolchains>
                    <jdk>
                        <version>11</version>
                        <vendor>oracle</vendor>
                    </jdk>
                </toolchains>
            </configuration>
        </plugin>
```

>[!NOTE]
>Os `vendor` valores suportados são `oracle` e `sun` os `version` valores suportados são `1.8`, `1.11`e `11`.

## Variáveis de ambiente {#environment-variables}

### Variáveis de Ambiente padrão {#standard-environ-variables}

Em alguns casos, os clientes acham necessário variar o processo de criação com base nas informações sobre o programa ou pipeline.

Por exemplo, se a Minificação do JavaScript em tempo de criação estiver sendo feita, por meio de uma ferramenta como gulp, pode haver o desejo de usar um nível de Minificação diferente ao criar um ambiente dev em vez de construir para o estágio e a produção.

Para suportar isso, o Cloud Manager adiciona essas variáveis de ambiente padrão ao container build para cada execução.

| **Nome da variável** | **Definição** |
|---|---|
| CM_BUILD | Sempre definido como &quot;true&quot; |
| RAMIFICAÇÃO | A ramificação configurada para a execução |
| CM_PIPELINE_ID | O identificador de pipeline numérico |
| CM_PIPELINE_NAME | O nome do pipeline |
| CM_PROGRAMA_ID | O identificador de programa numérico |
| CM_PROGRAMA_NAME | O nome do programa |
| ARTIFTS_VERSION | Para um pipeline de estágio ou produção, a versão sintética gerada pelo Cloud Manager |

### Variáveis de pipeline {#pipeline-variables}

Em alguns casos, o processo de compilação de um cliente pode depender de variáveis de configuração específicas que não seriam adequadas para serem colocadas no repositório Git ou que precisariam variar entre execuções de pipeline usando a mesma ramificação.

O Cloud Manager permite que essas variáveis sejam configuradas por meio da API do Cloud Manager ou da CLI do Cloud Manager por pipeline. As variáveis podem ser armazenadas como texto sem formatação ou como criptografadas em repouso. Em ambos os casos, as variáveis são disponibilizadas dentro do ambiente build como uma variável de ambiente que pode ser referenciada dentro do `pom.xml` arquivo ou de outros scripts de compilação.

Para definir uma variável usando a CLI, execute um comando como:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

As variáveis atuais podem ser listadas:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Os nomes de variáveis podem conter somente caracteres alfanuméricos e sublinhado (_). Por convenção, os nomes devem ser todos maiúsculos. Há um limite de 200 variáveis por pipeline, cada nome deve ter menos de 100 caracteres e cada valor deve ter menos de 2048 caracteres.

Quando usado em um `Maven pom.xml` arquivo, é útil mapear essas variáveis para as propriedades do Maven usando uma sintaxe semelhante a esta:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Ativar Perfis Maven no Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Em alguns casos limitados, pode ser necessário variar um pouco o processo de compilação ao ser executado no Gerenciador de nuvem em vez de quando é executado em estações de trabalho de desenvolvedor. Nesses casos, os Perfis [](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) Maven podem ser usados para definir como a compilação deve ser diferente em ambientes diferentes, incluindo o Cloud Manager.

A ativação de um Perfil Maven dentro do ambiente de compilação do Cloud Manager deve ser feita procurando a variável de ambiente CM_BUILD descrita acima. Em contrapartida, um perfil destinado a ser usado somente fora do ambiente de criação do Cloud Manager deve ser feito procurando o absentido dessa variável.

Por exemplo, se você quiser enviar uma mensagem simples somente quando a compilação for executada dentro do Cloud Manager, você deve fazer o seguinte:

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
>Para testar esse perfil em uma estação de trabalho de desenvolvedor, você pode ativá-lo na linha de comando (com `-PcmBuild`) ou no Ambiente de desenvolvimento integrado (IDE).

E se você quiser enviar uma mensagem simples somente quando a criação for executada fora do Gerenciador de nuvem, você deve fazer o seguinte:

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

Para usar um repositório Maven protegido por senha do Gerenciador de nuvem, especifique a senha (e, opcionalmente, o nome de usuário) como uma Variável [secreta do](#pipeline-variables) Pipeline e faça referência a esse segredo em um arquivo chamado `.cloudmanager/maven/settings.xml` no repositório git. Esse arquivo segue o [schema de Arquivo](https://maven.apache.org/settings.html) de Configurações Maven. Quando os start de processo de criação do Gerenciador de nuvem, o `<servers>` elemento nesse arquivo será mesclado no arquivo padrão `settings.xml` fornecido pelo Gerenciador de nuvem. As IDs de servidor que começam com `adobe` e `cloud-manager` são consideradas reservadas e não devem ser usadas por servidores personalizados. Com esse arquivo no lugar, a ID do servidor seria referenciada de dentro de um `<repository>` e/ou `<pluginRepository>` elemento dentro do `pom.xml` arquivo. Geralmente, esses `<repository>` e/ou `<pluginRepository>` elementos estariam contidos em um perfil [específico do](/help/using/create-an-application-project.md#activating-maven-profiles-in-cloud-manager)Cloud Manager, embora isso não seja estritamente necessário.

Por exemplo, digamos que o repositório esteja em https://repository.myco.com/maven2, o usuário que o Gerenciador da Cloud deve usar é `cloudmanager` e a senha é `secretword`.

Primeiro, defina a senha como um segredo no pipeline:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

Em seguida, consulte-o no `.cloudmanager/maven/settings.xml` arquivo:

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

Por fim, consulte a ID do servidor dentro do `pom.xml` arquivo:

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

## Instalação de pacotes adicionais do sistema {#installing-additional-system-packages}

Algumas compilações exigem a instalação de pacotes adicionais do sistema para funcionar totalmente. Por exemplo, uma compilação pode chamar um script Python ou ruby e, como resultado, precisa ter um interpretador de idioma apropriado instalado. Isso pode ser feito chamando o plug-in [exec-maven](https://www.mojohaus.org/exec-maven-plugin/) para chamar a APT. Essa execução geralmente deve estar envolvida em um perfil Maven específico do Cloud Manager. Por exemplo, para instalar o python:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Essa mesma técnica pode ser usada para instalar pacotes específicos de idioma, ou seja, usar `gem` para RubyGems ou `pip` para pacotes Python.

>[!NOTE]
>
>Instalar um pacote do sistema desta maneira **não** o instala no ambiente de tempo de execução usado para executar o Adobe Experience Manager. Se precisar de um pacote de sistema instalado no ambiente AEM, entre em contato com o CSE (Customer Success Engineers).

## Ignorando pacotes de conteúdo {#skipping-content-packages}

No Cloud Manager, as compilações podem produzir qualquer número de pacotes de conteúdo.
Por vários motivos, pode ser desejável produzir um pacote de conteúdo, mas não implantá-lo. Isso pode ser útil, por exemplo, ao criar pacotes de conteúdo usados apenas para teste ou que serão reempacotados por outra etapa do processo de compilação, ou seja, como um subpacote de outro pacote.

Para acomodar esses cenários, o Cloud Manager procurará uma propriedade chamada ***cloudManagerTarget*** nas propriedades dos pacotes de conteúdo incorporados. Se essa propriedade estiver definida como Nenhum, o pacote será ignorado e não implantado. O mecanismo para definir essa propriedade depende da forma como a compilação está produzindo o pacote de conteúdo. Por exemplo, no plugin filevault-maven, você o configuraria da seguinte maneira:

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

Com o plug-in content-package-maven-é semelhante:

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

## Desenvolver seu código com base nas práticas recomendadas {#develop-your-code-based-on-best-practices}

As equipes de engenharia e consultoria de Adobe desenvolveram um conjunto [abrangente de práticas recomendadas para desenvolvedores](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html)de AEM.
