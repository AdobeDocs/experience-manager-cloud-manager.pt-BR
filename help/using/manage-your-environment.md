---
title: Gerenciar os ambientes
seo-title: Manage your Environments
description: Saiba mais sobre o ambiente do Cloud Manager
seo-description: Follow this page to view the list of production and non-production environments that are used for setting up and running the CI/CD pipeline in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Environments
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 6ff704ec11dd4a5f73d5b5df5721c4fee649527b
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 6%

---

# Gerenciar os ambientes {#manage-your-environments}

>[!NOTE]
>Para saber mais sobre o gerenciamento de ambientes para o Cloud Manager AEM as a Cloud Service, consulte [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=pt-BR#using-cloud-manager).

O **Visão geral** A página do Cloud Manager inclui a variável **Ambientes** bloco que lista todos os ambientes de AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![](assets/Manage-Environ-Overview.png)

## Tutorial em vídeo {#video-tutorial}

### Visão geral do ambiente do Cloud Manager {#environ-video}

O vídeo a seguir fornece uma visão geral dos Ambientes do Cloud Manager que são compostos de instâncias do AEM Author, AEM Publish e Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Acesso a ambientes no Cloud Manager {#accessing-environments-in-cloud-manager}

O **Ambientes** O bloco exibe os ambientes de Produção e Estágio provisionados no programa junto com o status .

O status é o estado de energia acumulado entre os nós no ambiente. É verde se todos os nós estiverem em execução, vermelho se mesmo um nó estiver parado, azul se mesmo um nó estiver aparecendo e amarelo se mesmo um nó tiver um estado de energia indisponível (nessa ordem de prioridade).

![](assets/Environments-card-new.png)

### Ambientes {#environments}

Clique em **Gerenciar** para exibir o **Ambientes** tela.

O **Ambientes** exibe um cartão para cada *Produção* e *Fase* em seu programa. O nome do ambiente é visto acima de cada cartão. O cartão inclui uma tabela de nós no ambiente, juntamente com o tamanho da camiseta da cpu, o armazenamento, a região e o status.

>[!NOTE]
>
>O **STATUS** do nó representa o estado de energia da VM e não reflete o status de AEM no servidor. O status pode ser **Em execução** (círculo verde), **Parado** (círculo vermelho), **Em breve** (círculo azul) ou **Indisponível** (círculo amarelo).

![](assets/Environments-tab.png)

>[!NOTE]
>
>Se você precisar de seus registros de ambiente, eles poderão ser solicitados por meio de seu engenheiro de sucesso do cliente.
