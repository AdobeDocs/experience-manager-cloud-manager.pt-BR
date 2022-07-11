---
title: Segurança e privacidade
description: Saiba mais sobre a segurança e a privacidade de seu código e ativos de artefato no Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 3%

---


# Segurança e privacidade {#security-and-privacy}

Saiba mais sobre a segurança e a privacidade de seu código e ativos de artefato no Cloud Manager.

## Funções e permissões {#roles}

[!UICONTROL Cloud Manager] O tem funções pré-configuradas com permissões apropriadas.

Para saber mais sobre as possíveis funções que você pode atribuir nas permissões de Admin Console e função de usuário, consulte o documento [Permissões baseadas em funções.](/help/requirements/role-based-permissions.md)

## Isolamento de Recurso {#resource-isolation}

[!UICONTROL Cloud Manager] Os clientes precisam de suas credenciais IMS para se autenticar como todas as permissões vinculadas ao [!UICONTROL Cloud Manager] estão vinculadas às suas organizações IMS. Durante o processo de integração, a equipe de provisionamento garante que o isolamento de recursos seja aplicado em [!UICONTROL Cloud Manager].

## Segurança de dados {#data-security}

Entrada de código [!UICONTROL Cloud Manager] está criptografada em trânsito. Os binários criados pelo Cloud Manager também são criptografados em trânsito e criptografados quando armazenados.

Cada cliente recebe seu próprio repositório Git e o código é seguro e não é compartilhado com outras organizações.

## Privacidade de dados {#data-privacy}

[!UICONTROL Cloud Manager] adere aos princípios de privacidade definidos pelo Adobe. Os desenvolvedores enviam o código com segurança para repositórios Git por HTTPS.

[!UICONTROL Cloud Manager]A interface do usuário do é criada sobre serviços que estão em conformidade com uma estrutura de controle Adobe comum que. [!UICONTROL Cloud Manager]A interface do usuário do usa serviços seguros de vários provedores de nuvem.
