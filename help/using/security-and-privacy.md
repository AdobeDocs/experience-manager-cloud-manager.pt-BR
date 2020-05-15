---
title: Segurança e privacidade
seo-title: Segurança e privacidade do AEM Cloud Manager
description: Siga esta página para saber mais sobre a segurança e privacidade de seus ativos (código/artefatos).
seo-description: Siga esta página para saber mais sobre a segurança e a privacidade de seus ativos (código/artefatos) usando o AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: e2187565e7f06d64841eb2af9b4b1a56feb5ebe4
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 2%

---


# Segurança e privacidade {#security-and-privacy}

[!UICONTROL Cloud Manager] tem funções pré-configuradas com permissões apropriadas. Esta seção destaca a segurança e a privacidade de seus ativos (código/artefatos) usando o AEM Cloud Manager. Além disso, [!UICONTROL Cloud Manager] tem funções pré-configuradas com permissões apropriadas.

Para saber mais sobre as possíveis funções que você pode atribuir no Admin Console e as permissões de função do usuário, consulte Permissões [baseadas em](/help/using/role-based-permissions.md)funções.


## Isolamento do recurso {#resource-isolation}

Os clientes que usam [!UICONTROL Cloud Manager] suas credenciais de IMS precisarão ser autenticados, pois todas as permissões vinculadas [!UICONTROL Cloud Manager] serão configuradas e vinculadas à organização de IMS. Durante o processo de integração, a equipe de provisionamento garante que o isolamento de recursos seja aplicado em [!UICONTROL Cloud Manager].

## Segurança de dados {#data-security}

O código em [!UICONTROL Cloud Manager] é criptografado em trânsito. Os binários criados pelo Cloud Manager também são criptografados em trânsito e criptografados quando armazenados.

Cada cliente recebe seu próprio Repositório **** Git e seu código é seguro e não é compartilhado com outras **Organizações**.

## Privacidade de dados {#data-privacy}

[!UICONTROL Cloud Manager] segue os princípios de privacidade definidos pela Adobe. Os desenvolvedores enviam o código com segurança para o Repositório **Git** em HTTPS.

A interface do usuário (UI) para [!UICONTROL Cloud Manager] é desenvolvida sobre os serviços compatíveis com uma estrutura de controle comum definida pela Adobe. Interface do usuário para [!UICONTROL Cloud Manager] usar serviços protegidos de vários provedores de nuvem.
