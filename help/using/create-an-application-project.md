---
title: Criar um projeto de aplicativo AEM
seo-title: Criar um projeto de aplicativo AEM
description: 'null'
seo-description: Siga esta página para saber mais sobre como configurar um projeto do AEM ao começar a usar o Cloud Manager.
uuid: 7 b 976 ebf -5358-49 d 8-a 58 d -0 bae 026303 fa
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 76 c 1 a 8 e 4-d 66 f -4 a 3 b -8 c 0 c-b 80 c 9 e 17700 e
translation-type: tm+mt
source-git-commit: b39fc865e3c34052fb94b223d9eebc0fce3495d2

---


# Create an AEM Application Project {#create-an-aem-application-project}

## Using Wizard to Create an AEM Application Project {#using-wizard-to-create-an-aem-application-project}

Quando os clientes estão integrados para o Cloud Manager, eles são fornecidos com um repositório de git vazio. Os clientes atuais do Adobe Managed Services (AMS) (ou clientes AEM locais que estão migrando para o AMS) geralmente já terão seu código de projeto no git (ou outro sistema de controle de versão) e importarão seu projeto para o repositório git do Experience Cloud Manager. No entanto, os novos clientes não têm projetos existentes.

Para ajudar novos clientes a iniciarem, o Cloud Manger agora pode criar um projeto mínimo do AEM como um ponto de partida. This process is based on the [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Siga as etapas abaixo para criar um projeto de aplicativo AEM no Experience Cloud Manager:

1. Once you log in to Cloud Manager and the basic program setup is complete, a special call to action card will be shown on the **Overview** screen, if the repository is empty.

   ![](assets/image2018-10-3_14-29-44.png)

1. Click **Create** to navigate to the **Pipeline Setup** screen.

   ![](assets/image2018-10-3_14-30-22.png)

1. Click **Create to** open a dialog box, which allows the user to provide the parameters required by the AEM Project Archetype. Em seu formulário padrão, a caixa de diálogo solicita dois valores:

   * **Título** - por padrão, é definido como Nome *do programa*

   * **Nome da nova ramificação** - por padrão, este é *mestre*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça na parte inferior da caixa de diálogo. Em seu formulário expandido, a caixa de diálogo mostra todos os parâmetros de configuração para o Archetype. Many of these parameters have default values which are generated based on the **Title**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >For example, if the **Title** is ***We.Finance***, the Base Maven Artifact Id parameter is generated as ***com.wefinance***. Esses valores podem ser alterados, se desejado.
   >
   >
   >For example, you can change from the generated ***value com.wefinance*** to ***net.wefinance***.

1. Click **Create** in the preceding step to create the starter project by using the archetype and commit to the named git branch. Depois que isso for feito, você poderá configurar o pipeline.

## Setting up your Project {#setting-up-your-project}

### Modifying Project Setup Details {#modifying-project-setup-details}

Para ser criada e implantada com sucesso com o Gerenciador da nuvem, os projetos existentes do AEM devem obedecer a algumas regras básicas:

* Os projetos devem ser construídos com o Apache Maven.
* There must be a *pom.xml* file in the root of the Git repository. This *pom.xml* file can refer to as many submodules (which in turn may have other submodules, etc.) conforme necessário.

* You can add references to additional Maven artifact repositories in your *pom.xml* files. No entanto, não há suporte para o acesso a repositórios protegidos por senha ou de rede protegidos por rede.
* Deployable content packages are discovered by scanning for content package *zip* files which are contained in a directory named *target*. Qualquer número de submódulos pode produzir pacotes de conteúdo.

* Deployable Dispatcher artifacts are discovered by scanning for *zip* files (again, contained in a directory named *target*) which have directories named *conf* and *conf.d*.

* Se houver mais de um pacote de conteúdo, a ordem das implantações do pacote não será garantida. Se uma ordem específica for necessária, as dependências do pacote de conteúdo poderão ser usadas para definir a ordem.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Build Environment Details {#build-environment-details}

Cloud Manager builds and tests your code using a specialized build runtime **Environment**. Este ambiente tem os seguintes atributos:

* O ambiente de criação é baseado em Linux.
* O Apache Maven 3.6.0 está instalado.
* A versão Java instalada é Oracle JDK 8 u 202.
* Há alguns pacotes de sistema adicionais instalados, necessários:

   * bzip2
   * descompactar
   * libpng
   * imagemagick
   * graphicsmagick
   * Se precisar de outros pacotes, será necessário solicitar aqueles por meio dos Engenheiros de sucesso do cliente (CSE).

* Cada criação é feita em um ambiente inválido; o contêiner de compilação não mantém nenhum estado entre as execuções.
* Maven is always run with the command: *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* Maven is configured at a system level with a settings.xml file which automatically includes the public Adobe **Artifact** repository. (Refer to [Adobe Public Maven Repository](https://repo.adobe.com/) for more details).

## Activating Maven Profiles in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Em alguns casos limitados, pode ser necessário variar um pouco o processo de compilação ao executar dentro do Gerenciador de nuvem em vez de ao executar em estações de trabalho do desenvolvedor. For these cases, [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) can be used to define how the build should be different in different environments, including Cloud Manager.

Activation of a Maven Profile inside the Cloud Manager build environment should be done by looking for the presence of an environment variable named `CM_BUILD`. Essa variável sempre será definida no ambiente de compilação do Experience Cloud Manager. Por exemplo, um perfil destinado a ser usado apenas fora do ambiente de compilação do Experience Cloud Manager deve ser feito procurando pelo sentimento dessa variável.

Por exemplo, se você deseja gerar uma mensagem simples somente quando a criação é executada dentro do Gerenciador de nuvem, você faria isso:

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
>To test this profile on a developer workstation, you can either enable it on the command line (with `-PcmBuild`) or in your Integrated Development Environment (IDE).

E se você quiser gerar uma mensagem simples somente quando a criação for executada fora do Gerenciador de nuvem, você faria isso:

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

## Variáveis de ambiente personalizadas

Em alguns casos, o processo de criação de um cliente pode depender de variáveis de configuração específicas que seriam inadequadas para colocar no repositório do git. O Gerenciador de nuvem permite que essas variáveis sejam configuradas por um Engenheiro de sucesso do cliente (CSE) por cliente. Essas variáveis são armazenadas em um local de armazenamento seguro e são visíveis apenas no contêiner de compilação para o cliente específico. Os clientes que desejam usar esse recurso precisam entrar em contato com o CSE para configurar suas variáveis.

Uma vez configuradas, essas variáveis estarão disponíveis como variáveis de ambiente. Para usá-los como propriedades do Maven, você pode fazer referência a elas em seu arquivo pom.xml, potencialmente em um perfil, conforme descrito acima:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>Os nomes de variáveis de ambiente podem conter apenas caracteres alfanuméricos e sublinhados (_). Por convenção, os nomes devem ser todos os casos.

## Develop your Code Based on Best Practices {#develop-your-code-based-on-best-practices}

Adobe Engineering and Consulting teams have developed a [comprehensive set of best practices for AEM developers](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
