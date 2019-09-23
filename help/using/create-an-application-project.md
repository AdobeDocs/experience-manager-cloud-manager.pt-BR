---
title: Criar um projeto de aplicativo AEM
seo-title: Criar um projeto de aplicativo AEM
description: 'null'
seo-description: Siga esta página para saber mais sobre como configurar um projeto do AEM na introdução ao Cloud Manager.
uuid: 7b976ebf-5358-49d8-a58d-0bae026303fa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introdução
discoiquuid: 76c1a8e4-d66f-4a3b-8c0c-b80c9e17700e
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---


# Criar um projeto de aplicativo AEM {#create-an-aem-application-project}

## Usar o Assistente para criar um projeto de aplicativo AEM {#using-wizard-to-create-an-aem-application-project}

Quando os clientes são embarcados no Cloud Manager, eles recebem um repositório git vazio. Os clientes atuais do Adobe Managed Services (AMS) (ou clientes locais do AEM que estão migrando para o AMS) geralmente já têm o código do projeto em git (ou outro sistema de controle de versão) e importarão seu projeto para o repositório de git do Cloud Manager. Novos clientes, no entanto, não têm projetos existentes.

Para ajudar a iniciar novos clientes, o Cloud Manager agora pode criar um projeto AEM mínimo como ponto de partida. Esse processo se baseia no [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Siga as etapas abaixo para criar um projeto de aplicativo AEM no Cloud Manager:

1. Quando você fizer logon no Cloud Manager e a configuração básica do programa for concluída, uma chamada especial para o cartão de ação será exibida na tela **Visão geral** , se o repositório estiver vazio.

   ![](assets/image2018-10-3_14-29-44.png)

1. Clique em **Criar** para navegar até a tela Configuração **do** pipeline.

   ![](assets/image2018-10-3_14-30-22.png)

1. Clique em **Criar para** abrir uma caixa de diálogo, que permite ao usuário fornecer os parâmetros exigidos pelo AEM Project Archetype. Em seu formulário padrão, a caixa de diálogo solicita dois valores:

   * **Título** - por padrão, isso é definido como Nome *do programa*

   * **Novo nome** da ramificação - por padrão, é *mestre*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça em direção à parte inferior da caixa de diálogo. Em seu formulário expandido, a caixa de diálogo mostra todos os parâmetros de configuração do Archetype. Muitos desses parâmetros têm valores padrão que são gerados com base no **Título**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Por exemplo, se o **Título** for ***We.Finance***, o parâmetro de Id de artefato de base de máscara será gerado como ***com.wefinance***. Esses valores podem ser alterados, se desejado.
   >
   >
   >Por exemplo, você pode alterar do ***valor gerado com.wefinance*** para ***net.wefinance***.

1. Clique em **Criar** na etapa anterior para criar o projeto inicial usando o arquétipo e confirmando o ramo git nomeado. Quando isso estiver feito, você poderá configurar o pipeline.

## Configuração do projeto {#setting-up-your-project}

### Modificando Detalhes de Configuração do Projeto {#modifying-project-setup-details}

Para ser criado e implantado com êxito com o Cloud Manager, os projetos AEM existentes precisam seguir algumas regras básicas:

* Os projetos devem ser construídos com o Apache Maven.
* Deve haver um arquivo *pom.xml* na raiz do repositório Git. Esse arquivo *pom.xml* pode fazer referência a quantos submódulos (que por sua vez podem ter outros submódulos etc.) conforme necessário.

* Você pode adicionar referências a repositórios de artefatos Maven adicionais em seus arquivos *pom.xml* . No entanto, o acesso a repositórios de artefatos protegidos por senha ou pela rede não é suportado.
* Os pacotes de conteúdo implantáveis são detectados ao verificar se há arquivos *zip* do pacote de conteúdo contidos em um diretório chamado *target*. Qualquer número de submódulos pode produzir pacotes de conteúdo.

* Os artefatos do Dispatcher que podem ser implantados são descobertos pela varredura de arquivos *zip* (novamente, contidos em um diretório chamado *target*) que têm diretórios chamados *conf* e *conf.d*.

* Se houver mais de um pacote de conteúdo, a ordem de implantações de pacote não é garantida. Se uma ordem específica for necessária, as dependências do pacote de conteúdo poderão ser usadas para definir a ordem.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Criar detalhes do ambiente {#build-environment-details}

O Cloud Manager cria e testa seu código usando um ambiente de compilação especializado. Esse ambiente tem os seguintes atributos:

* O ambiente de compilação é baseado no Linux, derivado do Ubuntu 18.04.
* O Apache Maven 3.6.0 está instalado.
* A versão do Java instalada é o Oracle JDK 8u202.
* Existem outros pacotes de sistema instalados que são necessários:

   * bzip2
   * descompactar
   * libpng
   * imagemagick
   * gráfico

* Outros pacotes podem ser instalados no momento da criação, conforme descrito [abaixo](#installing-additional-system-packages).
* Cada construção é feita num ambiente intocado; o contêiner de compilação não mantém nenhum estado entre as execuções.
* Maven é sempre executado com o comando: *mvn —batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* O Maven é configurado no nível do sistema com um arquivo settings.xml que inclui automaticamente o repositório público do Adobe **Artifato** . (Consulte o Repositório [do](https://repo.adobe.com/) Adobe Public Maven para obter mais detalhes).

## Ativar perfis Maven no Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Em alguns casos limitados, pode ser necessário variar um pouco o processo de compilação ao ser executado no Gerenciador de nuvem em vez de quando é executado em estações de trabalho de desenvolvedor. Nesses casos, os Perfis [](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) Maven podem ser usados para definir como a compilação deve ser diferente em ambientes diferentes, incluindo o Cloud Manager.

A ativação de um Perfil Maven dentro do ambiente de criação do Cloud Manager deve ser feita procurando a presença de uma variável de ambiente chamada `CM_BUILD`. Essa variável sempre será definida dentro do ambiente de criação do Cloud Manager. Em contrapartida, um perfil destinado a ser usado somente fora do ambiente de criação do Cloud Manager deve ser feito procurando o absentido dessa variável.

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

E se você quiser enviar uma mensagem simples somente quando a criação for executada fora do Gerenciador de nuvem, você faria isso:

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

Em alguns casos, o processo de compilação de um cliente pode depender de variáveis de configuração específicas que não seriam adequadas para serem inseridas no repositório git. O Cloud Manager permite que essas variáveis sejam configuradas por um CSE (Customer Success Engineer, engenheiro de sucesso do cliente) com base no cliente. Essas variáveis são armazenadas em um local de armazenamento seguro e são visíveis apenas no contêiner de compilação do cliente específico. Os clientes que desejarem usar esse recurso precisam entrar em contato com o CSE para configurar suas variáveis.

Depois de configuradas, essas variáveis estarão disponíveis como variáveis de ambiente. Para usá-las como propriedades Maven, é possível referenciá-las no arquivo pom.xml, possivelmente em um perfil como descrito acima:

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
>Os nomes das variáveis de ambiente podem conter apenas caracteres alfanuméricos e sublinhado (_). Por convenção, os nomes devem ser todos maiúsculos.

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
>Instalar um pacote do sistema dessa maneira **não** o instala no ambiente de tempo de execução usado para executar o Adobe Experience Manager. Se precisar de um pacote de sistema instalado no ambiente AEM, entre em contato com o CSE (Customer Success Engineers).

## Ignorando pacotes de conteúdo {#skipping-content-packages}

No Cloud Manager, as compilações podem produzir qualquer número de pacotes de conteúdo.
Por vários motivos, pode ser desejável produzir um pacote de conteúdo, mas não implantá-lo. Isso pode ser útil, por exemplo, ao criar pacotes de conteúdo usados apenas para teste ou que serão reempacotados por outra etapa do processo de compilação, ou seja, como um subpacote de outro pacote.

Para acomodar esses cenários, o Cloud Manager procurará uma propriedade chamada ***cloudManagerTarget*** nas propriedades dos pacotes de conteúdo criados. Se essa propriedade estiver definida como nenhum, o pacote será ignorado e não implantado. O mecanismo para definir essa propriedade depende da forma como a compilação está produzindo o pacote de conteúdo. Por exemplo, com o plugin filevault-maven, você configuraria o plug-in da seguinte maneira:

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

As equipes de engenharia e consultoria da Adobe desenvolveram um conjunto [abrangente de práticas recomendadas para desenvolvedores](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html)do AEM.
