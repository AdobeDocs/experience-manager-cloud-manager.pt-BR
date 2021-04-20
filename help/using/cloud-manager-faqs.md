---
title: Perguntas frequentes do Cloud Manager
seo-title: Perguntas frequentes do Cloud Manager
description: Consulte as Perguntas frequentes do Cloud Manager para obter algumas dicas de solução de problemas
seo-description: Siga esta página para obter respostas sobre as perguntas frequentes do Cloud Manager
feature: Getting Started
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---


# Perguntas frequentes do Cloud Manager {#cloud-manager-faqs}

A seção a seguir fornece respostas para perguntas frequentes relacionadas ao Cloud Manager.

## É possível usar o Java 11 com builds do Cloud Manager? {#java-11-cloud-manager}

AEM build do Cloud Manager falha ao tentar alternar a build do Java 8 para o 11. O problema pode ter muitas causas e as mais comuns estão documentadas abaixo:

* Adicione o maven-toolchains-plugin com as configurações corretas para Java 11 conforme documentado [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Por exemplo, consulte o [código do projeto de amostra wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Se encontrar o erro abaixo, é necessário remover o uso de `maven-scr-plugin` e converter todas as anotações OSGi em anotações OSGi R6. Para obter instruções, consulte [aqui](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Para builds do Cloud Manager, o maven enforcer plugin falha com o erro `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Esse é um problema conhecido porque o Cloud Manager usa uma versão diferente do Java para executar o comando maven versus o código de compilação. Por enquanto, omita `requireJavaVersion` de suas configurações maven-enforcer-plugin.

## Nossa implantação ficou paralisada porque a verificação de qualidade do código falhou. Existe uma maneira de ignorar esta verificação? {#deployment-stuck}

Todas as falhas de qualidade de código, exceto para *Classificação de segurança*, são métricas não críticas, portanto, podem ser ignoradas ao expandir os itens na interface do usuário de resultados.

Um usuário com a função [Deployment Manager, Project Manager ou Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) pode substituir os problemas, caso o pipeline continue ou possa aceitar os problemas, caso em que o pipeline pára com uma falha.  Consulte [Portas de três níveis ao executar um pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) para obter mais detalhes.

## As implantações do Cloud Manager falham na etapa de teste de desempenho nos ambientes do Adobe Managed Services. Como depurar isso para passar as métricas críticas? {#debug-critical-metrics}

Consulte [Entender os resultados de teste](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) para entender os resultados.

Algumas observações sobre a etapa Teste de desempenho:

* A *Etapa de Desempenho* é uma etapa de desempenho da Web, ou seja, o tempo para carregar a página usando um navegador da Web.
* Os URLs listados no arquivo *CSV* resultante são carregados em um navegador Chrome na infraestrutura do Cloud Manager durante o teste.
* Uma métrica comum que falha é a *taxa de erro*. Para que um URL seja aprovado, o URL principal deve ser carregado com o status `200` e em menos de `20` segundos. Carregamentos de página que excedem `20` segundos são marcados como erros `504`.
* Se seu site exigir autenticação de usuário, consulte [Teste de desempenho autenticado](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) para configurar o teste para autenticar em seu site.

## Podemos usar o SNAPSHOT na versão do projeto Maven? Como o controle de versão dos pacotes e arquivos jar funciona para implantações de Preparo e Produção? {#snapshot-version}

Consulte os seguintes cenários para saber mais sobre o controle de versão dos pacotes e dos arquivos jar do pacote para implantações de Preparo e Produção:

1. Para implantações de desenvolvedores, os arquivos `pom.xml` da ramificação Git devem conter `-SNAPSHOT` no final do valor `<version>`. Isso permite a implantação subsequente em que a versão não é alterada para ainda ser instalada. Em implantações de desenvolvedores, nenhuma versão automática é adicionada ou gerada para a build maven.

1. Na implantação de Preparo e Produção, uma versão automática é gerada conforme documentado [aqui](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Para o controle de versão personalizado em implantações de Preparo e Produção, defina uma versão maven correta de 3 partes como `1.0.0`. Aumente a versão sempre que precisar fazer outra implantação na produção.

1. O Cloud Manager adiciona automaticamente sua versão ao Stage e às builds de produção e até cria uma ramificação Git. Nenhuma configuração especial é necessária. Se a etapa 3 acima for ignorada, a implantação ainda funcionará corretamente e uma versão será definida automaticamente.

1. Não há problemas, se você deixar a versão com `-SNAPSHOT` para Preparo e Produção, builds ou implantações. O Cloud Manager define automaticamente um número de versão adequado e cria uma tag para você no Git. Essa tag pode ser consultada posteriormente, se necessário.

1. Se quiser experimentar algum código experimental no ambiente de desenvolvimento, você pode criar uma nova ramificação Git e definir o pipeline para usar essa ramificação diferente. Isso é útil quando as implantações começam a falhar e você gostaria de testar com versões mais antigas do código para ver quando quebrou.

   O comando Git abaixo cria uma ramificação remota chamada *testbranch1* contra uma confirmação preexistente específica `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Essa ramificação especial pode ser usada no Cloud Manager sem afetar outras ramificações:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Consulte a [documentação do Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References) para obter mais detalhes.

   Se desejar excluir a ramificação de teste posteriormente, use o comando delete:

   `git push origin --delete testbranch1`

## A build do Maven falha nas implantações do Cloud Manager, mas é criada localmente sem erros. Como depurar? {#maven-build-fail}

Consulte [Recurso Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) para obter mais detalhes.

## Não é possível definir uma variável por meio das variáveis de pipeline definidas do aio cloud manager. Como depurar esses problemas? {#set-variable}

Se você estiver recebendo um erro `403` ao tentar listar ou definir variáveis de pipeline por comandos semelhantes aos abaixo, você precisa ser adicionado como uma função de produto *Deployment Manager* Cloud Manager no Admin Console.\
Consulte [Permissões da API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) para obter mais detalhes.

Comandos e erros relacionados:

`$ aio cloudmanager:list-pipeline-variables 222`

*Erro*:  `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Erro*:  `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
