---
title: Segurança e privacidade
seo-title: Segurança e privacidade do AEM Cloud Manager
description: Siga esta página para saber mais sobre a segurança e a privacidade de seus ativos (código/artefatos).
seo-description: Siga esta página para saber mais sobre a segurança e a privacidade de seus ativos (código/artefatos) usando o AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
feature: Introdução
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 3%

---


# Segurança e privacidade {#security-and-privacy}

[!UICONTROL Cloud Manager] O tem funções pré-configuradas com permissões apropriadas. Esta seção destaca a segurança e a privacidade de seus ativos (código/artefatos) usando o AEM Cloud Manager. Além disso, [!UICONTROL Cloud Manager] tem funções pré-configuradas com permissões apropriadas.

Para saber mais sobre as possíveis funções que você pode atribuir nas permissões de Admin Console e função de usuário, consulte [Permissões baseadas em funções](/help/using/role-based-permissions.md).


## Isolamento de Recurso {#resource-isolation}

Os clientes que usam [!UICONTROL Cloud Manager] precisarão de suas credenciais IMS para se autenticarem, pois todas as permissões vinculadas a [!UICONTROL Cloud Manager] serão configuradas e vinculadas à organização IMS. Durante o processo de integração, a equipe de provisionamento garante que o isolamento de recursos seja aplicado em [!UICONTROL Cloud Manager].

## Segurança de dados {#data-security}

O código em [!UICONTROL Cloud Manager] está criptografado em trânsito. Os binários criados pelo Cloud Manager também são criptografados em trânsito e criptografados quando armazenados.

Cada cliente recebe seu próprio **Repositório Git** e seu código é seguro e não é compartilhado com nenhuma outra **Organizações**.

## Privacidade de dados {#data-privacy}

[!UICONTROL Cloud Manager] adere aos princípios de privacidade definidos pelo Adobe. Os desenvolvedores enviam o código com segurança para o **Repositório Git** por HTTPS.

A interface do usuário (UI) para [!UICONTROL Cloud Manager] é criada sobre os serviços que estão em conformidade com uma estrutura de controle comum definida pelo Adobe. A Interface do usuário para [!UICONTROL Cloud Manager] usa serviços seguros de vários provedores de nuvem.
