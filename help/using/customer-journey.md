---
title: Jornada do cliente
seo-title: Jornada do cliente do Adobe AEM Cloud Manager
description: Siga esta página para saber mais sobre seu jornada as a customer e começar a usar o Cloud Manager.
seo-description: Siga esta página para saber mais sobre o jornada como cliente e começar a usar o Adobe AEM Cloud Manager.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
feature: Introdução
level: Iniciante
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 2%

---


# Jornada do cliente {#customer-journey}

Como cliente, você pode ser novo no Adobe Experience Manager (AEM), usando atualmente o AEM 6.4, ou pode precisar atualizar para a versão AEM 6.4 para usar [!UICONTROL Cloud Manager]. Os cenários a seguir explicam sua jornada como um cliente novo ou existente para começar a usar [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] O só está disponível para clientes do Adobe Managed Services que usam o AEM 6.4 ou superior.

## Integração a [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Novo cliente AEM no Adobe Managed Services**

   Como novo cliente, você será integrado ao [!UICONTROL Cloud Manager] como parte do processo de integração aos Adobe Managed Services.

   O URL para acessar [!UICONTROL Cloud Manager] será incluído no email de boas-vindas, juntamente com as instruções para fazer logon em [!UICONTROL Experience Cloud], e usar o Adobe Admin Console para gerenciar seus usuários e suas respectivas permissões para os usuários que precisam acessar [!UICONTROL Cloud Manager].

1. **Cliente AEM existente no Adobe Managed Services**

   Como cliente existente, primeiro será necessário atualizar seus ambientes de produção e de não produção existentes para a versão AEM 6.4. Ao mesmo tempo, durante a atualização, você será integrado e terá o URL para acessar [!UICONTROL Cloud Manager]. Além disso, será necessário começar a usar o Adobe Admin Console para gerenciar seus usuários e suas respectivas permissões para esses usuários que precisam acessar [!UICONTROL Cloud Manager].

   Seu projeto de AEM existente também precisará estar em conformidade com as práticas recomendadas, pois você começará a usar [!UICONTROL Cloud Manager] para implantar novas alterações de código nos ambientes de AEM.

   Para obter informações adicionais sobre os benefícios da atualização para o AEM 6.4, consulte [Atualização para AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Acessar [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Você obterá acesso ao [!UICONTROL Cloud Manager] e aos ambientes de AEM simplesmente fazendo logon na página de aterrissagem [!UICONTROL Experience Cloud], usando suas credenciais do Adobe Identity Management e selecionando AEM na interface do alternador de soluções.

Depois de fazer logon [!UICONTROL Cloud Manager] pela primeira vez, você terá acesso aos ambientes de AEM diretamente da interface do usuário [!UICONTROL Cloud Manager]. Neste ponto, você está pronto para explorar todas as possibilidades do [!UICONTROL Cloud Manager], uma vez que sua primeira ramificação de código esteja pronta para ser implantada em seus ambientes de preparo e produção.

Para explorar e começar a usar [!UICONTROL Cloud Manager], consulte [Primeiro logon](first-time-login.md). Para obter informações adicionais sobre AEM, consulte [Introdução ao AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). Além disso, consulte [Recursos AEM](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other) para obter mais informações.

## Introdução a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Depois de fazer logon em [!UICONTROL Cloud Manager], a primeira coisa a fazer é configurar o ambiente do repositório de códigos, em seguida, a equipe e as funções. Especificamente, as associações de função são atribuídas adicionando o usuário a um perfil [!UICONTROL Cloud Manager] usando a interface do usuário do Admin Console.

Em seguida, é necessário configurar as ramificações do código-fonte no **Repositório Git**, definir suas metas em termos de KPIs de carga e desempenho e testar os cenários para implantar o código com êxito nos ambientes de estágio e produção depois que todas as verificações de qualidade tiverem sido bem-sucedidas.

## Jornada End to End {#end-to-end-journey}

O diagrama a seguir ilustra a jornada do cliente em um alto nível, ao usar o pipeline de CI/CD [!UICONTROL Cloud Manager] para implantar suas alterações de código nos ambientes de preparo e produção.

![](assets/screen_shot_2018-05-15at124004pm.png)

