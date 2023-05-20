---
title: Jornada do usuário
description: Este documento descreve os diferentes cenários de integração e explica a introdução à jornada com o Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 100%

---


# Jornada do usuário {#user-journey}

Como usuário do Adobe Experience Manager, você pode:

* Ser novo no AEM.
* Estar usando atualmente o AEM 6.x.
* É necessário atualizar para a versão AEM 6.5 para usar o [!UICONTROL Cloud Manager].

Este documento descreve esses cenários e explica a jornada de introdução ao [!UICONTROL Cloud Manager].

>[!NOTE]
>
>O [!UICONTROL Cloud Manager] só está disponível para clientes do Adobe Managed Services (AMS) que usam o AEM 6.4 ou superior.

## Integração {#onboarding}

Dependendo se você é novo no AMS ou se já é cliente do AMS, o processo de integração é diferente.

### Novo no Adobe Managed Services {#new-to-ams}

Como novo cliente, você será integrado ao [!UICONTROL Cloud Manager] como parte do processo de integração ao Adobe Managed Services.

Como parte do processo de integração, você receberá um email de boas-vindas que inclui:

* O URL para acessar o [!UICONTROL Cloud Manager]
* Instruções para fazer logon na [!UICONTROL Experience Cloud]
* Instruções de uso do Admin Console para gerenciar usuários e suas respectivas permissões para que eles possam acessar o [!UICONTROL Cloud Manager] se necessário.

### Cliente existente do Adobe Managed Services {#existing-customer}

Como cliente do AMS, primeiro será necessário atualizar seus ambientes de produção e não produção existentes para o AEM 6.4 ou superior.

À medida que você executa a atualização, você será integrado ao Cloud Manager e receberá a URL para acessar o [!UICONTROL Cloud Manager]. Além disso, para os usuários que precisam acessar o [!UICONTROL Cloud Manager], será necessário começar a usar o Admin Console para gerenciá-los e suas respectivas permissões.

Seu projeto do AEM existente também precisará estar em conformidade com as melhores práticas recomendadas, pois você começará a usar o [!UICONTROL Cloud Manager] para implantar novas alterações de código em seus ambientes do AEM.

Para obter informações adicionais sobre os benefícios de atualizar para o AEM 6.5, consulte o documento [Atualização para o AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=pt-BR)

## Acessar o [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Você terá acesso ao [!UICONTROL Cloud Manager] e seus ambientes do AEM simplesmente fazendo logon na página de destino da [!UICONTROL Experience Cloud] usando suas credenciais do Adobe Identity Management e selecionando o AEM na interface do alternador de soluções.

Depois de fazer logon no [!UICONTROL Cloud Manager] pela primeira vez, você terá acesso aos ambientes do AEM diretamente da interface do [!UICONTROL Cloud Manager]. Nesse ponto, você está pronto para explorar todas as possibilidades do [!UICONTROL Cloud Manager] e preparar sua primeira ramificação de código a ser implantada nos seus ambientes de preparo e produção.

Para começar a usar o [!UICONTROL Cloud Manager], consulte o documento [Fazer logon pela primeira vez](/help/getting-started/first-time-login.md).

Para obter informações adicionais sobre o AEM, consulte o documento [Implantação e manutenção.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=pt-BR)

## Introdução ao [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Depois de fazer logon no [!UICONTROL Cloud Manager], você pode começar a usar o projeto do AEM por:

1. Configurar o ambiente do repositório de código.
1. Configurar a equipe e as funções.
   * As associações de função são atribuídas adicionando o usuário a um perfil do [!UICONTROL Cloud Manager] usando o Admin Console.
1. Configurar as ramificações do código-fonte no repositório Git.
1. Definir suas metas em termos de KPIs de carga e desempenho.
1. Definir cenários de teste para implantar com sucesso seu código em seus ambientes de estágio e produção depois que todas as verificações de qualidade forem bem-sucedidas.

## Jornada de ponta a ponta {#end-to-end-journey}

Este diagrama ilustra a jornada do cliente em alto nível ao usar o pipeline CI/CD do [!UICONTROL Cloud Manager] para implantar suas alterações de código em seus ambientes de preparo e produção.

![Jornada de ponta a ponta](/help/assets/screen_shot_2018-05-15at124004pm.png)
