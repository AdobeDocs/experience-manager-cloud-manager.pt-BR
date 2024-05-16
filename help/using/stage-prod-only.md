---
title: Pipelines somente de preparo e somente de produção
description: Saiba como dividir implantações de preparo e produção usando pipelines dedicados.
source-git-commit: c09fbf30270523018a36b128d43cbf10e65daf54
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 1%

---


# Pipelines somente de preparo e somente de produção {#stage-prod-only}

Saiba como dividir implantações de preparo e produção usando pipelines dedicados.

>[!NOTE]
>
>Este recurso só está disponível por meio do [programa de adoção antecipada.](/help/release-notes/current.md#early-adoption)

## Visão geral {#overview}

Os ambientes de preparo e produção são totalmente combinados. Por padrão, as implantações para eles estão vinculadas a um único pipeline. Isso é um pipeline de implantação implantado nos ambientes de preparo e produção nesse programa. Embora esse acoplamento seja normalmente adequado, há certos casos de uso em que há desvantagens:

* Se desejar implantar somente em preparo, você só poderá fazer isso rejeitando a variável **Promover para produção** etapa no pipeline. No entanto, a execução será marcada como cancelada.
* Se você quiser implantar o código mais recente em um ambiente de preparo para produção, será necessário reimplantar todo o pipeline, incluindo a implantação de preparo, mesmo que nenhum código tenha sido alterado lá.
* Como os ambientes não podem ser atualizados durante as implantações, se você quiser pausar e testar o ambiente de preparo por vários dias antes de promover para produção, o ambiente de produção não poderá ser atualizado. Isso torna tarefas não dependentes, como atualização [variáveis de ambiente](/help/getting-started/build-environment.md#environment-variables) impossível.

Os pipelines somente de preparo e de produção oferecem soluções para esses casos de uso fornecendo opções de implantação dedicadas.

* **Pipelines de implantação somente de preparo** implante somente em um ambiente de preparo com a execução terminada depois que a implantação e os testes forem concluídos.
   * Um pipeline somente de estágio se comporta de forma idêntica ao pipeline de produção de pilha completa acoplada padrão, mas sem as etapas de implantação de produção (aprovação, agendamento, implantação).
* **Pipelines de implantação somente de produção** implante somente em um ambiente de produção com a opção de selecionar uma execução concluída e validada com êxito no preparo e implante seus artefatos no prod.
   * Os pipelines somente de produção reutilizarão os artefatos das implantações de preparo, ignorando a fase de criação.

Os pipelines somente de preparo e somente de produção não serão executados enquanto um pipeline de produção de pilha completa estiver em execução e vice-versa.

Esses pipelines dedicados oferecem mais flexibilidade, mas observe os seguintes detalhes de operação e recomendações.

>[!NOTE]
>
>Os pipelines somente de produção sempre usarão os artefatos do pipeline somente de preparo, independentemente do que pode ter sido implantado no estágio por meio do pipeline de produção acoplada padrão enquanto isso.
>
>* Isso pode levar a reversões de código indesejadas.
>* A Adobe recomenda parar de usar o pipeline de produção acoplada padrão assim que você começar a usar os pipelines somente de produção e somente de preparo.
>* Se você ainda decidir executar os pipelines acoplados padrão e os pipelines de preparo/somente produção, lembre-se da reutilização de artefatos para evitar reversões de código.

## Criação de pipeline {#pipeline-creation}

Os pipelines somente de produção e somente de estágio são criados de maneira semelhante ao padrão acoplado [pipelines de produção](/help/using/production-pipelines.md) e [pipelines de não produção.](/help/using/non-production-pipelines.md) Consulte esses documentos para obter detalhes.

1. No **Pipelines** toque ou clique em **Adicionar pipeline**.

   * Selecionar **Adicionar pipeline de não produção** para criar um pipeline somente de preparo.
   * Selecionar **Adicionar pipeline somente de produção** para criar um pipeline somente de produção.

   ![Criação de um pipeline de produção/apenas de preparo](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Determinadas opções podem estar esmaecidas se os pipelines correspondentes já existirem.
>
>* **Adicionar pipeline somente de produção** não estarão disponíveis se um pipeline somente de estágio ainda não existir.
>* **Adicionar pipeline de produção** não estarão disponíveis se um pipeline acoplado padrão já existir.
>* Somente um pipeline de produção e um pipeline de apenas estágio são permitidos por programa.

### Pipelines somente de preparo {#stage-only}

1. Depois de selecionar a variável **Adicionar pipeline de não produção** opção, a variável **Adicionar pipeline de não produção** será aberta.
1. Para criar um pipeline somente de preparo, selecione o ambiente de preparo na **Ambientes de implantação qualificados** para o seu pipeline. Complete os campos restantes e toque ou clique **Continuar**.

   ![Criação de um pipeline somente de preparo](/help/assets/configure-pipelines/stage-only.png)

1. No **Teste de preparo** , você poderá definir testes que devem ser executados no ambiente de preparo. Toque ou clique **Salvar** para salvar o novo pipeline.

   ![Parâmetros de teste para um pipeline somente de preparo](/help/assets/configure-pipelines/stage-only-test.png)

### Pipelines de produção apenas {#prod-only}

1. Depois de selecionar a variável **Adicionar pipeline somente de produção** opção, a variável **Adicionar pipeline somente de produção** será aberta.
1. Forneça um **Nome do pipeline**. As opções e funcionalidades restantes da caixa de diálogo funcionam da mesma forma que as da caixa de diálogo de criação de pipeline acoplado padrão. Toque ou clique **Salvar** para salvar o pipeline.

   ![Criação de um pipeline somente de produção](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Execução de pipelines somente de produção e somente de preparo {#running}

Os pipelines somente de produção e somente de preparo são executados da mesma forma que os de [todos os outros pipelines são executados.](/help/using/managing-pipelines.md#running-pipelines) Consulte essa documentação para obter detalhes.

Além disso, uma execução de pipeline somente de produção pode ser acionada diretamente dos detalhes de execução de um pipeline somente de preparo.

### Pipelines somente de preparo {#stage-only-run}

Um pipeline somente de estágio é executado quase da mesma maneira que os pipelines acoplados padrão. No entanto, no final da execução, após as etapas de teste, uma **Promover build** O botão permite iniciar uma execução de pipeline somente de produção que usa os artefatos implantados no estágio por essa execução e os implanta na produção.

![Execução de pipeline somente de preparo](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

A variável **Promover build** O botão só será exibido se você estiver na última execução de pipeline somente de estágio bem-sucedida. Depois de tocar ou clicar, ele solicitará que você confirme a execução do pipeline somente de produção ou crie um pipeline somente de produção, se ainda não existir um.

### Pipelines de produção apenas {#prod-only-run}

Para pipelines somente de produção, é importante identificar os artefatos de origem que devem ser implantados na produção. Esses detalhes podem ser encontrados no **Preparação de artefato** etapa. Você pode navegar até essas execuções para obter mais detalhes e logs.

![Detalhes do artefato](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
