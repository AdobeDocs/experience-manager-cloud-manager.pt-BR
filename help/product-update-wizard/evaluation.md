---
title: Fase de avaliação
seo-title: Evaluation Phase
description: Saiba como a fase de avaliação do Assistente de atualização do produto avalia a complexidade da atualização com o detector de padrões.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 57%

---


# Fase de avaliação {#evaluation}

A primeira fase do Assistente de Atualização de Produto é a fase **[!UICONTROL Avaliação]**. Ele executa o detector de padrões no assistente para avaliar a complexidade da atualização. No final desta etapa, é possível exibir o relatório de avaliação.

O relatório verifica a prontidão da instância do autor para atualização, detectando padrões para o seguinte:

* Violações de regras em áreas afetadas ou substituídas pela atualização.
* Ele usa recursos do AEM 6.x ou APIs que não são compatíveis com versões anteriores e podem ser interrompidas após a atualização.

Este relatório ajuda a estimar o esforço de desenvolvimento necessário para atualizar para o Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para saber mais sobre o detector de padrões, consulte [Avaliação da complexidade da atualização com o detector de padrões](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Executar o relatório de avaliação {#running}

O detector de padrões pode ser executado em qualquer ambiente. No entanto, para aumentar a taxa de detecção e evitar qualquer lentidão em instâncias críticas para os negócios, o Cloud Manager o executa no ambiente de preparo da instância de criação.

**Para executar o relatório de avaliação:**

1. Inicie o assistente conforme descrito no documento [Assistente de atualização do produto](/help/product-update-wizard/overview.md).

1. Clique em **[!UICONTROL Executar avaliação]**.

   ![Executar avaliação](/help/assets/Run-Evaluation.png)

1. O assistente informa o status da ação. Você notará os status **Em andamento** ou **Concluído**, conforme for o caso, quando o relatório de avaliação estiver sendo gerado.

1. Depois que o relatório for gerado, você pode clicar em **[!UICONTROL Baixar relatório]** para salvar uma cópia.

   ![Relatório criado](/help/assets/Evaluation-1.png)

O assistente de Atualização de Produto atual no Cloud Manager oferece suporte somente à fase **Avaliação**. As outras quatro fases: **Correção**, **Execução**, **Validação** e **Conclusão** serão disponibilizadas em breve.
