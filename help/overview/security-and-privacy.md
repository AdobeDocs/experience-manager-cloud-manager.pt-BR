---
title: Segurança e privacidade
description: Saiba mais sobre a segurança e a privacidade de seu código e ativos de artefato no Adobe Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# Segurança e privacidade {#security-and-privacy}

Saiba mais sobre a segurança e a privacidade de seu código e ativos de artefato no Adobe Cloud Manager.

## Funções e permissões {#roles}

O Cloud Manager tem funções pré-configuradas com permissões apropriadas.

Para saber mais sobre as possíveis funções que você pode atribuir no Admin Console e as permissões da função de usuário, consulte o documento [Permissões baseadas em funções](/help/requirements/role-based-permissions.md).

## Isolamento de recurso {#resource-isolation}

Os clientes do Cloud Manager precisam das credenciais IMS para se autenticarem porque todas as permissões vinculadas ao Cloud Manager estão vinculadas às suas organizações IMS. Durante o processo de integração, a equipe de provisionamento garante que o isolamento de recursos seja aplicado no Cloud Manager.

## Segurança de dados {#data-security}

O código Cloud Manager é criptografado em trânsito. O Cloud Manager cria binários que também são criptografados durante a transmissão e armazenados em um formato criptografado.

Cada cliente recebe seu próprio repositório Git, e o código é protegido e não compartilhado com outra organização.

## Privacidade de dados {#data-privacy}

A Cloud Manager segue os princípios de privacidade definidos pela Adobe. Desenvolvedores enviam o código com segurança para repositórios Git por HTTPS.

A interface do usuário do Cloud Manager usa serviços que estão em conformidade com a Estrutura de controle comum do Adobe. A interface de usuário do Cloud Manager usa serviços seguros de vários provedores de nuvem.
