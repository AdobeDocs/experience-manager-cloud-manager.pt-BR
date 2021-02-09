---
title: Noções básicas sobre o Ambiente Build
description: Siga esta página para saber mais sobre ambientes
translation-type: tm+mt
source-git-commit: 60270a7adb612355ff6d6928adcff8e94cabe092
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 0%

---


# Noções básicas sobre o Ambiente de compilação {#build-environment-details}

O Cloud Manager cria e testa seu código usando um ambiente de compilação especializado. Esse ambiente tem os seguintes atributos:

* O ambiente build é baseado no Linux, derivado do Ubuntu 18.04.
* O Apache Maven 3.6.0 está instalado.
* As versões do Java instaladas são Oracle JDK 8u202 e 11.0.2.
* Existem outros pacotes de sistema instalados que são necessários:

   * bzip2
   * descompactar
   * libpng
   * imagemagick
   * gráfico

* Outros pacotes podem ser instalados no momento da criação, conforme descrito [abaixo](#installing-additional-system-packages).
* Cada obra é feita com um ambiente intocado; o container build não mantém nenhum estado entre as execuções.
* O Maven é sempre executado com estes três comandos:

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`

* O Maven é configurado no nível do sistema com um arquivo settings.xml que inclui automaticamente o repositório Adobe público **Artifato**. (Consulte [Repositório Maven Público do Adobe](https://repo.adobe.com/) para obter mais detalhes).

>[!NOTE]
>Embora o Cloud Manager não defina uma versão específica de `jacoco-maven-plugin`, a versão usada deve ser pelo menos `0.7.5.201505241946`.


>[!NOTE]
>Consulte os seguintes recursos adicionais para saber como usar as APIs do Cloud Manager:
> * [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Criação de uma integração de API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/create-api-integration.md)
>* [Permissões da API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md)


## Uso do Java 11 {#using-java-11}

O Cloud Manager agora é compatível com a criação de projetos de clientes com Java 8 e Java 11. Por padrão, os projetos são criados usando o Java 8. Os clientes que pretendem usar o Java 11 em seus projetos podem fazer isso usando o [Plug-in Apache Maven Toolchain](https://maven.apache.org/plugins/maven-toolchains-plugin/).

Para fazer isso, no arquivo pom.xml, adicione uma entrada `<plugin>` com a seguinte aparência:

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
>Os valores de `vendor` suportados são `oracle` e `sun` e os valores de `version` suportados são `1.8`, `1.11` e `11`.

>[!NOTE]
>A compilação do projeto do Gerenciador de nuvem ainda está usando o Java 8 para chamar o Maven, portanto, verificar ou impor a versão do Java configurada no plug-in da cadeia de ferramentas por meio de plug-ins como o [Plug-in do Apache Maven Execcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) não funciona e esses plug-ins não devem ser usados.

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

O Cloud Manager permite que essas variáveis sejam configuradas por meio da API do Cloud Manager ou da CLI do Cloud Manager por pipeline. As variáveis podem ser armazenadas como texto sem formatação ou como criptografadas em repouso. Em ambos os casos, as variáveis são disponibilizadas no ambiente de compilação como uma variável de ambiente que pode ser referenciada no arquivo `pom.xml` ou em outros scripts de compilação.

Para definir uma variável usando a CLI, execute um comando como:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

As variáveis atuais podem ser listadas:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Os nomes de variáveis só podem conter caracteres alfanuméricos e sublinhados (_). Por convenção, os nomes devem ser todos maiúsculos. Há um limite de 200 variáveis por pipeline, cada nome deve ter menos de 100 caracteres e cada valor deve ter menos de 2048 caracteres no caso de variáveis de tipo de sequência de caracteres e 500 caracteres no caso de variáveis de tipo de sequência de caracteres secreta.

Quando usado dentro de um arquivo `Maven pom.xml`, geralmente é útil mapear essas variáveis para propriedades Maven usando uma sintaxe semelhante a esta:

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

Algumas compilações exigem a instalação de pacotes de sistema adicionais para funcionar totalmente. Por exemplo, uma compilação pode chamar um script Python ou ruby e, como resultado, precisa ter um intérprete de linguagem apropriado instalado. Isso pode ser feito chamando o [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) para chamar a APT. Essa execução geralmente deve ser envolvida em um perfil Maven específico do Cloud Manager. Por exemplo, para instalar o python:

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
>Instalar um pacote de sistema desta maneira **não** o instala no ambiente de tempo de execução usado para executar o Adobe Experience Manager. Se precisar de um pacote de sistema instalado no ambiente AEM, entre em contato com o representante do Adobe.
