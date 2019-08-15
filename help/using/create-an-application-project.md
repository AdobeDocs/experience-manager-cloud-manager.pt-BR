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
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---


# Criar um projeto de aplicativo AEM {#create-an-aem-application-project}

## Uso do assistente para criar um projeto de aplicativo AEM {#using-wizard-to-create-an-aem-application-project}

Quando os clientes estão integrados para o Cloud Manager, eles são fornecidos com um repositório de git vazio. Os clientes atuais do Adobe Managed Services (AMS) (ou clientes AEM locais que estão migrando para o AMS) geralmente já terão seu código de projeto no git (ou outro sistema de controle de versão) e importarão seu projeto para o repositório git do Experience Cloud Manager. No entanto, os novos clientes não têm projetos existentes.

Para ajudar novos clientes a iniciarem, o Cloud Manger agora pode criar um projeto mínimo do AEM como um ponto de partida. Esse processo se baseia no [**arquivo de projeto do AEM**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Siga as etapas abaixo para criar um projeto de aplicativo AEM no Experience Cloud Manager:

1. Após efetuar logon no Experience Manager Manager e a configuração básica do programa for concluída, uma chamada especial para o cartão de ação será mostrada na tela **Visão geral** , se o repositório estiver vazio.

   ![](assets/image2018-10-3_14-29-44.png)

1. Clique **em Criar** para navegar até a tela **de Configuração** do pipeline.

   ![](assets/image2018-10-3_14-30-22.png)

1. Clique **em Criar para** abrir uma caixa de diálogo, que permite ao usuário fornecer os parâmetros exigidos pelo Arquetype do projeto do AEM. Em seu formulário padrão, a caixa de diálogo solicita dois valores:

   * **Título** - por padrão, é definido como Nome *do programa*

   * **Nome da nova ramificação** - por padrão, este é *mestre*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça na parte inferior da caixa de diálogo. Em seu formulário expandido, a caixa de diálogo mostra todos os parâmetros de configuração para o Archetype. Muitos desses parâmetros têm valores padrão gerados com base no **Título**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Por exemplo, se **o Título** for ***We. Finance***, o parâmetro de ID de artefato Maven base será gerado como ***com. wefinance***. Esses valores podem ser alterados, se desejado.
   >
   >
   >Por exemplo, você pode alterar do valor gerado ***com. wefinance*** para ***net. wefinance***.

1. Clique **em Criar** na etapa anterior para criar o projeto inicial usando o archetype e confirmar o ramo de git nomeado. Depois que isso for feito, você poderá configurar o pipeline.

## Configuração do projeto {#setting-up-your-project}

### Modificar detalhes da configuração do projeto {#modifying-project-setup-details}

Para ser criada e implantada com sucesso com o Gerenciador da nuvem, os projetos existentes do AEM devem obedecer a algumas regras básicas:

* Os projetos devem ser construídos com o Apache Maven.
* Deve haver um arquivo *pom.xml* na raiz do repositório Git. Esse *arquivo pom.xml* pode se referir a submódulos (que, por sua vez, podem ter outros submódulos etc.) conforme necessário.

* Você pode adicionar referências a repositórios de artefato Maven adicionais em seus *pom.xml* arquivos. No entanto, não há suporte para o acesso a repositórios protegidos por senha ou de rede protegidos por rede.
* Os pacotes de conteúdo implantáveis são descobertos por meio da leitura ótica dos arquivos *compactados* do pacote de conteúdo contidos em um diretório chamado *target*. Qualquer número de submódulos pode produzir pacotes de conteúdo.

* Os artefatos implantadores implantáveis são descobertos pela leitura de arquivos *zip* (novamente, contidos em um diretório chamado *target*) com diretórios chamados *conf* e *conf. d*.

* Se houver mais de um pacote de conteúdo, a ordem das implantações do pacote não será garantida. Se uma ordem específica for necessária, as dependências do pacote de conteúdo poderão ser usadas para definir a ordem.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Criar detalhes do ambiente {#build-environment-details}

O Cloud Manager constrói e testa seu código usando um ambiente de build especializado. Este ambiente tem os seguintes atributos:

* O ambiente de criação é baseado em Linux, derivado do Ubuntu 18.04.
* O Apache Maven 3.6.0 está instalado.
* A versão Java instalada é Oracle JDK 8 u 202.
* Há alguns pacotes de sistema adicionais instalados, necessários:

   * bzip2
   * descompactar
   * libpng
   * imagemagick
   * graphicsmagick

* Outros pacotes podem ser instalados no momento da criação, conforme descrito [abaixo](#installing-additional-system-packages).
* Cada criação é feita em um ambiente inválido; o contêiner de compilação não mantém nenhum estado entre as execuções.
* O Maven sempre é executado com o comando: *mvn —modo em lote limpo org. jacoco: jacoco-maven-plugin: pacote de preparar agente*
* O Maven é configurado em nível de sistema com um arquivo settings.xml que inclui automaticamente o repositório público Adobe **Artifact** . (Consulte Repositório Maven público [da Adobe](https://repo.adobe.com/) para obter mais detalhes).

## Ativação de perfis de maven no Gerenciador de nuvem {#activating-maven-profiles-in-cloud-manager}

Em alguns casos limitados, pode ser necessário variar um pouco o processo de compilação ao executar dentro do Gerenciador de nuvem em vez de ao executar em estações de trabalho do desenvolvedor. Nesses casos, os Perfis [de Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) podem ser usados para definir como a criação deve ser diferente em diferentes ambientes, incluindo o Experience Cloud Manager.

A ativação de um perfil Maven no ambiente de criação do Experience Cloud Manager deve ser feita procurando pela presença de uma variável de ambiente chamada `CM_BUILD`. Essa variável sempre será definida no ambiente de compilação do Experience Cloud Manager. Por exemplo, um perfil destinado a ser usado apenas fora do ambiente de compilação do Experience Cloud Manager deve ser feito procurando pelo sentimento dessa variável.

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
>Para testar esse perfil em uma estação de trabalho do desenvolvedor, você pode ativá-lo na linha de comando (com `-PcmBuild`) ou em seu Ambiente de desenvolvimento integrado (IDE).

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

## Instalação de pacotes de sistema adicionais {#installing-additional-system-packages}

Alguns builds exigem que pacotes de sistema adicionais sejam instalados para funcionar totalmente. Por exemplo, uma criação pode invocar um script de Python ou ruby e, como resultado, precisar ter um intérprete de idioma apropriado instalado. Isso pode ser feito chamando o [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) para invocar o APT. Geralmente, essa execução deve estar encapsulada em um perfil Maven específico do Experience Cloud. Por exemplo, para instalar o python:

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

Essa mesma técnica pode ser usada para instalar pacotes específicos de idioma, isto é, uso `gem` para rubygems ou `pip` para pacotes de Python.

>[!NOTE]
>
>Instalar um pacote do sistema dessa maneira **não a** instala no ambiente de tempo de execução usado para executar o Adobe Experience Manager. Se precisar de um pacote de sistema instalado no ambiente AEM, entre em contato com os Engenheiros de sucesso do cliente (CSE).

## Ignorar pacotes de conteúdo {#skipping-content-packages}

No Cloud Manager, é possível criar qualquer número de pacotes de conteúdo.
Por diversos motivos, pode ser desejável disponibilizar um pacote de conteúdo, mas não implantá-lo. Isso pode ser útil, por exemplo, ao criar pacotes de conteúdo usados apenas para teste ou que serão reorganizados por outra etapa no processo de compilação, isto é, como um subpacote de outro pacote.

Para acomodar esses cenários, o Cloud Manager procurará uma propriedade denominada ***cloudmanagertarget*** nas propriedades dos pacotes de conteúdo construídos. Se essa propriedade estiver definida como nenhum, o pacote será ignorado e não implantado. O mecanismo para definir essa propriedade depende da forma como a criação está produzindo o pacote de conteúdo. Por exemplo, com o filevault-plugin-plugin configuraria o plug-in como este:

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

Com o content-package-maven-plugin, é semelhante:

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

As equipes de engenharia e consultoria da Adobe desenvolveram um conjunto [abrangente de práticas recomendadas para desenvolvedores do AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
