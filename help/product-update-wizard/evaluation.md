---
title: Fase de avaliação
seo-title: Evaluation Phase
description: Saiba como a fase de avaliação do Assistente de atualização do produto avalia a complexidade da atualização com o detector de padrões.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: ht
source-wordcount: '279'
ht-degree: 100%

---


# Fase de avaliação {#evaluation}

A primeira fase do Assistente de atualização do produto é a fase de **[!UICONTROL Avaliação]**, que avalia a complexidade da atualização com o detector de padrões diretamente no assistente. No final desta etapa, você terá acesso a um relatório de avaliação.

O relatório gerado permite verificar a elegibilidade para atualização da instância de criação, detectando padrões que:

* Quebram determinadas regras relacionadas às áreas afetadas ou substituídas pela atualização.

* Usam ou uma API ou um recurso do AEM 6.x sem retrocompatibilidade com a nova versão do AEM e que possa deixar de funcionar após a atualização.

O relatório atua como uma avaliação do esforço de desenvolvimento que está envolvido na atualização para o Adobe Experience Manager (AEM) 6.5.

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

A versão atual do Assistente de atualização do produto no Cloud Manager oferece suporte somente à fase de **Avaliação**. As outras quatro fases: **Correção**, **Execução**, **Validação** e **Conclusão** serão disponibilizadas em breve.
