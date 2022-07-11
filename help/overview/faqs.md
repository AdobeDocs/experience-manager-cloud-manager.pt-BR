---
title: Perguntas frequentes sobre o Cloud Manager
description: Este documento fornece respostas às perguntas mais frequentes sobre o Cloud Manager para clientes do AMS.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 6be659e02df0657ec7d3dbce8c18c44a327a36f4
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 1%

---


# Perguntas frequentes sobre o Cloud Manager {#cloud-manager-faqs}

Este documento fornece respostas às perguntas mais frequentes sobre o Cloud Manager para clientes do AMS.

## É possível usar o Java 11 com builds do Cloud Manager? {#java-11}

Sim. Será necessário adicionar a variável `maven-toolchains-plugin` com as configurações corretas para o Java 11.

* Esse processo está documentado [aqui.](/help/getting-started/using-the-wizard.md)
* Para ver um exemplo, consulte a [código do projeto de amostra wknd.](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)

## Minha build falha com um erro sobre o maven-scr-plugin após mudar do Java 8 para o Java 11. O que posso fazer? {#maven-src-plugin}

A build do AEM Cloud Manager pode falhar ao tentar alternar a build do Java 8 para o 11. Se você encontrar o seguinte erro, será necessário remover `maven-scr-plugin` e converter todas as anotações OSGi em anotações OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Para obter instruções sobre como remover este plug-in, [veja aqui.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)

## Minha build falha com um erro sobre RequireJavaVersion após alternar do Java 8 para o Java 11. O que posso fazer? {#requirejavaversion}

Para builds do Cloud Manager, a variável `maven-enforcer-plugin` pode falhar com esse erro

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Esse é um problema conhecido porque o Cloud Manager usa uma versão diferente do Java para executar o comando maven versus o código de compilação. Simplesmente omite `requireJavaVersion` do `maven-enforcer-plugin` configurações.

## A verificação de qualidade do código falhou e sua implantação travou. Existe uma maneira de ignorar esta verificação? {#deployment-stuck}

Sim. Todas as falhas de qualidade de código, exceto classificações de segurança, são métricas não críticas, portanto, podem ser ignoradas como parte de um pipeline de implantação, expandindo os itens na interface do usuário de resultados.

Um usuário com [Gerenciador de implantação, Gerenciador de projeto ou Proprietário comercial](/help/requirements/users-and-roles.md#role-definitions) pode substituir os problemas, caso o pipeline continue ou possa aceitar os problemas, caso o pipeline pare com uma falha.

Veja os documentos [Portas de três níveis ao executar um pipeline](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) e [Configuração de pipeline de não produção](/help/using/non-production-pipelines.md#understanding-the-flow) para obter mais detalhes.

## As implantações do Cloud Manager falham na etapa de teste de desempenho nos ambientes do Adobe Managed Services. Como depurar isso para passar as métricas críticas? {#debug-critical-metrics}

Não há resposta única para esta questão. Mas estes são alguns pontos importantes sobre a etapa do teste de desempenho que você deve ter em mente:

* Esta etapa é uma etapa de desempenho da Web, ou seja, o tempo para carregar a página usando um navegador da Web.
* Os URLs listados no arquivo .csv de resultado são carregados em um navegador Chrome na infraestrutura do Cloud Manager durante o teste.
* Uma métrica comum que falha é a taxa de erro.
   * Para que um URL seja aprovado, o URL principal deve ser carregado com `200` e em menos de `20` segundos.
   * Carregamentos de página que excedem `20` segundos são marcados como `504` erros.
* Se o site exigir autenticação do usuário, consulte o documento [Entender os resultados de teste](/help/using/code-quality-testing.md#authenticated-performance-testing) para configurar o teste para autenticar em seu site.

Consulte o documento [Como entender os resultados de teste](/help/using/code-quality-testing.md) para mais informações sobre os controlos de qualidade.

## Posso usar o SNAPSHOT para a versão do projeto Maven? {#snapshot}

Sim. Para implantações de desenvolvedores, a ramificação git `pom.xml` os arquivos devem conter `-SNAPSHOT` no final do `<version>` valor.

Isso permite que a implantação subsequente ainda seja instalada quando a versão não foi alterada. Em implantações de desenvolvedores, nenhuma versão automática é adicionada ou gerada para a build maven.

Você também pode definir a versão como `-SNAPSHOT` para builds ou implantações de estágio e produção. O Cloud Manager define automaticamente um número de versão adequado e cria uma tag para você no git. Essa tag pode ser consultada posteriormente, se necessário.

Mais detalhes sobre o manuseio de versão são [documentado aqui.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling.html)

## Como o controle de versão de pacote e pacote funciona para implantações de armazenamento temporário e de produção? {#staging-production}

Em implantações de armazenamento temporário e produção, uma versão automática é gerada [conforme documentado aqui.](/help/managing-code/maven-project-version.md)

Para o controle de versão personalizado em implantações de estágio e produção, defina uma versão maven adequada em três partes como `1.0.0`. Aumente a versão sempre que implantar na produção.

O Cloud Manager adiciona automaticamente sua versão ao palco e compilações de produção e cria uma ramificação git. Nenhuma configuração especial é necessária. Se você não definir uma versão maven conforme descrito anteriormente, a implantação ainda terá sucesso e uma versão será definida automaticamente.

## Minha build maven falha para implantações do Cloud Manager, mas é criada localmente sem erros. O que há de errado? {#maven-build-fail}

Veja isso [recurso git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) para obter mais detalhes.

## Não consigo definir uma variável usando um comando aio. O que posso fazer? {#set-variable}

Você pode receber um erro 403, como o seguinte, ao tentar listar ou definir variáveis de pipeline por `aio` comandos.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

Nesse caso, o usuário que executa esses comandos precisa ser adicionado ao **Gerenciador de implantação** na Admin Console.

Consulte [Permissões de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) para obter mais detalhes.
