---
title: Fase de avaliação
seo-title: Evaluation Phase
description: Saiba como a fase de avaliação do assistente de Atualização de produto avalia a complexidade da atualização com o detector de padrão.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 17%

---


# Fase de avaliação {#evaluation}

A primeira fase do assistente de Atualização de Produto é a fase **[!UICONTROL Avaliação]**, que avalia a complexidade da atualização com o detector de padrão diretamente no assistente. No final desta etapa, você pode acessar o relatório de avaliação.

O relatório gerado permite verificar a qualificação de atualização da instância do autor, detectando os seguintes padrões que:

* Quebrar determinadas regras relacionadas às áreas afetadas ou substituídas pela atualização.

* Usar um recurso AEM 6.x ou uma API que não seja compatível com a nova versão do AEM e possa ser interrompida após uma atualização.

O relatório atua como uma avaliação do esforço de desenvolvimento que está envolvido na atualização para o Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para saber mais sobre o detector de padrões, consulte [Avaliação da Complexidade da Atualização com o Detector de Padrões](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Executar o relatório de avaliação {#running}

O detector de padrões pode ser executado em qualquer ambiente. No entanto, para aumentar a taxa de detecção e evitar qualquer lentidão em instâncias críticas para os negócios, o Cloud Manager o executa no ambiente de preparo da instância do autor.

**Para executar o relatório de avaliação:**

1. Inicie o assistente conforme descrito no documento [Assistente de Atualização de Produto](/help/product-update-wizard/overview.md).

1. Clique em **[!UICONTROL Executar Avaliação]**.

   ![Executar avaliação](/help/assets/Run-Evaluation.png)

1. O assistente informa o status da ação. Aviso **Em andamento** ou **concluído**, conforme aplicável, quando o relatório de avaliação estiver sendo gerado.

1. Depois que o relatório for gerado, você pode clicar em **[!UICONTROL Baixar relatório]** para salvar uma cópia.

   ![Relatório criado](/help/assets/Evaluation-1.png)

A versão atual do assistente de Atualização de Produto no Cloud Manager dá suporte somente à fase **Avaliação**. As outras quatro fases: **Correção**, **Execução**, **Validação** e **Conclusão** serão disponibilizadas em breve.
