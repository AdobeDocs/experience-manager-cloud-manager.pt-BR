---
title: Jornada do usuário
description: Saiba mais sobre os diferentes cenários de integração e introdução ao Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 21%

---


# Jornada de usuário {#user-journey}

Como usuário do AEM (Adobe Experience Manager), você provavelmente se encaixa em um dos seguintes cenários:

* Você é novo no AEM.
* No momento, você está usando o AEM 6.x.
* Você precisa atualizar para AEM 6.5 para usar o [!UICONTROL Cloud Manager].

Este documento descreve estes três cenários e explica a jornada de começar a usar o [!UICONTROL Cloud Manager].

>[!NOTE]
>
>O [!UICONTROL Cloud Manager] só está disponível para clientes do Adobe Managed Services (AMS) que usam o AEM 6.4 ou superior.

## Integração {#onboarding}

Dependendo se você é novo no AMS ou se já é cliente do AMS, o processo de integração é diferente.

### Novo no Adobe Managed Services {#new-to-ams}

Como novo cliente, você será integrado ao [!UICONTROL Cloud Manager] como parte do processo de integração ao Adobe Managed Services.

Como parte do processo de integração, você recebe um email de boas-vindas que inclui o seguinte:

* A URL para acessar o [!UICONTROL Cloud Manager].
* Instruções para fazer login no [!UICONTROL Experience Cloud].
* Instruções de uso do Admin Console para gerenciar usuários e suas respectivas permissões para que eles possam acessar o [!UICONTROL Cloud Manager] se necessário.

### Cliente atual do Adobe Managed Services {#existing-customer}

Como cliente do AMS, você deve primeiro atualizar seus ambientes de produção e não produção existentes para o AEM 6.4 ou superior.

Durante a atualização, você será integrado ao Cloud Manager e receberá a URL para acessar o [!UICONTROL Cloud Manager]. Além disso, para os usuários que precisam acessar o [!UICONTROL Cloud Manager], você deve começar a usar o Admin Console para gerenciá-los e suas respectivas permissões.

Seu projeto existente do AEM também precisa estar em conformidade com as práticas recomendadas, pois você começa a usar o [!UICONTROL Cloud Manager] para implantar novas alterações de código em seus ambientes do AEM.

Para obter informações adicionais sobre os benefícios de atualizar para AEM 6.5, consulte [Atualização para AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Acessar o [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Faça logon na página de aterrissagem [!UICONTROL Experience Cloud] usando suas credenciais de Identity Management do Adobe. A partir daí, selecione AEM no alternador de soluções para acessar o [!UICONTROL Cloud Manager] e seus ambientes AEM.

Depois de fazer logon no [!UICONTROL Cloud Manager] pela primeira vez, você terá acesso aos ambientes AEM diretamente da interface do usuário do [!UICONTROL Cloud Manager]. Nesse ponto, você está pronto para explorar todas as possibilidades do [!UICONTROL Cloud Manager] e preparar sua primeira ramificação de código a ser implantada nos seus ambientes de preparo e produção.

Para começar a usar o [!UICONTROL Cloud Manager], consulte [Primeiro Logon](/help/getting-started/first-time-login.md).

Para obter informações adicionais sobre o AEM, consulte [Implantação e manutenção](https://experienceleague.adobe.com/br/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Introdução ao [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Depois de fazer logon no [!UICONTROL Cloud Manager], você pode começar a usar o projeto AEM fazendo o seguinte:

1. Configurar o ambiente do repositório de código.
1. Configurar a equipe e as funções. As associações de função são atribuídas adicionando o usuário a um perfil do [!UICONTROL Cloud Manager] usando o Admin Console.
1. Configure as ramificações do código-fonte no repositório Git.
1. Defina suas metas em termos de KPIs de carga e desempenho (Indicadores-chave de desempenho).
1. Defina cenários de teste para implantar seu código com êxito nos ambientes de preparo e produção depois que todas as verificações de qualidade forem aprovadas.

## Jornada de ponta a ponta {#end-to-end-journey}

Este diagrama ilustra a jornada do cliente em alto nível ao usar o pipeline CI/CD [!UICONTROL Cloud Manager] para implantar suas alterações de código em seus ambientes de preparo e produção.

![Jornada de ponta a ponta](/help/assets/screen_shot_2018-05-15at124004pm.png)
