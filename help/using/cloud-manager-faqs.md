---
title: Perguntas frequentes sobre o Cloud Manager
seo-title: Perguntas frequentes sobre o Cloud Manager
description: Consulte Perguntas frequentes do Cloud Manager para obter algumas dicas de solução de problemas
seo-description: Siga esta página para obter respostas sobre as perguntas frequentes do Cloud Manager
translation-type: tm+mt
source-git-commit: 1d4f07ba0aa4630585ccbb35f2d48f0c7e1f3df2
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---


# Perguntas frequentes do Cloud Manager {#cloud-manager-faqs}

A seção a seguir fornece respostas para algumas perguntas frequentes mais frequentes relacionadas ao Cloud Manager.

## 1. É possível usar o Java 11 com compilações do Cloud Manager? {#java-11-cloud-manager}

A compilação do AEM Cloud Manager falha ao tentar alternar a compilação do Java 8 para o 11. O problema pode ter muitas causas e as mais comuns estão documentadas abaixo:

* Adicione o maven-toolchain-plugin com as configurações corretas para Java 11, conforme documentado [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Por exemplo, consulte [código de exemplo de projeto wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Se você encontrar o erro abaixo, será necessário remover o uso do plug-in maven-scr e converter todas as anotações OSGi em anotações OSGi R6. Para obter instruções, consulte [here](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Para o Cloud Manager, cria uma falha no plug-in maven enforcer com o erro `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Esse é um problema conhecido porque o Cloud Manager usa uma versão diferente do java para executar o comando maven versus o código de compilação. Por enquanto, omita `requireJavaVersion` das configurações maven-enforcer-plugin.

## 2. Nossa implantação ficou paralisada porque a verificação de qualidade do código falhou. Há alguma maneira de ignorar este cheque? {#deployment-stuck}

Todas as falhas de qualidade de código, exceto *Classificação de segurança*, são métricas não críticas, portanto, podem ser ignoradas ao expandir os itens na interface de usuário de resultados.

Um usuário com a função [Gerenciador de Implantação, Gerente de Projeto ou Proprietário de Negócios](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) pode substituir os problemas, caso em que o pipeline prossegue ou pode aceitar os problemas, caso em que o pipeline para com uma falha.  Consulte [Portas de três níveis ao executar um pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) para obter mais detalhes.

## 3. As implantações do Cloud Manager falham na etapa de teste de desempenho nos ambientes de serviços gerenciados da Adobe. Como depurar isso para passar pelas métricas críticas? {#debug-critical-metrics}

Consulte [Entenda seus Resultados de Teste](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) para entender os resultados.

Algumas observações sobre a etapa do teste de desempenho:

* A *Etapa de desempenho* é uma etapa de desempenho da Web - o que significa que é o momento de carregar a página usando um navegador da Web.
* Os URLs listados no arquivo CSV de resultado são carregados em um navegador Chrome na infraestrutura do Cloud Manager durante o teste.
* Uma métrica comum que falha é a *taxa de erro*. Para que um URL seja aprovado, o URL principal deve ser carregado com o status 200 e em menos de 20 segundos. As cargas de página que excedem 20 segundos são marcadas como erros 504.
* Se o site exigir a autenticação do usuário, consulte [Teste de desempenho autenticado](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) para configurar o teste para autenticação no site.

## 4. Podemos usar o SNAPSHOT na versão do projeto maven? Como o controle de versão dos pacotes e arquivos jar de pacote funciona para implantações de estágio e produção? {#snapshot-version}

1. Para implantações dev, os arquivos pom.xml git branch devem conter -SNAPSHOT no final do valor `<version>`. Isso permite implantações subsequentes nas quais a versão não é alterada para ainda ser instalada. Em implantações dev, nenhuma versão automática é adicionada ou gerada para a compilação maven.

1. Nas implantações de estágio e de produção, uma versão automática é gerada conforme documentado aqui.

1. Para o controle de versão personalizado em implantações de estágio e produção, defina uma versão maven correta de 3 partes, como `1.0.0`. Aumente a versão sempre que precisar fazer outra implantação na produção.

1. O Cloud Manager adiciona automaticamente sua versão aos builds stage e production e até cria uma ramificação git. Nenhuma configuração especial é necessária. Se a etapa 3 acima for ignorada, a implantação ainda funcionará normalmente e uma versão será definida automaticamente.

1. Se você deixar a versão com `-SNAPSHOT` para criação ou implantação de estágio e produção, tudo bem. O Cloud Manager define automaticamente um número de versão adequado e cria uma tag para você no git. Essa tag pode ser consultada posteriormente, se necessário.

1. Se quiser experimentar algum código experimental no dev, você pode criar um novo ramo git e definir o pipeline para usar esse ramo diferente.  Isso é útil quando o start de implantações falha e você gostaria de testar com versões mais antigas do código para ver quando ele quebrou.

   O comando git abaixo cria uma ramificação remota chamada *testbranch1* contra uma confirmação preexistente específica `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Essa ramificação especial pode ser usada no Gerenciador de nuvem sem afetar outras ramificações:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Consulte a documentação [Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References) para obter mais detalhes.

   Se desejar excluir a ramificação de teste posteriormente, use o comando delete (obviamente, tenha cuidado com esse comando):

   `git push origin --delete testbranch1`

## 5. Falha na criação do Maven nas implantações do Cloud Manager, mas é criada localmente sem erros. Como depurar? {#maven-build-fail}

Consulte [Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) para obter mais detalhes.

## 6. Não é possível definir uma variável por meio de variáveis de pipeline definidas pelo gerenciador de nuvem do rádio. Como depurar esses problemas? {#set-variable}

Se você estiver recebendo um erro 403 ao tentar lista ou definir variáveis de pipeline por comandos semelhantes aos abaixo, então será necessário adicionar uma função de produto *Gerenciador de implantação* do Gerenciador de nuvem no Admin Console.\
Consulte [Permissões de API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) para obter mais detalhes.

Comandos e erros relacionados:

`$ aio cloudmanager:list-pipeline-variables 222`

Erro: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

Erro: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
