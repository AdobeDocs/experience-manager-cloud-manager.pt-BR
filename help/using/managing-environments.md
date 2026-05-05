---
title: Gerenciamento de ambientes
description: Saiba como usar o Cloud Manager para gerenciar seus ambientes.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 275
ht-degree: 100%

---

# Gerenciamento de ambientes {#managing-environments}

Saiba como usar o Cloud Manager para gerenciar seus ambientes.

## Página de visão geral {#overview-page}

A página de **visão geral** do Cloud Manager inclui o bloco **Ambientes** que lista todos os ambientes do AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![Página de visão geral](/help/assets/Manage-Environ-Overview.png)

## Bloco de ambientes {#environments-tile}

O bloco **Ambientes** exibe os ambientes de produção e de preparo provisionados no programa junto com o status.

O status é o estado de energia acumulado nos nós do ambiente na seguinte ordem de prioridade.

* Verde - Todos os nós estão em execução
* Vermelho - Um ou mais nós foram interrompidos.
* Azul - Um ou mais nós estão chegando.
* Amarelo - Um ou mais nós têm um estado de energia indisponível.

![Bloco de ambientes](/help/assets/Environments-card-new.png)

## Gerenciamento de ambientes {#managing-environments-with-cloud-manager}

No bloco **Ambientes**, clique na linha de qualquer ambiente para exibir a tela **Ambientes**.

A tela **Ambientes** exibe cada ambiente de produção e preparo do seu programa. O nome do ambiente é visto acima de cada cartão. O cartão inclui uma tabela de nós no ambiente, juntamente com o tamanho da CPU, o armazenamento, a região e o status.

>[!NOTE]
>
>O **STATUS** do nó representa o estado de energia da VM e não reflete o status do AEM no servidor. O status pode ser:

* Verde - Em execução
* Vermelho - Parado
* Azul - Chegando
* Amarelo - Indisponível

![Guia Ambientes](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Detalhes do ambiente, como nome, não podem ser alterados depois de provisionados.

>[!NOTE]
>
>Solicite os logs do seu ambiente por meio do engenheiro de sucesso do cliente.

## Tutorial em vídeo {#video-tutorial}

Este vídeo fornece uma visão geral dos ambientes do Cloud Manager que são compostos por instâncias de criação, publicação e Dispatcher do AEM.

>[!VIDEO](https://video.tv.adobe.com/v/34272?captions=por_br)

*(3 minutos, 1 segundo)*
