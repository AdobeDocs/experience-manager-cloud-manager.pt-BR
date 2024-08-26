---
title: Provisionamento de ambiente
description: Saiba como os seus ambientes são provisionados como parte do processo de integração do Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 36%

---


# Provisionamento de ambiente {#environments-provisioning}

Saiba como os seus ambientes são provisionados como parte do processo de integração do Cloud Manager.

## Provisionamento {#provisioning}

Durante o processo de integração, o Adobe provisiona automaticamente todos os ambientes de nuvem AEM que você comprou e os vincula ao seu programa no [!UICONTROL Cloud Manager]. Cada assinatura do Adobe Managed Services inclui ambientes de nuvem AEM. Normalmente, incluem pelo menos um ambiente de produção e um ambiente de preparo. Opcionalmente, eles também podem incluir um ou mais ambientes de desenvolvimento ou teste.

## Email de boas-vindas {#welcome-email}

Após a conclusão do processo de provisionamento do ambiente, o administrador do cliente designado recebe um email de boas-vindas com a confirmação de que recebeu acesso ao Adobe [!UICONTROL Experience Cloud]. O email de boas-vindas contém informações detalhadas sobre como começar a usar os serviços da [!UICONTROL Experience Cloud], ambientes da nuvem do [!UICONTROL AEM Managed Services] e o portal de autoatendimento do [!UICONTROL Cloud Manager]. Além disso, o email contém informações importantes, como as informações de contato do engenheiro de sucesso do cliente (CSE), onde buscar recursos de suporte, fóruns, perguntas frequentes e muito mais. Na lista de recursos fornecida no email, você também receberá detalhes sobre como acessar o [!UICONTROL Cloud Manager] nos seus ambientes de nuvem de AEM.

## Próximas etapas {#next-steps}

Depois de receber o email de boas-vindas, você estará pronto para fazer logon no [!UICONTROL Cloud Manager] como administrador do sistema, usando suas credenciais do Adobe IMS. Depois de fazer logon, é possível verificar se os ambientes de produção e não produção de nuvem do AEM estão disponíveis e se estão funcionando sem problemas.

O [!UICONTROL Cloud Manager] usa esses ambientes de nuvem AEM para executar o pipeline de CI/CD. Ele implanta o código de seu repositório Git no ambiente de preparo. Em seguida, ele implanta o código no ambiente de produção do AEM. Você também pode acessar os ambientes de nuvem do AEM diretamente do [!UICONTROL Cloud Manager] quando estiver pronto para começar a criar experiências digitais para suas propriedades da Web.
