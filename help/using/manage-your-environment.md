---
title: Gerenciar seus ambientes
seo-title: Gerenciar seus ambientes
description: 'null'
seo-description: Siga esta página para exibir a lista de ambientes de produção e não produção usados para configurar e executar o pipeline CI/CD no Gerenciador de nuvem.
uuid: 04 e 67572-11 db -4 d 5 d-acf 3-fd 7 f 644 a 95 f 0
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: usando
discoiquuid: c 5 b 39 de 2-3 a 9 b -437 f -98 e 8-e 6 e 6249 a 5 b 3 a
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Gerenciar seus ambientes {#manage-your-environments}

A página **Visão geral** do Gerenciador de nuvem inclui o bloco **de Ambientes** que lista todos os ambientes AEM gerenciados.

Cada um dos ambientes listados exibe seu status associado.

![](assets/Manage_Environments1.png)

## Acessar ambientes no Gerenciador de nuvem {#accessing-environments-in-cloud-manager}

O bloco **Ambientes** exibe os ambientes de Produção e Stage fornecidos no seu programa junto com o status.

O status é o estado de potência integrada entre os nós no ambiente. É verde se todos os nós estiverem sendo executados, vermelho se até mesmo um nó for interrompido, azul se até um nó estiver chegando e amarelo se até um nó tiver um estado de potência indisponível (nesta ordem de prioridade).

![](assets/manage_environments-screen2.png)

### Ambientes {#environments}

Clique **em Gerenciar** para exibir a **tela Ambientes** .

A tela **Ambientes** exibe um cartão para os ambientes *Production* e *Stage* (se for o caso) no seu programa. O nome do ambiente é visualizado acima de cada cartão. O cartão inclui uma tabela de nós no ambiente junto com o tamanho t-camt da cpu, o armazenamento, a região e o status.

>[!NOTE]
>
>O **STATUS** do nó representa o estado de potência da VM e não reflete o status do AEM no servidor. O status pode estar **em Execução** (círculo verde), **Interrompido** (círculo vermelho), **Vindo** (círculo azul) ou **Indisponível** (círculo amarelo).

![](assets/Manage_Environments2.png)
