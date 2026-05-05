---
title: Segurança e privacidade
description: Saiba mais sobre a segurança e a privacidade do seu código e ativos de artefato no Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 202
ht-degree: 100%

---

# Segurança e privacidade {#security-and-privacy}

Saiba mais sobre a segurança e a privacidade do seu código e ativos de artefato no Cloud Manager.

## Funções e permissões {#roles}

O [!UICONTROL Cloud Manager] tem funções pré-configuradas com permissões apropriadas.

Para saber mais sobre as possíveis funções que você pode atribuir no Admin Console e as permissões da função de usuário, consulte o documento [Permissões baseadas em funções](/help/requirements/role-based-permissions.md).

## Isolamento de recurso {#resource-isolation}

Os clientes do [!UICONTROL Cloud Manager] precisam das credenciais IMS para se autenticarem, uma vez que todas as permissões vinculadas ao [!UICONTROL Cloud Manager] estão vinculadas às suas organizações IMS. Durante o processo de integração, a equipe de provisionamento garante que o isolamento de recursos seja aplicado no [!UICONTROL Cloud Manager].

## Segurança de dados {#data-security}

O código no [!UICONTROL Cloud Manager] é criptografado em trânsito. Os binários criados pelo Cloud Manager também são criptografados em trânsito e quando armazenados.

Cada cliente recebe seu próprio repositório Git com código protegido que não é compartilhado com outras organizações.

## Privacidade de dados {#data-privacy}

O [!UICONTROL Cloud Manager] segue os princípios de privacidade definidos pela Adobe. Desenvolvedores enviam o código com segurança para repositórios Git por HTTPS.

A interface do [!UICONTROL Cloud Manager] é criada com base em serviços que estão em conformidade com uma estrutura de controle comum da Adobe. A interface do [!UICONTROL Cloud Manager] usa serviços seguros de vários provedores de nuvem.
