---
title: Pipelines somente de preparo e somente de produção - Primeiros usuários
description: Saiba como dividir implantações de preparo e produção usando pipelines dedicados.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 2c6f5692ffa31e02d7338e68063d0c1c03a0c73b
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 98%

---

# Pipelines somente de preparo e somente de produção (Primeiros usuários) {#stage-prod-only}

Saiba como dividir implantações de preparo e produção usando pipelines dedicados.

>[!NOTE]
>
>Este recurso só está disponível por meio do [programa de adoção antecipada](/help/release-notes/2024/2024-8-0.md).

## Visão geral {#overview}

Os ambientes de preparo e produção são totalmente combinados. Por padrão, as implantações para eles estão vinculadas a um único pipeline. Ou seja, um pipeline de implantação é iniciado nos ambientes de preparo e produção desse programa. Embora esse acoplamento seja normalmente adequado, há certos casos de uso em que há desvantagens:

* Se quiser implantar somente em preparo, rejeite a etapa **Promover para produção** no pipeline. No entanto, a execução será marcada como cancelada.
* Se você quiser implantar o código mais recente em um ambiente de preparo para produção, será necessário reimplantar todo o pipeline, incluindo a implantação de preparo, mesmo que nenhum código tenha sido alterado lá.
* Os ambientes não podem ser atualizados durante as implantações. Se você pausar para testar o ambiente de preparo por vários dias antes de promover para a produção, o ambiente de produção permanecerá bloqueado e não poderá ser atualizado. Isso torna impossíveis tarefas não dependentes, como a atualização de [variáveis de ambiente](/help/getting-started/build-environment.md#environment-variables).

Os pipelines somente de preparo e somente de produção oferecem soluções para esses casos de uso fornecendo opções de implantação dedicadas.

* **Pipelines de implantação somente de preparo:** implantam somente em um ambiente de preparo e a execução termina quando a implantação e os testes são concluídos. Um pipeline somente de preparo se comporta de forma idêntica ao pipeline de produção de pilha completa acoplado padrão, mas sem as etapas de implantação de produção (aprovação, agendamento, implantação).
* **Pipelines de implantação somente de produção:** implanta apenas para produção, selecionando a execução de estágio bem-sucedida mais recente. Em seguida, implante seus artefatos na produção. Os pipelines somente de produção reutilizam artefatos da implantação de preparo, ignorando a fase de compilação.

Os pipelines somente de preparo e somente de produção não são executados enquanto um pipeline de produção de pilha completa está em andamento e vice-versa. Se o pipeline somente de preparo e o pipeline de produção de pilha completa tiverem o acionador **Sobre alterações do Git** configurado e estiverem apontando para a mesma ramificação e repositório, apenas o pipeline somente de preparo será iniciado automaticamente. Os pipelines somente de produção não iniciam **`On Git Changes`** porque não estão diretamente vinculados a um repositório.

Os pipelines somente de produção são acionados manualmente, pois não estão vinculados diretamente a um repositório para **Sobre alterações do Git**.

Esses pipelines dedicados oferecem mais flexibilidade, mas observe os seguintes detalhes de operação e recomendações.

>[!NOTE]
>
>Os pipelines somente de produção sempre usam artefatos do pipeline somente de preparo. Isso é verdade mesmo se o pipeline de produção acoplado padrão tiver implantado algo diferente para ser preparado enquanto isso.
>
>* Esse cenário pode levar a reversões de código indesejadas.
>* A Adobe recomenda parar de usar o pipeline de produção acoplada padrão assim que você começar a usar os pipelines somente de produção e somente de preparo.
>* Se você ainda decidir executar os pipelines acoplados padrão junto com os pipelines somente de preparo/produção, lembre-se da reutilização de artefatos para evitar reversões de código.

## Criação de pipeline {#pipeline-creation}

Os pipelines somente de produção e somente de preparo são criados de maneira semelhante aos [pipelines de produção](/help/using/production-pipelines.md) e [pipelines de não produção](/help/using/non-production-pipelines.md) acoplados padrão. Consulte esses documentos para obter detalhes.

1. Na janela **Pipelines**, clique em **Adicionar pipeline**.

   * Selecione **Adicionar pipeline de não produção** para criar um pipeline somente de preparo.
   * Selecione **Adicionar pipeline somente de produção** para criar um pipeline somente de produção.

   ![Criação de um pipeline somente de produção/preparo](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Determinadas opções podem estar esmaecidas se os pipelines correspondentes já existirem.
>
>* A opção **Adicionar pipeline somente de produção** não estará disponível se não existir um pipeline somente de preparo.
>* A opção **Adicionar pipeline de produção** não está disponível se já existir um pipeline acoplado padrão.
>* São permitidos apenas um pipeline somente de produção e um pipeline somente de preparo por programa.

### Pipelines somente de preparo {#stage-only}

1. Depois de selecionar a opção **Adicionar pipeline de não produção**, a caixa de diálogo **Adicionar pipeline de não produção** é exibida.
1. Para criar um pipeline somente de preparo, selecione o ambiente de preparo no campo **Ambientes de implantação elegíveis** para o seu pipeline.
1. Preencha os campos restantes.
1. Clique em **Continuar**.

   ![Criação de um pipeline somente de preparo](/help/assets/configure-pipelines/stage-only.png)

1. Na guia **Teste de preparo**, defina o teste a ser executado no ambiente de preparo.
1. Clique em **Salvar**.

   ![Parâmetros de teste para um pipeline somente de preparo](/help/assets/configure-pipelines/stage-only-test.png)

### Pipelines somente de produção {#prod-only}

1. Depois de selecionar a opção **Adicionar pipeline somente de produção**, a caixa de diálogo **Adicionar pipeline somente de produção** é exibida.
1. No campo **Nome do pipeline**, digite o nome desejado. As opções e funcionalidades restantes da caixa de diálogo funcionam da mesma forma que as da caixa de diálogo de criação de pipeline acoplado padrão. 
1. No canto inferior direito da caixa de diálogo, clique em **Salvar**.

   ![Criação de um pipeline somente de produção](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Execução de pipelines somente de produção e somente de preparo {#running}

Os pipelines somente de produção e somente de preparo são executados basicamente da mesma maneira que [todos os outros pipelines](/help/using/managing-pipelines.md#running-pipelines). Consulte a documentação para obter mais detalhes. No entanto, há dois novos recursos desses pipelines.

* Os pipelines somente de preparo e somente de produção oferecem um novo [modo de emergência](#emergency-mode) para ignorar o teste.
* Uma execução de pipeline somente de produção pode ser acionada diretamente dos detalhes de execução de um [pipeline somente de preparo](#stage-only-run).

### Modo de emergência {#emergency-mode}

Ao iniciar pipelines somente de produção e somente de preparo, você será solicitado a confirmar o início e como eles são iniciados.

* O **Modo normal** é uma execução padrão e inclui etapas de teste de preparo.
* O **Modo de emergência** ignora as etapas de teste de estágio.

![Modo de emergência](/help/assets/configure-pipelines/emergency-mode.png)

### Pipelines somente de preparo {#stage-only-run}

Um pipeline somente de preparo é executado quase da mesma maneira que os pipelines acoplados padrão. No entanto, no final da execução, após as etapas de teste, um botão **Promover compilação** é exibido. Esse botão permite iniciar uma execução de pipeline somente de produção usando os artefatos que foram implantados no preparo durante a execução e implantá-los na produção.

![Execução de pipeline somente de preparo](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Clicar em **Promover compilação** solicita que você confirme a execução do pipeline somente de preparo relacionado normalmente ou no [modo de emergência](#emergency-mode).

Se não existir um pipeline somente de produção, você será solicitado a criar um.

### Pipelines somente de produção {#prod-only-run}

Para pipelines somente de produção, identifique os artefatos de origem que deseja implantar na produção. Esses detalhes podem ser encontrados na etapa **Preparação de artefato**. É possível navegar até essas execuções para obter mais detalhes e logs.

![Detalhes do artefato](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

