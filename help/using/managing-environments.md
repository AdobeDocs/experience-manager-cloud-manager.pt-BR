---
title: Gerenciar ambientes
description: Saiba como usar o Cloud Manager para gerenciar seus ambientes.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 78%

---


# Gerenciar ambientes {#managing-environments}

Saiba como usar o Cloud Manager para gerenciar seus ambientes.

## Página de visão geral {#overview-page}

A página de **visão geral** do Cloud Manager inclui o bloco **Ambientes** que lista todos os ambientes do AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![Página de visão geral](/help/assets/Manage-Environ-Overview.png)

## Bloco Ambientes {#environments-tile}

O bloco **Ambientes** exibe os ambientes de produção e de preparo provisionados no programa junto com o status.

O status é o estado de energia acumulado nos nós do ambiente na seguinte ordem de prioridade.

* Verde - Todos os nós estão em execução
* Vermelho - Um ou mais nós foram interrompidos.
* Azul - Um ou mais nós estão chegando.
* Amarelo - Um ou mais nós têm um estado de energia indisponível.

![Bloco de ambientes](/help/assets/Environments-card-new.png)

## Gerenciar ambientes {#managing-environments-with-cloud-manager}

No bloco **Ambientes**, clique na linha de qualquer ambiente para exibir a tela **Ambientes**.

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
>Detalhes do ambiente, como um nome, não podem ser alterados depois de provisionados.

>[!NOTE]
>
>Se você precisar de seus registros de ambiente, eles poderão ser solicitados por meio do seu engenheiro de sucesso do cliente.

## Tutorial em vídeo {#video-tutorial}

Este vídeo fornece uma visão geral dos ambientes do Cloud Manager que são compostos por instâncias de criação, publicação e Dispatcher do AEM.

>[!VIDEO](https://video.tv.adobe.com/v/26318/) (3 minutos, 1 segundo)
