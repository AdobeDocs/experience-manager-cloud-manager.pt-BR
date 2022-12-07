---
title: Fase de avaliação
seo-title: Evaluation Phase
description: Saiba como a fase de avaliação do Assistente de atualização de produto avalia a complexidade da atualização com o detector de padrão.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: ce2145da3b9e605e8a41bac28df520f14e255557
workflow-type: ht
source-wordcount: '296'
ht-degree: 100%

---


# Fase de avaliação {#evaluation}

A primeira fase do Assistente de atualização de produto é a fase **[!UICONTROL Avaliação]**, que avalia a complexidade da atualização com o detector de padrão diretamente no assistente. No final desta etapa, você terá acesso a um relatório de avaliação.

O relatório gerado permite verificar a qualificação de atualização da instância do autor, detectando padrões que:

* Violam determinadas regras em áreas que serão afetadas ou substituídas pela atualização.

* Usam um recurso do AEM 6.x ou uma API que não seja compatível com a nova versão do AEM e possa ser interrompida após a atualização.

O relatório atua como uma avaliação do esforço de desenvolvimento que está envolvido na atualização para o Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para saber mais sobre o detector de padrões, consulte o documento [Avaliação da complexidade da atualização com o Detector de padrões.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=pt-BR)

## Execução da avaliação {#running}

O detector de padrões pode ser executado em qualquer ambiente. No entanto, para aumentar a taxa de detecção e evitar qualquer lentidão em instâncias críticas para os negócios, o Cloud Manager o executará no ambiente de preparo da instância do autor.

Siga estas etapas para gerar o relatório de avaliação.

1. Inicie o assistente conforme descrito no documento [Assistente de atualização do produto.](/help/product-update-wizard/overview.md)

1. Clique em **[!UICONTROL Executar avaliação]**.

   ![Executar avaliação](/help/assets/Run-Evaluation.png)

1. O assistente informa o status da ação. Você notará os status **Em andamento** ou **Concluído** conforme aplicável quando o relatório de avaliação for gerado.

1. Depois que o relatório for gerado, você pode clicar em **[!UICONTROL Baixar relatório]** para salvar uma cópia.

   ![Relatório criado](/help/assets/Evaluation-1.png)

A versão atual do assistente de Atualização de produto no Cloud Manager oferece suporte somente à fase de **Avaliação**. As outras quatro fases: **Correção**, **Execução**, **Validação** e **Conclusão** serão disponibilizadas em breve.
