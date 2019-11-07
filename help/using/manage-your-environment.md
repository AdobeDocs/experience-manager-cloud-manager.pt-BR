---
title: Gerenciar os ambientes
seo-title: Gerenciar os ambientes
description: 'null'
seo-description: Siga esta página para exibir a lista de ambientes de produção e de não produção usados para configurar e executar o pipeline de CI/CD no Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: usando
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
translation-type: tm+mt
source-git-commit: c81243708d938a8bffdec8a35f32a2cf552c1c95

---


# Gerenciar os ambientes {#manage-your-environments}

A página **Visão geral** do Gerenciador de nuvem inclui o bloco **Ambientes** que lista todos os ambientes AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![](assets/Manage-Environ-Overview.png)

## Tutorial em vídeo {#video-tutorial}

### Visão geral do ambiente do Cloud Manager {#environ-video}

O vídeo a seguir fornece uma visão geral dos Ambientes do Cloud Manager que são compostos por instâncias do AEM Author, AEM Publish e Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/?captions=por_br)

## Acessar ambientes no Cloud Manager {#accessing-environments-in-cloud-manager}

O bloco **Ambientes** exibe os ambientes Produção e Fase provisionados em seu programa junto com o status.

O status é o estado de energia acumulada nos nós no ambiente. É verde se todos os nós estiverem em execução, vermelho se mesmo um nó estiver parado, azul se mesmo um nó estiver aparecendo e amarelo se mesmo um nó tiver um estado de energia indisponível (nessa ordem de prioridade).

![](assets/Environments-card-new.png)

### Ambientes {#environments}

Clique em **Gerenciar** para exibir a tela **Ambientes** .

A tela **Ambientes** exibe um cartão cada para os ambientes *Produção* e *Fase* (conforme aplicável) no programa. O nome do ambiente é visto acima de cada placa. A placa inclui uma tabela de nós no ambiente, juntamente com o tamanho de t-shirt da cpu, o armazenamento, a região e o status.

>[!NOTE]
>
>O **STATUS** do nó representa o estado de energia da VM e não reflete o status do AEM no servidor. O status pode ser **Em execução** (círculo verde), **Interrompido** (círculo vermelho), **Subindo** (círculo azul) ou **Indisponível** (círculo amarelo).

![](assets/Environments-tab.png)
