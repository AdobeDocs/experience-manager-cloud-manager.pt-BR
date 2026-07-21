---
title: Fase de avaliação
seo-title: Evaluation Phase
description: Saiba como a fase de avaliação do Assistente de atualização do produto avalia a complexidade da atualização com o detector de padrões.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
TQID: https://experienceleague.adobe.com/dj-Wnq9FagNI3mzzVHcUH-sOufzb02D0juHqhtgpon0
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 1b146c2a01d3371ed2fe014a15a84ddee2cd9b6c
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 40%

---

# Fase de avaliação {#evaluation}

A primeira fase do Assistente de Atualização de Produto é a fase **[!UICONTROL Avaliação]**. Ele executa o detector de padrões no assistente para avaliar a complexidade da atualização. No final desta etapa, é possível exibir o relatório de avaliação.

O relatório verifica a prontidão da instância do autor para atualização, detectando padrões para o seguinte:

* Violações de regras em áreas afetadas ou substituídas pela atualização.
* Ele detecta recursos ou APIs do AEM 6.x que não são compatíveis com versões anteriores e podem falhar após a atualização.

Este relatório ajuda a estimar o esforço de desenvolvimento necessário para atualizar para o Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para saber mais sobre o detector de padrões, consulte [Avaliação da complexidade da atualização com o detector de padrões](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Executar o relatório de avaliação {#running}

O detector de padrões pode ser executado em qualquer ambiente. No entanto, para aumentar a taxa de detecção e evitar qualquer impacto no desempenho em instâncias críticas, o Cloud Manager a executa no ambiente de preparo da instância do autor.

**Para executar o relatório de avaliação:**

1. Inicie o assistente conforme descrito no documento [Assistente de atualização do produto](/help/product-update-wizard/overview.md).

1. Clique em **[!UICONTROL Executar avaliação]**.

   ![Executar avaliação](/help/assets/Run-Evaluation.png)

1. O assistente informa o status da ação. Nota **Em andamento** ou **Concluída**, conforme aplicável, enquanto o relatório de avaliação está sendo gerado.

1. Depois que o relatório for gerado, você pode clicar em **[!UICONTROL Baixar relatório]** para salvar uma cópia.

   ![Relatório criado](/help/assets/Evaluation-1.png)

O assistente de Atualização de Produto atual no Cloud Manager oferece suporte somente à fase **Avaliação**. As outras quatro fases, ou seja, **Correção**, **Execução**, **Validação** e **Conclusão**, serão disponibilizadas em breve.
