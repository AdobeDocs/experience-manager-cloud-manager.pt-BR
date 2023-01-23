---
title: O ambiente de criação
description: Saiba mais sobre o ambiente de criação especializado no qual os usuários do Cloud Manager criam e testam seus códigos.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 42cafc03a607ace183d58adbe1c397c1a6c5c22f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# O ambiente de criação {#build-environment}

Saiba mais sobre o ambiente de criação especializado no qual os usuários do Cloud Manager criam e testam seus códigos.

## Detalhes do ambiente {#details}

Os ambientes de criação do Cloud Manager têm os seguintes atributos.

* O ambiente de criação é baseado em Linux, com a tecnologia do Ubuntu 18.04.
* O Apache Maven 3.6.0 está instalado.
* As versões do Java instaladas são: Oracle JDK 8u202 e Oracle JDK 11.0.2.
* Por padrão, a variável de ambiente `JAVA_HOME` está definida como `/usr/lib/jvm/jdk1.8.0_202`, que contém o Oracle JDK 8u202. Consulte a seção [Versão alternativa do JDK de execução do Maven](#alternate-maven) para obter mais detalhes.
* Há alguns pacotes de sistema adicionais instalados que são necessários.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Outros pacotes podem ser instalados no momento da criação, conforme descrito na seção [Instalação de pacotes de sistema adicionais.](#installing-additional-system-packages)
* Cada build é criada em um ambiente original. O container da build não mantém nenhum estado entre as execuções.
* O Maven é sempre executado com estes três comandos:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* O Maven é configurado em um nível de sistema com um arquivo `settings.xml` que inclui automaticamente o repositório público de artefatos da Adobe usando um perfil chamado `adobe-public`.
   * Consulte o [Repositório Maven público da Adobe](https://repo1.maven.org/) para obter mais detalhes.

>[!NOTE]
>
>Embora o Cloud Manager não defina uma versão específica do `jacoco-maven-plugin`, a versão usada deve ser pelo menos a `0.7.5.201505241946`.

>[!TIP]
>
>Consulte os seguintes recursos adicionais para saber como usar as APIs do Cloud Manager:
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Criar uma integração de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [Permissões de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)


## Uso de uma versão específica do Java {#using-java-version}

Por padrão, os projetos são criados pelo processo de compilação do Cloud Manager usando o Oracle 8 JDK. Os clientes que desejam usar um JDK alternativo têm duas opções.

* [Maven Toolchains](#maven-toolchains)
* [Selecionar uma versão alternativa do JDK para todo o processo de execução do Maven](#alternate-maven)

### Maven Toolchains {#maven-toolchains}

O [plug-in Maven Toolchains](https://maven.apache.org/plugins/maven-toolchains-plugin/) permite que os projetos selecionem um JDK específico (ou conjunto de ferramentas) a ser usado no contexto de plug-ins do Maven com reconhecimento de conjuntos de ferramentas. Isso é feito no arquivo `pom.xml` do projeto especificando um fornecedor e o número da versão. Um exemplo de seção do arquivo `pom.xml` é:

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

Isso fará com que todos os plug-ins do Maven com reconhecimento de conjuntos de ferramentas usem o JDK do Oracle 11.

Ao usar esse método, o próprio Maven ainda é executado usando o JDK padrão (Oracle 8) e a variável de ambiente `JAVA_HOME` não é alterada. Portanto, verificar ou impor a versão do Java por meio de plug-ins como o [Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) não terá resultado, e esses plug-ins não devem ser usados.

As combinações de fornecedor/versão disponíveis no momento são:

| Fornecedor | Versão |
|---|---|
| Oracle | 1.8 |
| Oracle | 1.11 |
| Oracle | 11 |
| sun | 1.8 |
| sun | 1.11 |
| sun | 11 |

>[!NOTE]
>
>A partir de abril de 2022, o JDK do Oracle será o JDK padrão para o desenvolvimento e a operação de aplicativos do AEM. O processo de criação do Cloud Manager mudará automaticamente para o uso do JDK do Oracle, mesmo se uma opção alternativa for explicitamente selecionada no conjunto de ferramentas do Maven. Consulte [as notas de versão de abril](/help/release-notes/2022/2022-4-0.md) para obter mais detalhes.

### Versão alternativa do JDK de execução do Maven {#alternate-maven}

Também é possível selecionar o Oracle 8 ou Oracle 11 como o JDK para toda a execução do Maven. Diferentemente das opções de conjuntos de ferramentas, isso altera o JDK usado para todos os plug-ins, a menos que a configuração de conjuntos de ferramentas também esteja definida. Nesse caso, a configuração de conjuntos de ferramentas ainda será aplicada para plug-ins do Maven com reconhecimento de conjuntos de ferramentas. Como resultado, a verificação e a implementação da versão do Java usando o [Plug-in executor Apache Maven](https://maven.apache.org/enforcer/maven-enforcer-plugin/) funcionarão.

Para fazer isso, crie um arquivo chamado `.cloudmanager/java-version` na ramificação do repositório Git usada pelo pipeline. Esse arquivo pode ter o conteúdo `11` ou `8`. Qualquer outro valor é ignorado. Se `11` for especificado, o Oracle 11 será usado e a variável de ambiente `JAVA_HOME` será definida como `/usr/lib/jvm/jdk-11.0.2`. Se `8` for especificado, o Oracle 8 será usado e a variável de ambiente `JAVA_HOME` será definida como `/usr/lib/jvm/jdk1.8.0_202`.

## Variáveis de ambiente {#environment-variables}

### Variáveis de ambiente padrão {#standard-environ-variables}

Em alguns casos, pode ser necessário variar o processo de criação com base nas informações sobre o programa ou pipeline.

Por exemplo, se a minificação do JavaScript em tempo de criação for feita por meio de uma ferramenta como o gulp, talvez seja desejável usar um nível de minificação diferente ao criar para um ambiente de desenvolvimento, em vez de criar para preparo e produção.

Para ser compatível com isso, o Cloud Manager adiciona variáveis de ambiente padrão ao contêiner de criação para cada execução.

| Nome da variável | Descrição |
|---|---|
| `CM_BUILD` | Sempre definida como `true` |
| `BRANCH` | A ramificação configurada para a execução |
| `CM_PIPELINE_ID` | O identificador numérico do pipeline |
| `CM_PIPELINE_NAME` | O nome do pipeline |
| `CM_PROGRAM_ID` | O identificador numérico do programa |
| `CM_PROGRAM_NAME` | O nome do programa |
| `ARTIFACTS_VERSION` | Para um pipeline de preparo ou produção, a versão sintética gerada pelo Cloud Manager |

### Disponibilidade da variável de ambiente padrão {#availability}

As variáveis de ambiente padrão podem ser usadas em vários lugares.

#### Autor, visualização e publicação {#author-preview-publish}

As variáveis e os segredos comuns do ambiente podem ser usados nos ambientes de criação, visualização e publicação.

#### Dispatcher {#dispatcher}

Somente variáveis de ambiente normais podem ser usadas com [o dispatcher.](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=pt-BR) Segredos não podem ser usados.

No entanto, as variáveis de ambiente não podem ser usadas em diretivas `IfDefine`.

>[!TIP]
>
>Você deve validar o uso das variáveis de ambiente com o [dispatcher localmente](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=pt-BR) antes da implantação.

#### Configurações do OSGi {#osgi}

Tanto as variáveis de ambiente comuns quanto os segredos podem ser usados em [Configurações OSGi.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html?lang=pt_BR)

### Variáveis de pipeline {#pipeline-variables}

Em alguns casos, o processo de criação pode depender de variáveis de configuração específicas que seriam inadequadas para colocar no repositório Git ou precisariam variar entre execuções de pipeline usando a mesma ramificação.

O Cloud Manager permite que essas variáveis sejam configuradas por meio da API do Cloud Manager ou da CLI do Cloud Manager por pipeline. As variáveis podem ser armazenadas como texto simples ou criptografadas em repouso. Em ambos os casos, as variáveis são disponibilizadas no ambiente de criação como uma variável de ambiente que pode ser referenciada de dentro do arquivo `pom.xml` ou de outros scripts de criação.

Para definir uma variável usando a CLI, execute um comando semelhante ao seguinte.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

As variáveis atuais podem ser listadas usando um comando semelhante ao seguinte.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

As variáveis devem atender a determinadas limitações.

* Os nomes de variáveis só podem conter caracteres alfanuméricos e sublinhado (`_`).
   * Por convenção, os nomes devem estar todos em maiúsculas.
* Há um limite de 200 variáveis por pipeline.
* Cada nome deve ter menos de 100 caracteres.
* Cada valor da string deve ter menos de 2.048 caracteres.
* Cada valor de secretString deve ter menos de 500 caracteres.

Quando usado dentro de um arquivo `pom.xml` do Maven, geralmente é útil mapear essas variáveis para propriedades do Maven usando uma sintaxe semelhante à seguinte.

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

## Instalação de pacotes de sistema adicionais {#installing-additional-system-packages}

Para funcionar plenamente, algumas builds exigem a instalação de pacotes de sistema adicionais. Por exemplo, uma build pode invocar um script do Python ou Ruby e, como resultado, precisa ter um interpretador de linguagem adequado instalado. Isso pode ser feito chamando o [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) para invocar o APT. Essa execução geralmente deve ser encapsulada em um perfil do Maven específico do Cloud Manager. Por exemplo, para instalar o Python:

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

Essa mesma técnica pode ser usada para instalar pacotes específicos de linguagem, ou seja, usando `gem` para RubyGems ou `pip` pacotes do Python.

>[!NOTE]
>
>Instalar um pacote de sistema dessa maneira não o instala no ambiente de tempo de execução usado para executar o Adobe Experience Manager. Se a instalação de um pacote de sistema no ambiente AEM for necessária, entre em contato com o representante da Adobe.
