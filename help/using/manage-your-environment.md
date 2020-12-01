---
title: Gerenciar os ambientes
seo-title: Gerenciar os ambientes
description: 'null'
seo-description: Siga esta página para visualização da lista de ambientes de produção e de não produção usados para configurar e executar o pipeline de CI/CD no Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
translation-type: tm+mt
source-git-commit: c81243708d938a8bffdec8a35f32a2cf552c1c95
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 4%

---


# Gerenciar os ambientes {#manage-your-environments}

A página **Visão geral** do Cloud Manager inclui o bloco **Ambientes** que lista todos os ambientes AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![](assets/Manage-Environ-Overview.png)

## Tutorial em vídeo {#video-tutorial}

### Visão geral do Ambiente do Cloud Manager {#environ-video}

O vídeo a seguir fornece uma visão geral dos Ambientes do Cloud Manager que são compostos por instâncias do AEM Author, AEM Publish e Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Acessar Ambientes no Cloud Manager {#accessing-environments-in-cloud-manager}

O bloco **Ambientes** exibe os ambientes de Produção e Estágio provisionados no programa juntamente com o status.

O status é o estado de energia acumulada nos nós do ambiente. É verde se todos os nós estiverem em execução, vermelho se mesmo um nó estiver parado, azul se mesmo um nó estiver aparecendo e amarelo se mesmo um nó tiver um estado de energia indisponível (nessa ordem de prioridade).

![](assets/Environments-card-new.png)

### Ambientes {#environments}

Clique em **Gerenciar** para exibir a tela **Ambientes**.

A tela **Ambientes** exibe um cartão para ambientes *Production* e *Stage* (conforme aplicável) no programa. O nome do ambiente é visto acima de cada cartão. A placa inclui uma tabela de nós no ambiente, juntamente com o tamanho de t-shirt da cpu, do armazenamento, da região e do estado.

>[!NOTE]
>
>O **STATUS** do nó representa o estado de energia da VM e não reflete o estado do AEM no servidor. O status pode ser **Execução** (círculo verde), **Parado** (círculo vermelho), **Aproximando** (círculo azul) ou **Indisponível** (círculo amarelo).

![](assets/Environments-tab.png)
