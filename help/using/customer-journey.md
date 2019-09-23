---
title: Jornada do cliente
seo-title: Jornada do cliente do Adobe AEM Cloud Manager
description: Siga esta página para saber mais sobre sua jornada como cliente para começar a usar o Cloud Manager.
seo-description: Siga esta página para saber mais sobre sua jornada como cliente para começar a usar o Adobe AEM Cloud Manager.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introdução
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# Jornada do cliente {#customer-journey}

Como cliente, você pode ser novo no Adobe Experience Manager (AEM), usando atualmente o AEM 6.4, ou pode precisar atualizar para a versão AEM 6.4 para usar [!UICONTROL Cloud Manager]. Os seguintes cenários explicam sua jornada como um cliente novo ou existente para começar a usar [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] está disponível somente para clientes do Adobe Managed Services usando o AEM 6.4 ou superior.

## No embarque para [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Novo cliente AEM nos serviços gerenciados da Adobe**

   Como novo cliente, você será embarcado no serviço de nuvem gerenciado da Adobe como parte do processo de integração [!UICONTROL Cloud Manager] ao serviço de nuvem gerenciado.

   O URL para acesso [!UICONTROL Cloud Manager] será incluído no email de boas-vindas, juntamente com as instruções para fazer logon [!UICONTROL Experience Cloud]e usar o Adobe Admin Console para gerenciar seus usuários e suas respectivas permissões, para os usuários que precisam acessar [!UICONTROL Cloud Manager].

1. **Cliente AEM existente nos serviços gerenciados da Adobe**

   Como cliente existente, primeiro será necessário atualizar seus ambientes de produção e não-produção existentes para a versão AEM 6.4. Ao mesmo tempo, você executará a atualização e receberá o URL para acesso [!UICONTROL Cloud Manager]. Além disso, você precisará começar a usar o Adobe Admin Console para gerenciar seus usuários e suas respectivas permissões, para os usuários que precisam acessar [!UICONTROL Cloud Manager].

   Seu projeto AEM existente também precisará estar em conformidade com as práticas recomendadas, já que você começará a usar [!UICONTROL Cloud Manager] para implantar novas alterações de código em seus ambientes AEM.

   Para obter informações adicionais sobre os benefícios de atualizar para o AEM 6.4, consulte [Atualização para o AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Acessar [!UICONTROL Cloud Manager]{#accessing-cloud-manager}

Você obterá acesso aos ambientes AEM [!UICONTROL Cloud Manager] [!UICONTROL Experience Cloud] e AEM simplesmente fazendo logon na página de aterrissagem, usando suas credenciais do Adobe Identity Management e selecionando AEM na interface do alternador de soluções.

Após fazer logon [!UICONTROL Cloud Manager] pela primeira vez, você terá acesso aos seus ambientes AEM diretamente da [!UICONTROL Cloud Manager] interface do usuário. Nesse ponto, você estará pronto para explorar todas as possibilidades do [!UICONTROL Cloud Manager], uma vez que tiver sua primeira ramificação de código pronta para ser implantada em seus ambientes de estágio e produção.

Para explorar e começar a explorar [!UICONTROL Cloud Manager], consulte [Logon](first-time-login.md)pela primeira vez. Para obter informações adicionais sobre o AEM, consulte [Introdução ao AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). Além disso, consulte Recursos [do](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&mv=other) AEM para obter mais informações.

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Depois que você estiver conectado, [!UICONTROL Cloud Manager]a primeira coisa a fazer será configurar seu ambiente de repositório de códigos, sua equipe e suas funções. Especificamente, as associações de função são atribuídas adicionando o usuário a um [!UICONTROL Cloud Manager] perfil usando a interface do usuário do Admin Console.

Em seguida, é necessário configurar suas ramificações de código-fonte no Repositório **do** Git, definir suas metas em termos de KPIs de carga e desempenho e testar cenários para implantar com êxito seu código nos ambientes de estágio e de produção, uma vez que todas as verificações de qualidade tenham sido bem-sucedidas.

## Viagem de ponta a ponta {#end-to-end-journey}

O diagrama a seguir ilustra a jornada do cliente em um nível alto, ao usar o pipeline de [!UICONTROL Cloud Manager] CI/CD para implantar suas alterações de código nos ambientes de estágio e de produção.

![](assets/screen_shot_2018-05-15at124004pm.png)

