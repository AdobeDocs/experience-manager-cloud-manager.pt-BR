---
title: Segurança e privacidade
description: Saiba mais sobre a segurança e a privacidade de seu código e ativos de artefato no Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 60%

---


# Segurança e privacidade {#security-and-privacy}

Saiba mais sobre a segurança e a privacidade de seu código e ativos de artefato no Cloud Manager.

## Funções e permissões {#roles}

O [!UICONTROL Cloud Manager] tem funções pré-configuradas com permissões apropriadas.

Para saber mais sobre as possíveis funções que você pode atribuir no Admin Console e as permissões de função de usuário, consulte [Permissões baseadas em funções](/help/requirements/role-based-permissions.md).

## Isolamento de recursos {#resource-isolation}

Os clientes do [!UICONTROL Cloud Manager] precisam das credenciais IMS para se autenticarem, uma vez que todas as permissões vinculadas ao [!UICONTROL Cloud Manager] estão vinculadas às suas organizações IMS. Durante o processo de integração, a equipe de provisionamento garante que o isolamento de recursos seja aplicado no [!UICONTROL Cloud Manager].

## Segurança de dados {#data-security}

O código no [!UICONTROL Cloud Manager] é criptografado em trânsito. Os binários criados pelo Cloud Manager também são criptografados em trânsito e quando armazenados.

Cada cliente recebe seu próprio repositório Git, e o código é protegido e não compartilhado com outras organizações.

## Privacidade de dados {#data-privacy}

O [!UICONTROL Cloud Manager] segue os princípios de privacidade definidos pela Adobe. Os desenvolvedores enviam o código com segurança para repositórios Git por HTTPS.

A interface de usuário do [!UICONTROL Cloud Manager] é criada com base em serviços que estão em conformidade com uma estrutura de controle comum de Adobe. A interface do [!UICONTROL Cloud Manager] usa serviços seguros de vários provedores de nuvem.
