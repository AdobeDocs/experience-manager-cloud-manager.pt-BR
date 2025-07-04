---
title: O ambiente de criação
description: Saiba mais sobre o ambiente de criação especializado no qual os usuários do Cloud Manager criam e testam seus códigos.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 97%

---


# O ambiente de criação {#build-environment}

Saiba mais sobre o ambiente de criação especializado no qual os usuários do Cloud Manager criam e testam seus códigos.

## Detalhes do ambiente {#details}

Os ambientes de criação do Cloud Manager têm os atributos a seguir.

* O ambiente de compilação se baseia em Linux e é derivado do Ubuntu 22.04.
* O Apache Maven 3.9.4 está instalado.
   * A Adobe recomenda [atualizar os repositórios Maven para usar HTTPS em vez de HTTP](#https-maven).
* As versões do Java instaladas são: Oracle JDK 8u401 e Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* Por padrão, a variável de ambiente `JAVA_HOME` é definida como `/usr/lib/jvm/jdk1.8.0_401`, o que contém o Oracle JDK 8u401. Consulte a seção [Versão alternativa do JDK de execução do Maven](#alternate-maven) para obter mais detalhes.
* Há alguns pacotes de sistema adicionais instalados que são necessários.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* É possível instalar outros pacotes no momento da criação, conforme descrito na seção [Instalação de pacotes de sistema adicionais](#installing-additional-system-packages).
* Cada compilação é criada em um ambiente limpo. O container da build não mantém nenhum estado entre as execuções.
* O Maven é executado com estes três comandos:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* O Maven é configurado em nível de sistema com um arquivo `settings.xml`, que inclui automaticamente o repositório público de artefatos da Adobe usando um perfil chamado `adobe-public`. Consulte [Repositório Maven público da Adobe](https://repo1.maven.org/) para mais detalhes.
* O Node.js 18 está disponível para [pipelines de front-end](/help/overview/ci-cd-pipelines.md).

>[!NOTE]
>
>Embora o Cloud Manager não defina uma versão específica do `jacoco-maven-plugin`, a versão usada não deve ser inferior à `0.7.5.201505241946`.

>[!TIP]
>
>Consulte os seguintes recursos adicionais para saber como usar as APIs do Cloud Manager:
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Criar uma integração de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [Permissões de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## Repositórios Maven HTTPS {#https-maven}

O Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) iniciou uma atualização contínua do ambiente de compilação (que terminou com a versão 2023.12.0), a qual incluiu a atualização para o Maven 3.8.8. Uma mudança significativa introduzida no Maven 3.8.1 foi um aprimoramento de segurança destinado a reduzir possíveis vulnerabilidades. Mais especificamente, o Maven agora desabilita por padrão todos os espelhos inseguros de `http://*`, conforme descrito nas [notas de versão do Maven](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

Como resultado desse aprimoramento de segurança, algumas pessoas podem enfrentar problemas durante a etapa de compilação, especialmente ao baixar artefatos de repositórios Maven que usam conexões HTTP inseguras.

Para garantir uma experiência perfeita com a versão atualizada, a Adobe recomenda atualizar os repositórios Maven para usar HTTPS em vez de HTTP. Esse ajuste se alinha à evolução contínua do setor em direção a protocolos de comunicação seguros e ajuda a manter um processo de compilação seguro e confiável.

## Uso de uma versão específica do Java {#using-java-version}

Por padrão, os projetos são criados pelo processo de compilação do Cloud Manager usando o Oracle 8 JDK. Os clientes que desejam usar um JDK alternativo têm duas opções.

* [Maven Toolchains](#maven-toolchains)
* [Selecionar uma versão alternativa do JDK para todo o processo de execução do Maven](#alternate-maven)

### Maven Toolchains {#maven-toolchains}

O [plug-in Maven Toolchains](https://maven.apache.org/plugins/maven-toolchains-plugin/) permite que os projetos selecionem um JDK específico (ou conjunto de ferramentas) a ser usado no contexto de plug-ins do Maven com reconhecimento de conjuntos de ferramentas. Isso é feito por especificar um fornecedor e o número da versão no arquivo `pom.xml` do projeto. Veja um exemplo de seção do arquivo `pom.xml`:

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

Isso fará com que todos os plug-ins do Maven com reconhecimento de conjuntos de ferramentas usem o Oracle JDK, versão 11.

Ao usar esse método, o próprio Maven ainda é executado usando o JDK padrão (Oracle 8) e a variável de ambiente `JAVA_HOME` não é alterada. Portanto, verificar ou impor a versão do Java por meio de plug-ins como o [Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) não terá resultado, e, portanto, estes não devem ser usados.

As combinações de fornecedor/versão disponíveis no momento são:

| Fornecedor | Versão |
|---|---|
| Oracle | 1.8 |
| Oracle | 1.11 |
| Oracle | 11 |
| Dom | 1.8 |
| Dom | 1.11 |
| Dom | 11 |

>[!NOTE]
>
>A partir de abril de 2022, o Oracle JDK será o JDK padrão para o desenvolvimento e a operação de aplicativos do AEM. O processo de criação do Cloud Manager passa automaticamente a usar o JDK do Oracle, mesmo que uma opção alternativa esteja explicitamente selecionada no conjunto de ferramentas do Maven. Consulte as [notas de versão de abril](/help/release-notes/2022/2022-4-0.md) para mais detalhes.

### Versão alternativa do JDK de execução do Maven {#alternate-maven}

Também é possível selecionar o Oracle 8 ou Oracle 11 como o JDK para toda a execução do Maven. Diferentemente das opções de conjuntos de ferramentas, essa definição altera o JDK usado em todos os plug-ins, a menos que a configuração de conjuntos de ferramentas também esteja definida; neste caso, essa configuração ainda será aplicada aos plug-ins Maven com reconhecimento de conjuntos de ferramentas. Como resultado, a verificação e a implementação da versão do Java usando o [plug-in Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) será bem-sucedida.

Para isso, crie um arquivo chamado `.cloudmanager/java-version` na ramificação do repositório Git usada pelo pipeline. Esse arquivo pode ter o conteúdo `11` ou `8`. Qualquer outro valor é ignorado. Se `11` for especificado, o sistema usará o Oracle 11 e definirá a variável de ambiente `JAVA_HOME` como `/usr/lib/jvm/jdk-11.0.22`. Se `8` for especificado, o sistema usará o Oracle 8 e definirá a variável de ambiente `JAVA_HOME` como `/usr/lib/jvm/jdk1.8.0_401`.

## Variáveis de ambiente {#environment-variables}

### Variáveis de ambiente padrão {#standard-environ-variables}

Em alguns casos, pode ser necessário variar o processo de criação com base nas informações sobre o programa ou pipeline.

Por exemplo, ao usar uma ferramenta como o gulp para minimização do JavaScript, você pode preferir níveis de minimização diferentes para ambientes de desenvolvimento em comparação a ambientes de preparo e produção.

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

#### Ambientes de criação, visualização e publicação {#author-preview-publish}

As variáveis e os segredos comuns do ambiente podem ser usados nos ambientes de criação, visualização e publicação.

#### Dispatcher {#dispatcher}

Somente variáveis de ambiente normais podem ser usadas com o [Dispatcher](https://experienceleague.adobe.com/pt-br/docs/experience-manager-dispatcher/using/dispatcher). Não é possível usar segredos.

No entanto, as variáveis de ambiente não podem ser usadas em diretivas `IfDefine`.

>[!TIP]
>
>Valide o uso das variáveis de ambiente com o [Dispatcher localmente](https://experienceleague.adobe.com/pt-br/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) antes da implantação.

#### Configurações do OSGi {#osgi}

As variáveis e os segredos comuns do ambiente podem ser usados nas [configurações do OSGi](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi).

### Variáveis de pipeline {#pipeline-variables}

Em alguns casos, o processo de criação pode depender de variáveis de configuração específicas que seriam inadequadas para colocar no repositório Git ou precisariam variar entre execuções de pipeline usando a mesma ramificação.

O Cloud Manager permite que essas variáveis sejam configuradas por meio da API ou da CLI do Cloud Manager com base no pipeline. As variáveis podem ser armazenadas como texto simples ou criptografadas em repouso. Em ambos os casos, as variáveis são disponibilizadas no ambiente de compilação como variáveis de ambiente que podem ser referenciadas no arquivo `pom.xml` ou em outros scripts de criação.

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
* Cada nome deve conter menos de 100 caracteres.
* Cada valor de string deve conter menos de 2.048 caracteres.
* Cada valor de `secretString` deve conter menos de 500 caracteres.

Quando usadas dentro de um arquivo `pom.xml` do Maven, geralmente é útil mapear essas variáveis para propriedades do Maven usando uma sintaxe semelhante à seguinte.

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

Para funcionar plenamente, algumas builds exigem a instalação de pacotes de sistema adicionais. Por exemplo, uma build pode invocar um script do Python ou Ruby e, como resultado, precisar de um interpretador de linguagem adequado instalado. Para isso, é possível chamar o [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) para invocar o APT. Essa execução geralmente deve ser encapsulada em um perfil Maven específico do Cloud Manager. Por exemplo, para instalar o Python, faça o seguinte:

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

Essa técnica também pode ser usada para instalar pacotes de idioma específicos. Isto é, usando `gem` para RubyGems ou `pip` para pacotes Python.

>[!NOTE]
>
>Instalar um pacote de sistema dessa maneira não o instala no ambiente de tempo de execução usado para executar o Adobe Experience Manager. Se a instalação de um pacote de sistema no ambiente AEM for necessária, entre em contato com o representante da Adobe.
