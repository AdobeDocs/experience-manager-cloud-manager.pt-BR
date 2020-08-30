---
title: Avaliação
seo-title: Avaliação
description: 'Esta página serve como ponto de partida para aprender a fase de Avaliação no Assistente de Atualização de Produto. '
seo-description: Esta página serve como ponto de partida para aprender a fase de Avaliação no Assistente de Atualização de Produto.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---


# Fase de avaliação {#evaluation}

A primeira fase do assistente de Atualização de produto é a **[!UICONTROL Evaluation]** fase.
Aqui você pode avaliar a complexidade da atualização com o detector de padrões acessível diretamente do assistente. No final desta etapa, você terá acesso ao relatório de avaliação.

O relatório gerado permite que você verifique a instância do autor para atualização detectando padrões que:

* Violar certas regras e são feitas em áreas que serão afetadas ou substituídas pela atualização.

* Use um recurso AEM 6.x ou uma API que não seja compatível com versões anteriores no novo AEM e que possa ser interrompida após a atualização.

Isto serve como uma avaliação do esforço de desenvolvimento que está envolvido na atualização para a Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para saber mais sobre o detector de padrões, consulte [Avaliação da complexidade de atualização com o Detector de padrões](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Executando o Avaliador {#running-evaluator}

Siga as etapas abaixo para gerar o relatório de avaliação:

1. Clique em **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >O detector de padrões pode funcionar em qualquer ambiente. No entanto, para aumentar a taxa de detecção e evitar qualquer lentidão em instâncias críticas para os negócios, o Cloud Manager a executará em ambientes de preparo na instância do autor.

   ![](assets/Run-Evaluation.png)

1. O assistente informa o status de sua ação. Você notará **Em andamento** ou **concluído** , conforme o caso, quando o relatório de avaliação estiver sendo gerado.

   Depois que o relatório é gerado, você pode clicar em **[!UICONTROL Download report]** para salvar uma cópia.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >A versão atual do assistente de Atualização de produto no Cloud Manager é compatível somente com a fase de **avaliação** . As outras quatro fases, **Remediação**, **Execução**, **Validação** e **Conclusão** , estarão em breve.
