---
title: Integração de usuários
description: Saiba mais sobre os diferentes cenários de integração e a introdução ao Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
TQID: https://experienceleague.adobe.com/EnNaMZzu5bLUD3Jjsp6ovqFvoFM30ju4FOQJfmySLEk
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2cd89edca1c1dfac7f1b7b68eccdf1416efb4724
workflow-type: tm+mt
source-wordcount: 567
ht-degree: 62%

---

# Integração de usuários {#user-journey}

Como usuário do AEM (Adobe Experience Manager), você se ajusta a um dos seguintes cenários:

* Você é novo no AEM.
* Você está usando atualmente o AEM 6.x.
* Você precisa atualizar para o AEM 6.5 para usar o [!UICONTROL Cloud Manager].

Este documento descreve esses três cenários e explica o processo de introdução ao [!UICONTROL Cloud Manager].

>[!NOTE]
>
>O [!UICONTROL Cloud Manager] só está disponível para clientes do Adobe Managed Services (AMS) que usam o AEM 6.4 ou superior.

## Integração {#onboarding}

Dependendo se você é novo no AMS ou se já é cliente do AMS, o processo de integração é diferente.

### Novo no Adobe Managed Services {#new-to-ams}

Como novo cliente, você foi integrado ao [!UICONTROL Cloud Manager] como parte do processo de integração ao Adobe Managed Services.

Como parte do processo de integração, você receberá um email de boas-vindas que inclui:

* O URL para acessar o [!UICONTROL Cloud Manager].
* Instruções para fazer logon na [!UICONTROL Experience Cloud].
* Instruções de uso do Admin Console para gerenciar usuários e suas respectivas permissões para que eles possam acessar o Cloud Manager se necessário.

### Cliente atual do Adobe Managed Services {#existing-customer}

Como cliente do AMS, primeiro será necessário atualizar seus ambientes de produção e não produção já existentes para o AEM 6.4 ou superior.

Durante a atualização, você será integrado ao Cloud Manager e receberá o URL para acessar o [!UICONTROL Cloud Manager]. Além disso, para usuários que precisam acessar o [!UICONTROL Cloud Manager], será necessário usar o Admin Console para gerenciá-los e suas respectivas permissões.

Seu projeto existente do AEM também precisa estar em conformidade com as práticas recomendadas, pois você começa a usar o [!UICONTROL Cloud Manager] para implantar novas alterações de código em seus ambientes do AEM.

Para obter informações adicionais sobre os benefícios de atualizar para o AEM 6.5, consulte [Atualização para o AEM 6.5](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Acessar o [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Faça logon na página de destino da [!UICONTROL Experience Cloud] usando suas credenciais do Adobe Identity Management. Selecione AEM no alternador de soluções para acessar o [!UICONTROL Cloud Manager] e seus ambientes do AEM.

Após fazer logon no [!UICONTROL Cloud Manager] pela primeira vez, você terá acesso aos ambientes do AEM diretamente da interface do [!UICONTROL Cloud Manager]. Neste ponto, você está pronto para usar todos os recursos do [!UICONTROL Cloud Manager] e preparar sua primeira ramificação de código a ser implantada nos seus ambientes de preparo e produção.

Para começar a usar o [!UICONTROL Cloud Manager], consulte [Primeiro Logon](/help/getting-started/first-time-login.md).

Para obter informações adicionais sobre o AEM, consulte [Implantação e manutenção](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Introdução ao [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Após fazer logon no [!UICONTROL Cloud Manager], você pode começar a usar o projeto do AEM da seguinte forma:

1. Configure o ambiente do repositório de código.
1. Configure a equipe e funções. As associações de função são atribuídas adicionando o usuário a um perfil do [!UICONTROL Cloud Manager] usando o Admin Console.
1. Configure as ramificações do código-fonte no repositório Git.
1. Defina os KPIs de carga e desempenho (Indicadores-chave de desempenho).
1. Defina cenários de teste para implantar com sucesso seu código em seus ambientes de preparo e produção depois que todas as verificações de qualidade forem aprovadas.

## Visão geral do processo {#end-to-end-journey}

O diagrama a seguir resume o processo ao usar o pipeline CI/CD do [!UICONTROL Cloud Manager] para implantar suas alterações de código em seus ambientes de preparo e produção.

![jornada do cliente para integração com o Cloud Manager, mostrando o caminho para clientes novos e existentes por meio de provisionamento ou atualizações de ambiente, gerenciamento de usuários e funções, implementação de projetos e pipeline de CI/CD.](/help/assets/screen_shot_2018-05-15at124004pm.png)
