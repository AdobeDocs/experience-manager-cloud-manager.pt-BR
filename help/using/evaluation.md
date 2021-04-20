---
title: Avaliação
seo-title: Avaliação
description: 'Esta página serve como ponto de partida para aprender a fase de Avaliação no Assistente de atualização do produto. '
seo-description: Esta página serve como ponto de partida para aprender a fase de Avaliação no Assistente de atualização do produto.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
feature: Getting Started
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---


# Fase de avaliação {#evaluation}

A primeira fase do assistente de Atualização de produto é a fase **[!UICONTROL Evaluation]**.
Aqui você pode avaliar a complexidade da atualização com o detector de padrão acessível diretamente do assistente. No final desta etapa, você terá acesso ao relatório de avaliação.

O relatório gerado permite verificar a instância do autor para atualização detectando padrões que:

* Violar certas regras e são feitas em áreas que serão afetadas ou substituídas pela atualização.

* Use um recurso AEM 6.x ou uma API que não seja compatível com versões anteriores no novo AEM e possa ser interrompida após a atualização.

Isso serve como uma avaliação do esforço de desenvolvimento envolvido na atualização para o Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para saber mais sobre o detector de padrões, consulte [Avaliação da complexidade da atualização com o Detector de padrões](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Executando o Avaliador {#running-evaluator}

Siga as etapas abaixo para gerar o relatório de avaliação:

1. Clique em **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >
   >O detector de padrões pode ser executado em qualquer ambiente. No entanto, para aumentar a taxa de detecção e evitar qualquer lentidão em instâncias críticas para os negócios, o Cloud Manager a executará no ambiente de preparo na instância do autor.

   ![](assets/Run-Evaluation.png)

1. O assistente informa você sobre o status da ação. Você notará **In progress** ou **completed** conforme aplicável quando o relatório de avaliação está sendo gerado.

   Depois que o relatório é gerado, você pode clicar em **[!UICONTROL Download report]** para salvar uma cópia.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >A versão atual do assistente de Atualização de produto no Cloud Manager é compatível somente com a fase de **Avaliação**. As outras quatro fases, nomeadamente **Remediação**, **Execução**, **Validação** e **Conclusão**, estão em breve.
