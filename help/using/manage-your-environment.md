---
title: Gerenciar os ambientes
seo-title: Gerenciar os ambientes
description: Saiba mais sobre o ambiente do Cloud Manager
seo-description: Siga esta página para exibir a lista de ambientes de produção e não de produção que são usados para configurar e executar o pipeline de CI/CD no Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Environments
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 4%

---


# Gerenciar os ambientes {#manage-your-environments}

A página **Visão geral** do Cloud Manager inclui o bloco **Ambientes** que lista todos os ambientes de AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![](assets/Manage-Environ-Overview.png)

## Tutorial em vídeo {#video-tutorial}

### Visão geral do ambiente do Cloud Manager {#environ-video}

O vídeo a seguir fornece uma visão geral dos Ambientes do Cloud Manager que são compostos de instâncias do AEM Author, AEM Publish e Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Acesso a ambientes no Cloud Manager {#accessing-environments-in-cloud-manager}

O bloco **Ambientes** exibe os ambientes de Produção e Estágio provisionados no programa junto com o status .

O status é o estado de energia acumulado entre os nós no ambiente. É verde se todos os nós estiverem em execução, vermelho se mesmo um nó estiver parado, azul se mesmo um nó estiver aparecendo e amarelo se mesmo um nó tiver um estado de energia indisponível (nessa ordem de prioridade).

![](assets/Environments-card-new.png)

### Ambientes {#environments}

Clique em **Gerenciar** para exibir a tela **Ambientes**.

A tela **Ambientes** exibe um cartão cada para os ambientes *Produção* e *Preparo* (conforme aplicável) no seu programa. O nome do ambiente é visto acima de cada cartão. O cartão inclui uma tabela de nós no ambiente, juntamente com o tamanho da camiseta da cpu, o armazenamento, a região e o status.

>[!NOTE]
>
>O **STATUS** do nó representa o estado de energia da VM e não reflete o status de AEM no servidor. O status pode ser **Executando** (círculo verde), **Parado** (círculo vermelho), **Começando** (círculo azul) ou **Não disponível** (círculo amarelo).

![](assets/Environments-tab.png)
