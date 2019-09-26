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
source-git-commit: 9e33b90818c686f0b7aacaf0955c3f2eba05488f

---


# Evaluation Phase {#evaluation}

The first phase in the Product Update wizard is **[!UICONTROL Evaluation]** phase.
Here you can assess the upgrade complexity with the pattern detector accessible to you directly from the wizard. At the end of this step, you will have access to the evaluation report.

The generated report allows you to check the Author instance for upgradability by detecting patterns that:

* Violate certain rules and are done in areas that will be affected or overwritten by the upgrade.

* Use an AEM 6.x feature or an API that is not backwards compatible on the new AEM and can potentially break after upgrade.

This serves as an assessment of the development effort that is involved in upgrading to Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>To learn more about pattern detector, refer to Assessing the Upgrade Complexity with the Pattern Detector[](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Executar o Avaliador {#running-evaluator}

Siga as etapas abaixo para gerar o relatório de avaliação:

1. Clique em **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >O detector de padrões pode funcionar em qualquer ambiente. No entanto, para aumentar a taxa de detecção e evitar qualquer lentidão em instâncias críticas para os negócios, o Cloud Manager a executará no ambiente de preparo na instância do autor.

   ![](assets/Run-Evaluation.png)

1. O assistente informa o status de sua ação. Você notará **Em andamento** ou **concluído** , conforme aplicável, quando o relatório de avaliação estiver sendo gerado.

   Depois que o relatório é gerado, você pode clicar em **[!UICONTROL Download report]** para salvar uma cópia.

   ![](assets/Evaluation-1.png)


>[!NOTE]
>A versão atual do assistente de Atualização de produto no Cloud Manager é compatível somente com a fase de **avaliação** . As outras quatro fases, **Remediação**, **Execução**, **Validação** e **Conclusão** , estarão em breve.
