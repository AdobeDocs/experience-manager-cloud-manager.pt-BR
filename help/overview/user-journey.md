---
title: Jornada do usuário
description: Este documento descreve os diferentes cenários de integração e explica a introdução ao jornada com o Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---


# Jornada do usuário {#user-journey}

Como usuário do Adobe Experience Manager, você pode:

* Seja novo em AEM.
* Esteja usando atualmente o AEM 6.x.
* Precisa atualizar para a versão AEM 6.5 para usar [!UICONTROL Cloud Manager].

Este documento descreve esses cenários e explica sua jornada de começar a usar [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] O só está disponível para clientes do Adobe Managed Services (AMS) usando o AEM 6.4 ou superior.

## Integração {#onboarding}

O processo de integração é diferente, dependendo se você é novo no AMS ou se é um cliente AMS existente.

### Novo no Adobe Managed Services {#new-to-ams}

Como novo cliente, você estará integrado ao [!UICONTROL Cloud Manager] como parte do processo de integração ao Adobe Managed Services.

Como parte do processo de integração, você receberá um email de boas-vindas que inclui:

* O URL para acessar [!UICONTROL Cloud Manager]
* Instruções para fazer logon no [!UICONTROL Experience Cloud]
* Instruções para usar o Admin Console para gerenciar usuários e suas respectivas permissões para que possam acessar o [!UICONTROL Cloud Manager] se necessário.

### Cliente do Adobe Managed Services existente {#existing-customer}

Como cliente do AMS, primeiro será necessário atualizar seus ambientes de produção e não de produção existentes para o AEM 6.4 ou superior.

À medida que você executa a atualização, você será integrado ao Cloud Manager e receberá o URL para acessar o [!UICONTROL Cloud Manager]. Além disso, para os usuários que precisam acessar o [!UICONTROL Cloud Manager], será necessário começar a usar o Admin Console para gerenciá-los e suas respectivas permissões.

Seu projeto de AEM existente também precisará estar em conformidade com as práticas recomendadas, pois você começará a usar [!UICONTROL Cloud Manager] para implantar novas alterações de código em seus ambientes de AEM.

Para obter informações adicionais sobre os benefícios de atualizar para o AEM 6.5, consulte o documento [Atualização para o AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html)

## Acesso ao [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Você terá acesso ao [!UICONTROL Cloud Manager] e seus ambientes de AEM simplesmente fazendo logon na [!UICONTROL Experience Cloud] página de aterrissagem usando suas credenciais do Adobe Identity Management e selecionando AEM na interface do alternador de soluções.

Depois de fazer logon [!UICONTROL Cloud Manager] pela primeira vez, você terá acesso aos ambientes de AEM diretamente do [!UICONTROL Cloud Manager] IU. Nesse ponto, você está pronto para explorar todas as possibilidades de [!UICONTROL Cloud Manager] e prepare sua primeira ramificação de código a ser implantada nos ambientes de preparo e produção.

Para começar a [!UICONTROL Cloud Manager], consulte o documento [Primeiro logon](/help/getting-started/first-time-login.md).

Para obter informações adicionais sobre AEM, consulte o documento [Implantação e manutenção.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html)

## Introdução ao [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Depois de fazer logon no [!UICONTROL Cloud Manager] você pode começar a usar o projeto do AEM ao:

1. Configurar o ambiente do repositório de código.
1. Configuração da equipe e funções.
   * As associações de função são atribuídas adicionando o usuário a um [!UICONTROL Cloud Manager] perfil usando o Admin Console.
1. Configurar as ramificações do código-fonte no repositório Git.
1. Definir suas metas em termos de KPIs de carga e desempenho.
1. Definir cenários de teste para implantar com sucesso seu código em seus ambientes de estágio e produção depois que todas as verificações de qualidade forem bem-sucedidas.

## Jornada de ponta a ponta {#end-to-end-journey}

Este diagrama ilustra a jornada do cliente em alto nível ao usar [!UICONTROL Cloud Manager] pipeline de CI/CD para implantar suas alterações de código em seus ambientes de armazenamento temporário e de produção.

![Jornada completa](/help/assets/screen_shot_2018-05-15at124004pm.png)
