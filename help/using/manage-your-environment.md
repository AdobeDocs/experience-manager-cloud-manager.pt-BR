---
title: Gerenciar seus ambientes
seo-title: Gerenciar seus ambientes
description: 'null'
seo-description: Siga esta página para exibir a lista de ambientes de produção e de não produção usados para configurar e executar o pipeline de CI/CD no Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: usando
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
translation-type: tm+mt
source-git-commit: 2b71bb61e00d462a43519ec0a2dcfe9231fe53ff

---


# Gerenciar seus ambientes {#manage-your-environments}

A página **Visão geral** do Gerenciador de nuvem inclui o bloco **Ambientes** que lista todos os ambientes AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![](assets/Manage_Environments1.png)

## Acessar ambientes no Cloud Manager {#accessing-environments-in-cloud-manager}

O bloco **Ambientes** exibe os ambientes Produção e Fase provisionados em seu programa junto com o status.

O status é o estado de energia acumulada nos nós no ambiente. It is green if all nodes are running, red if even one node is stopped, blue if even one node is coming up, and yellow if even one node has a power state unavailable (in this order of priority).

![](assets/manage_environments-screen2.png)

### Environments {#environments}

Click Manage to display the Environments screen.********

The Environments screen displays a card each for Production and Stage environments (as applicable) in your program. ******** The name of the environment is seen above each card. The card includes a table of nodes in the environment along with the t-shirt size of the cpu, the storage, the region, and the status.

>[!NOTE]
>
>The STATUS of the node represents the power state of the VM and does not reflect the status of AEM on the server. **** O status pode ser **Em execução** (círculo verde), **Interrompido** (círculo vermelho), **Subindo** (círculo azul) ou **Indisponível** (círculo amarelo).

![](assets/Manage_Environments2.png)
