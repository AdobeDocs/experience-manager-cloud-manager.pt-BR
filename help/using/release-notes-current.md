---
title: Notas da versão 2022.4.0
description: Estas são as notas de versão do Cloud Manager versão 2022.4.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 3d4eea13c0f2e9c4030bbfd3b7c5c25336548498
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---


# Notas de versão do Cloud Manager versão 2022.4.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] versão 2022.4.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2022.4.0 é 7 de abril de 2022. A próxima versão está prevista para 5 de maio de 2022.

## Novidades {#what-is-new}

* As melhorias na duração e na taxa de sucesso das etapas de criação do pipeline foram implementadas e serão implantadas de forma incremental para todos os clientes até o mês de abril.
* Agora é possível encontrar facilmente uma ramificação git digitando os primeiros caracteres do nome no campo de entrada no assistente adicionar e editar pipeline e selecionando entre as correspondências sugeridas.
* O **Pipelines** A página agora tem paginação para melhorar a usabilidade de programas com um grande número de pipelines.
   * 50 linhas por página serão exibidas na tabela.
* A versão do [Arquétipo de projeto AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) usado pelo Cloud Manager foi atualizado para a versão 36.
* O JDK do Oracle agora é o JDK padrão para o desenvolvimento e a operação de aplicativos AEM. O processo de build do Cloud Manager mudará automaticamente para o uso do JDK do Oracle, mesmo se uma opção alternativa estiver explicitamente selecionada na cadeia de ferramentas Maven.
   * Para saber mais sobre como alternar para o Oracle JDK, consulte [a documentação do Ambiente de build.](/help/using/build-environment-details.md#using-java-support)
   * Consulte [Perguntas frequentes sobre a política de suporte de Java para Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) para abordar perguntas comuns sobre essa alteração.
