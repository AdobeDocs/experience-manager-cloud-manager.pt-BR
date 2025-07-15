---
title: Perguntas frequentes sobre o Cloud Manager
description: Encontre as respostas para as perguntas mais frequentes sobre o Cloud Manager para clientes do AMS.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: e7e9844b5f06552fc2104584c63935dee7a9fa89
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 100%

---


# Perguntas frequentes sobre o Cloud Manager {#cloud-manager-faqs}

Este documento fornece respostas às perguntas mais frequentes sobre o Cloud Manager para clientes do AMS.

<!-- 
## Is it possible to use Java 11 with Cloud Manager builds? {#java-11}

Yes. You need to add the `maven-toolchains-plugin` with the correct settings for Java 11.

* This process is documented [here](/help/getting-started/using-the-wizard.md).
* For an example, see the [WKND sample project code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75). -->

## Minha compilação falha com um erro sobre maven-scr-plugin após alternar do Java 8 para o Java 11. O que posso fazer? {#maven-src-plugin}

A compilação do AEM Cloud Manager pode falhar ao tentar alternar a compilação do Java 8 para o 11. Se você encontrar o erro a seguir, será necessário remover `maven-scr-plugin` e converter todas as anotações OSGi para anotações OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Para obter instruções sobre como remover esse plug-in, consulte [esta](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/) página.

## Minha compilação falha com um erro sobre RequireJavaVersion após alternar do Java 8 para o Java 11. O que posso fazer? {#requirejavaversion}

Para builds do Cloud Manager, o `maven-enforcer-plugin` pode falhar com esse erro

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Esse problema conhecido ocorre porque o Cloud Manager usa uma versão diferente do Java para executar o comando Maven em relação ao código de compilação. Omita o `requireJavaVersion` das configurações do `maven-enforcer-plugin`.

## A verificação da qualidade do código falhou e a implantação está travada. Existe uma maneira de ignorar essa verificação? {#deployment-stuck}

Sim. Todas as falhas de qualidade de código, exceto classificações de segurança, são métricas não críticas. Portanto, podem ser ignoradas como parte de um pipeline de implantação expandindo os itens na interface de resultados.

Um usuário com a função [Gerente de implantação, Gerente de projeto ou Proprietário da empresa](/help/requirements/users-and-roles.md#role-definitions) pode ignorar os problemas. Nesse caso, o pipeline prossegue. Ou eles podem aceitar os problemas. Nesse caso, o pipeline é interrompido com uma falha.

Consulte os documentos [Portas de três níveis ao executar um pipeline](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) e [Configuração de pipelines de não produção](/help/using/non-production-pipelines.md#understanding-the-flow) para obter mais detalhes.

## As implantações do Cloud Manager falham na etapa de teste de desempenho nos ambientes do Adobe Managed Services. Como esse problema pode ser depurado para passar nas métricas críticas? {#debug-critical-metrics}

Não há resposta única para esta questão. No entanto, os seguintes aspectos da etapa do teste de desempenho podem ser úteis:

* Esta é uma etapa de desempenho da Web. Ou seja, é sobre o tempo para carregar a página usando um navegador da Web.
* Os URLs listados no arquivo .csv resultante são carregados em um navegador Chrome na infraestrutura do Cloud Manager durante o teste.
* Uma métrica comum que falha é a taxa de erro. Para que um URL seja aprovado, o URL principal precisa ser carregado com o status `200` e em menos de `20` segundos. Carregamentos de página que excedem `20` segundos são marcados como erros `504`.
* Se o site exigir autenticação do usuário, consulte [Noções básicas dos resultados dos testes](/help/using/code-quality-testing.md#authenticated-performance-testing) para configurar o teste para que você possa autenticar em seu site.

Consulte [Noções básicas dos resultados dos testes](/help/using/code-quality-testing.md) para mais informações sobre as verificações de qualidade.

## Posso usar o SNAPSHOT para a versão do projeto Maven? {#snapshot}

Sim. Para implantações de desenvolvedores, os arquivos `pom.xml` da ramificação Git precisam conter `-SNAPSHOT` no final do valor `<version>`.

Isso permite que as implantações subsequentes ainda sejam instaladas quando a versão não for alterada. Em implantações de desenvolvedores, nenhuma versão automática é adicionada ou gerada para a compilação maven.

Você também pode definir a versão como `-SNAPSHOT` para compilações ou implantações de preparo ou de produção. O Cloud Manager define automaticamente um número de versão adequado e cria uma tag para você no Git. Essa tag pode ser referenciada posteriormente, se necessário.

Mais detalhes sobre o manuseio de versão estão [documentados aqui](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## Como funciona o controle de versão de pacotes para implantações de preparo e produção? {#staging-production}

As implantações de preparo e produção geram uma versão automática, [conforme documentado aqui](/help/managing-code/maven-project-version.md).

Para o controle de versão personalizado em implantações de preparo e produção, defina uma versão maven adequada com três partes como `1.0.0`. Aumente a versão sempre que implantar na produção.

O Cloud Manager adiciona automaticamente a versão às compilações de preparo e produção e cria uma ramificação Git. Nenhuma configuração especial é necessária. Se você não definir uma versão do Maven conforme descrito anteriormente, a implantação ainda será bem-sucedida e uma versão será definida automaticamente.

## Minha compilação maven falha para implantações do Cloud Manager, mas é criada localmente sem erros. O que há de errado? {#maven-build-fail}

Consulte esse [recurso do Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) para obter mais detalhes.

## Não consigo definir uma variável usando um comando aio. O que posso fazer? {#set-variable}

Você pode receber um erro 403, como o seguinte, ao tentar listar ou definir variáveis de pipeline por meio de comandos `aio`.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

Nesse caso, o usuário que executa esses comandos precisa ser adicionado à função **Gerente de implantação** no Admin Console.

Consulte [Permissões da API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) para obter mais detalhes.
