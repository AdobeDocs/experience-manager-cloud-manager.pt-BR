---
title: Provisionamento de ambiente
description: Saiba como os seus ambientes são provisionados como parte do processo de integração do Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: ht
source-wordcount: '297'
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
