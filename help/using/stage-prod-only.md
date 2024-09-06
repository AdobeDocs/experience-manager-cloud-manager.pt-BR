---
title: Pipelines somente de preparo e somente de produção
description: Saiba como dividir implantações de preparo e produção usando pipelines dedicados.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 03f7429fd2c4a6dd4c8ae3228eff9c8cdab1ded8
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 42%

---

# Pipelines somente de preparo e somente de produção {#stage-prod-only}

Saiba como dividir implantações de preparo e produção usando pipelines dedicados.

>[!NOTE]
>
>Este recurso só está disponível por meio do [programa de adoção antecipada](/help/release-notes/current.md#early-adoption).

## Visão geral {#overview}

Os ambientes de preparo e produção são totalmente combinados. Por padrão, as implantações para eles estão vinculadas a um único pipeline. Ou seja, um pipeline de implantação é implantado nos ambientes de preparo e produção nesse programa. Embora esse acoplamento seja normalmente adequado, há certos casos de uso em que há desvantagens:

* Se você deseja implantar somente em preparo, rejeite a etapa **Promover para Produção** no pipeline. No entanto, a execução é marcada como cancelada.
* Se você quiser implantar o código mais recente em um ambiente de preparo para produção, será necessário reimplantar todo o pipeline, incluindo a implantação de preparo, mesmo que nenhum código tenha sido alterado lá.
* Os ambientes não podem ser atualizados durante as implantações. Se você pausar para testar o ambiente de preparo por vários dias antes de promover para a produção, o ambiente de produção permanecerá bloqueado e não poderá ser atualizado. Este cenário torna impossíveis tarefas não dependentes, como a atualização de [variáveis de ambiente](/help/getting-started/build-environment.md#environment-variables).

Os pipelines somente de preparo e somente de produção oferecem soluções para esses casos de uso fornecendo opções de implantação dedicadas.

* **Pipelines de Implantação Somente de Preparo:** Implanta apenas em um ambiente de preparo com a execução concluída após a implantação e os testes serem concluídos. Um pipeline somente de preparo se comporta de forma idêntica ao pipeline de produção de empilhamento completo acoplado padrão, mas sem as etapas de implantação de produção (aprovação, agendamento, implantação).
* **Pipelines de Implantação Somente de Produção:** Implanta apenas para produção selecionando a execução de estágio bem-sucedida mais recente. Em seguida, implante seus artefatos na produção. Os pipelines somente de produção reutilizam artefatos de implantação de estágio, ignorando a fase de compilação.

Os pipelines somente de preparo e somente de produção não são executados enquanto um pipeline de produção de pilha completa está em andamento e vice-versa. Se o pipeline de produção somente de preparo e o pipeline de pilha completa tiverem o acionador **Em alterações do Git** configurado e estiverem apontando para a mesma ramificação e repositório, apenas o pipeline somente de preparo será iniciado automaticamente. Os pipelines somente de produção não iniciam **`On Git Changes`** porque não estão diretamente vinculados a um repositório.

Os pipelines somente de produção são acionados manualmente, pois não estão vinculados diretamente a um repositório para **Sobre Alterações do Git**.

Esses pipelines dedicados oferecem mais flexibilidade, mas observe os seguintes detalhes de operação e recomendações.

>[!NOTE]
>
>Os pipelines somente de produção sempre usam artefatos do pipeline somente de preparo. Esse processo continua verdadeiro mesmo se o pipeline de produção acoplada padrão tiver implantado algo diferente para ser preparado enquanto isso.
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

1. Após selecionar a opção **Adicionar pipeline de não produção**, a caixa de diálogo **Adicionar pipeline de não produção** é aberta.
1. Para criar um pipeline somente de preparo, selecione o ambiente de preparo no campo **Ambientes de implantação qualificados** para seu pipeline.
1. Preencha os campos restantes.
1. Clique em **Continuar**.

   ![Criação de um pipeline somente de preparo](/help/assets/configure-pipelines/stage-only.png)

1. Na guia **Teste de Preparo**, defina o teste a ser executado no ambiente de preparo.
1. Clique em **Salvar**.

   ![Parâmetros de teste para um pipeline somente de preparo](/help/assets/configure-pipelines/stage-only-test.png)

### Pipelines somente de produção {#prod-only}

1. Após selecionar a opção **Adicionar pipeline somente de produção**, a caixa de diálogo **Adicionar pipeline somente de produção** é aberta.
1. No campo **Nome do pipeline**, digite o nome desejado. As opções e funcionalidades restantes da caixa de diálogo funcionam da mesma forma que as opções encontradas na caixa de diálogo de criação de pipeline acoplado padrão.
1. No canto inferior direito da caixa de diálogo, clique em **Salvar**.

   ![Criação de um pipeline somente de produção](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Execução de pipelines somente de produção e somente de preparo {#running}

Os pipelines somente de produção e somente de preparo são executados quase da mesma forma que [todos os outros pipelines são executados](/help/using/managing-pipelines.md#running-pipelines). Consulte essa documentação para obter detalhes. No entanto, há dois novos recursos desses pipelines.

* Os pipelines somente de preparo e somente de produção oferecem um novo [modo de emergência](#emergency-mode) para ignorar o teste.
* A execução do pipeline somente de produção pode ser acionada diretamente dos detalhes de execução de um [pipeline somente de preparo](#stage-only-run).

### Modo de emergência {#emergency-mode}

Ao iniciar pipelines online somente de produção e de preparo, você será solicitado a confirmar o início e como ele é iniciado.

* **Modo Normal** é uma execução padrão e inclui etapas de teste de preparo.
* **Modo de emergência** ignora etapas de teste de estágio.

![Modo de emergência](/help/assets/configure-pipelines/emergency-mode.png)

### Pipelines somente de preparo {#stage-only-run}

Um pipeline somente de preparo é executado quase da mesma maneira que os pipelines acoplados padrão. No entanto, no final da execução, após as etapas de teste, um botão **Promover compilação** é exibido. Esse botão permite iniciar uma execução de pipeline somente de produção usando os artefatos que foram implantados no estágio na execução e implantá-los na produção.

![Execução de pipeline somente de preparo](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Clicar em **Promover compilação** solicita que você confirme a execução do pipeline somente de estágio relacionado normalmente ou no [modo de emergência](#emergency-mode).

Se não existir um pipeline somente de produção, você será solicitado a criar um.

### Pipelines somente de produção {#prod-only-run}

Para pipelines somente de produção, identifique os artefatos de origem que deseja implantar na produção. Esses detalhes são encontrados na etapa **Preparação de Artefato**. Você pode navegar até essas execuções para obter mais detalhes e logs.

![Detalhes do artefato](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
