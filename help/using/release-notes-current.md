---
title: Notas da versão 2020.8.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.8.0
description: Siga esta página para obter informações sobre a versão 2020.8.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.8.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 3be958aa21d5423ddf371c286825d01afd554c4b
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 20%

---

# Notas da versão 2020.8.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.8.0.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2020.8.0 é 6 de agosto de 2020.

## Novidades {#whats-new}

* O teste de desempenho de sites agora suporta o uso opcional da autenticação.

   Consulte para obter mais detalhes.

* Agora há suporte para Repositórios de Maven Privado com vínculo de autenticação.

## Correções de erros {#bug-fixes}

* Alguns plug-ins SonarQube desnecessários e indesejados estavam sendo executados como parte da verificação de qualidade de código.

* Na página de execução de pipeline, o nome da ramificação estava formatado incorretamente.

* Ao implantar topologias com uma única publicação, um único despachante e um autor em modo de espera frio, o despachante foi removido erroneamente do balanceador de carga.

* Em alguns casos, as execuções de pipeline concluídas não foram registradas com êxito como tendo sido concluídas, impedindo assim novas execuções do pipeline.

* Ocasionalmente, as execuções de tubulação ficariam *presas* devido a problemas de comunicação interna.

* A dica de ferramenta nos cartões de programa não estava consistentemente correta.

* Houve uma incompatibilidade de cores na página de visão geral.

## Problemas conhecidos {#known-issues}

* Quando um ambiente AMS contém uma instância stand-by, a mensagem registrada informa que a instância está inativa em vez de no modo de espera.

* Devido a uma mudança na forma como a cobertura de código é calculada, a versão _mínima_ do plug-in Jacoco agora é a 0.7.5.201505241946 (lançada em maio de 2015). Os clientes que indicarem uma versão mais antiga receberão uma mensagem de erro no processo de qualidade do código.
