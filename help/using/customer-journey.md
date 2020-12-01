---
title: Jornada do cliente
seo-title: Jornada do cliente do Adobe AEM Cloud Manager
description: Siga esta página para saber mais sobre sua jornada como cliente para começar a usar o Cloud Manager.
seo-description: Siga esta página para saber mais sobre sua jornada como cliente para começar a usar o Adobe AEM Cloud Manager.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# Jornada do cliente {#customer-journey}

Como cliente, você pode ser novo na Adobe Experience Manager (AEM), usando atualmente a AEM 6.4, ou pode precisar atualizar para a versão AEM 6.4 para usar [!UICONTROL Cloud Manager]. Os seguintes cenários explicam sua jornada como um cliente novo ou existente para começar a usar [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] só está disponível para clientes do Adobe Managed Services usando o AEM 6.4 ou superior.

## No embarque para [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Novo cliente AEM nos serviços gerenciados da Adobe**

   Como um novo cliente, você será embarcado para [!UICONTROL Cloud Manager] como parte do processo de integração dos Serviços gerenciados da Adobe.

   O URL para acessar [!UICONTROL Cloud Manager] será incluído no email de boas-vindas, juntamente com as instruções para fazer logon em [!UICONTROL Experience Cloud], e usará o Adobe Admin Console para gerenciar seus usuários e suas respectivas permissões, para os usuários que precisam acessar [!UICONTROL Cloud Manager].

1. **Cliente AEM existente nos serviços gerenciados da Adobe**

   Como um cliente existente, primeiro você precisará atualizar seus ambientes de produção e não-produção existentes para a versão AEM 6.4. Ao mesmo tempo, você executará a atualização, e receberá o URL para acessar [!UICONTROL Cloud Manager]. Além disso, será necessário start usando o Adobe Admin Console para gerenciar seus usuários e suas respectivas permissões, para os usuários que precisam acessar [!UICONTROL Cloud Manager].

   Seu projeto de AEM existente também precisará estar em conformidade com as práticas recomendadas, pois você será start usando [!UICONTROL Cloud Manager] para implantar novas alterações de código nos ambientes de AEM.

   Para obter informações adicionais sobre os benefícios da atualização para o AEM 6.4, consulte [Atualização para AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Acessar [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Você obterá acesso a [!UICONTROL Cloud Manager] e seus ambientes AEM simplesmente fazendo logon na landing page [!UICONTROL Experience Cloud], usando suas credenciais do Adobe Identity Management e selecionando AEM na interface do alternador de soluções.

Depois de fazer logon [!UICONTROL Cloud Manager] pela primeira vez, você terá acesso aos ambientes AEM diretamente da interface do usuário [!UICONTROL Cloud Manager]. Neste ponto, você está pronto para explorar todas as possibilidades de [!UICONTROL Cloud Manager], uma vez que tenha sua primeira ramificação de código pronta para ser implantada em seus ambientes de estágio e produção.

Para explorar e começar a usar [!UICONTROL Cloud Manager], consulte [Início de sessão pela primeira vez](first-time-login.md). Para obter informações adicionais sobre AEM, consulte [Introdução ao AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). Além disso, consulte [Recursos AEM](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other) para obter mais informações.

## Introdução a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Depois que você estiver conectado a [!UICONTROL Cloud Manager], a primeira coisa a fazer será configurar seu ambiente de repositório de código, sua equipe e suas funções. Especificamente, as associações de função são atribuídas adicionando o usuário a um perfil [!UICONTROL Cloud Manager] usando a interface do usuário Admin Console.

Em seguida, é necessário configurar as ramificações do código-fonte no **Repositório Git**, definir suas metas em termos de KPIs de carga e desempenho e testar cenários para implantar com êxito seu código em seus ambientes de estágio e produção depois que todas as verificações de qualidade forem bem-sucedidas.

## Viagem de ponta a ponta {#end-to-end-journey}

O diagrama a seguir ilustra a jornada do cliente em um nível alto, ao usar o pipeline [!UICONTROL Cloud Manager] CI/CD para implantar suas alterações de código nos ambientes de estágio e produção.

![](assets/screen_shot_2018-05-15at124004pm.png)

