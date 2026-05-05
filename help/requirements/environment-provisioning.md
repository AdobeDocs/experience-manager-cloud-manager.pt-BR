---
title: Provisionamento de ambiente
description: Saiba como os seus ambientes são provisionados como parte do processo de integração do Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
TQID: https://experienceleague.adobe.com/xLjZdRZeCiqF0KxHQ1nBI4IBBsh4BDTqETv79lrypR0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 299
ht-degree: 100%

---

# Provisionamento de ambiente {#environments-provisioning}

Saiba como os seus ambientes são provisionados como parte do processo de integração do Cloud Manager.

## Provisionamento {#provisioning}

Durante o processo de integração, o Adobe provisiona automaticamente todos os ambientes de nuvem do AEM que você comprou e os vincula ao seu programa no [!UICONTROL Cloud Manager]. Toda assinatura do Adobe Managed Services inclui ambientes de nuvem do AEM. Normalmente, eles incluem pelo menos um ambiente de produção e um ambiente de preparo. Outra opção é que eles incluam um ou mais ambientes de desenvolvimento ou teste.

## Email de boas-vindas {#welcome-email}

Após a conclusão do processo de provisionamento do ambiente, o administrador do cliente designado recebe um email de boas-vindas com a confirmação de que o acesso à Adobe [!UICONTROL Experience Cloud] foi concedido. O email de boas-vindas contém informações detalhadas sobre como começar a usar os serviços da [!UICONTROL Experience Cloud], ambientes da nuvem do [!UICONTROL AEM Managed Services] e o portal de autoatendimento do [!UICONTROL Cloud Manager]. Além disso, o email contém informações importantes, como as informações de contato do Engenheiro de sucesso do cliente (CSE), onde buscar recursos de suporte, fóruns, perguntas frequentes e muito mais. Na lista de recursos fornecida no email, você também recebe detalhes sobre como acessar o [!UICONTROL Cloud Manager] nos seus ambientes da nuvem do AEM.

## Próximas etapas {#next-steps}

Depois de receber o email de boas-vindas, você estará pronto para fazer logon no [!UICONTROL Cloud Manager] como administrador do sistema, usando suas credenciais do Adobe IMS. Depois de fazer logon, é possível verificar que os ambientes de produção e não produção de nuvem do AEM estão disponíveis e funcionando sem problemas.

O [!UICONTROL Cloud Manager] usa esses ambientes de nuvem do AEM para executar o pipeline de CI/CD. Ele implanta o código do seu repositório Git no ambiente de preparo. Depois, ele implanta o código no ambiente de produção do AEM. Você também pode acessar os ambientes da nuvem do AEM diretamente do [!UICONTROL Cloud Manager] quando estiver pronto para começar a criar experiências digitais para suas propriedades da Web.
