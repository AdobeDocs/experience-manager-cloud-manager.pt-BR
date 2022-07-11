---
title: Gerenciamento de ambientes
description: Saiba como usar o Cloud Manager para gerenciar seus ambientes.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 80f8707e00357f5a08dd835b846c9ee610f3e573
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 2%

---


# Gerenciamento de ambientes {#managing-environments}

Saiba como usar o Cloud Manager para gerenciar seus ambientes.

## Página Visão geral {#overview-page}

O **Visão geral** A página do Cloud Manager inclui a variável **Ambientes** bloco que lista todos os ambientes de AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![Página Visão geral](/help/assets/Manage-Environ-Overview.png)

## Bloco de ambientes {#environments-tile}

O **Ambientes** O bloco exibe os ambientes de produção e de preparo provisionados no programa junto com o status .

O status é o estado de energia acumulado entre os nós no ambiente na seguinte ordem de prioridade.

* Verde - Todos os nós estão em execução
* Vermelho - Um ou mais nós foram interrompidos.
* Azul - Um ou mais nós estão chegando.
* Amarelo - Um ou mais nós têm um estado de energia indisponível.

![Mosaico de ambientes](/help/assets/Environments-card-new.png)

## Gerenciamento de ambientes {#managing-environments-with-cloud-manager}

No **Ambientes** bloco, clique em **Gerenciar** para exibir o **Ambientes** tela.

O **Ambientes** exibe um cartão para ambientes de produção e de preparo (conforme aplicável) em seu programa. O nome do ambiente é visto acima de cada cartão. O cartão inclui uma tabela de nós no ambiente, juntamente com o tamanho da camiseta da cpu, o armazenamento, a região e o status.

>[!NOTE]
>
>O **STATUS** do nó representa o estado de energia da VM e não reflete o status de AEM no servidor. O status pode ser:

* Verde - Em Execução
* Vermelho - Parado
* Azul - Em breve
* Amarelo - Indisponível

![Guia Ambientes](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Se você precisar de seus registros de ambiente, eles poderão ser solicitados por meio de seu engenheiro de sucesso do cliente.

## Tutorial em vídeo {#video-tutorial}

Este vídeo fornece uma visão geral dos ambientes do Cloud Manager que são compostos por instâncias de criação, publicação e Dispatcher de AEM.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)
