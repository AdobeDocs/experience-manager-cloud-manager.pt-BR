---
title: Avaliação
seo-title: Avaliação
description: 'Esta página serve como um ponto de partida para a fase de avaliação no Assistente de atualização do produto. '
seo-description: Esta página serve como um ponto de partida para a fase de avaliação no Assistente de atualização do produto.
uuid: 62 d 68 e 79-c 2 ba -4 d 8 b-ba 7 d -33709014 d 5 b 6
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc 91 a 5-be 9 e -4684-8146-d 88 f 4013 d 4 d 1
translation-type: tm+mt
source-git-commit: 2fda16bb4826171c993ec07c7ff3e38d1675b9f5

---


# Evaluation Phase {#evaluation}

Once you click **[!UICONTROL Start Update]**, the first phase in Product Update Wizard is the Evaluation phase. Nessa fase, você pode avaliar a complexidade da atualização com o padrão detectado diretamente para você do assistente. No final desta etapa, você terá acesso ao relatório de avaliação.

O relatório gerado permite verificar a instância do Autor para atualizá-la, detectando padrões que:

* Violar determinadas regras e são feitas em áreas que serão afetadas ou substituídas pela atualização.

* Use um recurso AEM 6. x ou uma API que não seja compatível com o novo AEM e que possa ser break após a atualização.


Isso serve como uma avaliação do esforço de desenvolvimento envolvido na atualização para o Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

Siga as etapas abaixo para executar o avaliador:

1. Select **[!UICONTROL Run Evaluation]** to run the pattern detector. O detector padrão pode ser executado em qualquer ambiente. No entanto, para aumentar a taxa de detecção e evitar qualquer lentidão em casos críticos de negócios, o Cloud Manager executará o procedimento no ambiente de preparo temporário na instância do autor.

![](assets/Run-Evaluation.png)

1. O assistente informa o status da sua ação. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

Once the report is generated, you can select [!UICONTROL Download] to save a copy of the evaluation report.

![](assets/Evaluation-1.png)

>[!NOTE]
>The other four phases succeeding **Evaluation** namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon and are not available in the current release.
