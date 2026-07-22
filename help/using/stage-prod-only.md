---
title: Pipelines somente de preparo e somente de produção
description: Saiba como dividir implantações de preparo e produção usando pipelines dedicados.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
TQID: https://experienceleague.adobe.com/whq-Hkwp3mjTr0iftoKZHKdsi0xaKtVXazXjUENoaLk
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 6b0075d2405e89dce1c883a2b5fc0bd952a3fddd
workflow-type: tm+mt
source-wordcount: 975
ht-degree: 53%

---

# Dividir pipelines somente de estágio e somente de produção {#stage-prod-only}

Você pode dividir implantações de preparo e produção usando pipelines dedicados.

## Visão geral {#overview}

Os ambientes de preparo e produção são totalmente combinados. Por padrão, as implantações para eles estão vinculadas a um único pipeline. Um pipeline de implantação é implantado nos ambientes de preparo e produção nesse programa. Embora esse acoplamento seja normalmente adequado, há certos casos de uso em que ocorrem desvantagens:

* Se quiser implantar no preparo, ignore a etapa **Promover para Produção** no pipeline. No entanto, a execução é marcada como cancelada.
* Se você quiser implantar o código mais recente de um ambiente de preparo para produção, será necessário reimplantar todo o pipeline, incluindo a implantação de preparo, mesmo que nenhum código tenha sido alterado lá.
* Os ambientes não podem ser atualizados durante as implantações. Se você atrasar os testes no ambiente de preparo por vários dias antes de promover para a produção, o ambiente de produção permanecerá bloqueado e não poderá ser atualizado. Isso torna impossíveis tarefas não dependentes, como a atualização de [variáveis de ambiente](/help/getting-started/build-environment.md#environment-variables).

Os pipelines somente de preparo e de produção oferecem soluções para esses casos de uso fornecendo opções de implantação dedicadas.

* **Pipelines de Implantação Somente de Preparo:** Implante apenas em um ambiente de preparo com a execução concluída após a implantação e os testes serem concluídos. Um pipeline somente de preparo se comporta de forma idêntica ao pipeline de produção de pilha completa acoplado padrão, mas sem as etapas de implantação de produção (aprovação, agendamento, implantação).
* **Pipelines de Implantação Somente de Produção:** Implante apenas na produção selecionando a execução de estágio bem-sucedida mais recente. Em seguida, implante os artefatos na produção. Os pipelines somente de produção reutilizam artefatos de implantação de estágio, ignorando a fase de compilação.

Os pipelines somente de preparo e somente de produção não são executados enquanto um pipeline de produção de pilha completa está em andamento e vice-versa. Se o pipeline somente de preparo e o pipeline de produção de pilha completa tiverem o acionador **Sobre alterações do Git** configurado e estiverem apontando para a mesma ramificação e repositório, apenas o pipeline somente de preparo será iniciado automaticamente. Os pipelines somente de produção não acionam **`On Git Changes`** porque não estão diretamente vinculados a um repositório.

Os pipelines somente de produção são acionados manualmente, pois não estão vinculados diretamente a um repositório para **Sobre alterações do Git**.

Esses pipelines dedicados oferecem mais flexibilidade, mas observe os seguintes detalhes de operação e recomendações:

>[!NOTE]
>
>Os pipelines somente de produção sempre usam artefatos do pipeline somente de preparo. Esse processo permanece válido mesmo se o pipeline de produção acoplada padrão tiver implantado algo diferente para preparo enquanto isso.
>
>* Esse cenário resulta em reversões de código indesejadas.
>* A Adobe recomenda interromper o uso do pipeline de produção acoplada padrão assim que você começar a usar os pipelines somente de produção e somente de preparo.
>* Se você ainda decidir executar os pipelines acoplados padrão junto com os pipelines somente de preparo/produção, lembre-se da reutilização de artefatos para evitar reversões de código.

## Criação de pipeline {#pipeline-creation}

Os pipelines somente de produção e somente de preparo são criados de maneira semelhante aos [pipelines de produção](/help/using/production-pipelines.md) e [pipelines de não produção](/help/using/non-production-pipelines.md) agrupados padrão. Consulte esses documentos para obter detalhes.

1. Na janela **Pipelines**, clique em **Adicionar pipeline**.

   * Selecione **Adicionar pipeline de não produção** para criar um pipeline somente de preparo.
   * Selecione **Adicionar pipeline somente de produção** para criar um pipeline somente de produção.

   ![Criação de um pipeline somente de produção/preparo](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Determinadas opções estarão esmaecidas se os pipelines correspondentes já existirem.
>
>* **Adicionar pipeline somente de produção** não estará disponível se um pipeline somente de preparo ainda não existir.
>* A opção **Adicionar pipeline de produção** não está disponível se já existir um pipeline acoplado padrão.
>* Somente um pipeline de produção e um pipeline de apenas estágio são permitidos por programa.

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

1. Depois de clicar em **Adicionar pipeline somente produção**, sua caixa de diálogo associada será aberta.
1. No campo **Nome do pipeline**, digite o nome desejado. As opções e funcionalidades restantes da caixa de diálogo funcionam da mesma forma que as da caixa de diálogo de criação de pipeline acoplado padrão.
1. No canto inferior direito da caixa de diálogo, clique em **Salvar**.

   ![Criação de um pipeline somente de produção](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Execução de pipelines somente de produção e somente de preparo {#running}

Os pipelines somente de produção e somente de preparo são executados basicamente da mesma maneira que [todos os outros pipelines](/help/using/managing-pipelines.md#running-pipelines). Consulte a documentação para obter mais detalhes. No entanto, há dois novos recursos desses pipelines.

* Os pipelines somente de preparo e somente de produção oferecem um novo [modo de emergência](#emergency-mode) para ignorar o teste.
* Uma execução de pipeline somente de produção pode ser acionada diretamente dos detalhes de execução de um [pipeline somente de preparo](#stage-only-run).

### Modo de emergência {#emergency-mode}

Ao iniciar pipelines somente de produção e somente de preparo, você será solicitado a confirmar o início e como ele continua.

* O **Modo normal** é uma execução padrão e inclui etapas de teste de preparo.
* O **Modo de emergência** ignora as etapas de teste de estágio.

![Modo de emergência](/help/assets/configure-pipelines/emergency-mode.png)

### Pipelines somente de preparo {#stage-only-run}

Um pipeline somente de preparo é executado quase da mesma maneira que os pipelines acoplados padrão. No entanto, no final da execução, após as etapas de teste, um botão **Promover compilação** é exibido. Esse botão permite iniciar uma execução de pipeline somente de produção. Ele usa os artefatos que foram implantados para preparo na execução. Em seguida, ele os implanta na produção.

![Execução de pipeline somente de preparo](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Clicar em **Promover compilação** solicita que você confirme a execução do pipeline somente de produção relacionado normalmente ou no [modo de emergência](#emergency-mode).

Se não existir um pipeline somente de produção, você será solicitado a criar um.

### Pipelines somente de produção {#prod-only-run}

Para pipelines somente de produção, identifique os artefatos de origem que deseja implantar na produção. Esses detalhes podem ser encontrados na etapa **Preparação de artefato**. É possível navegar até essas execuções para obter mais detalhes e logs.

![Detalhes do artefato](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

