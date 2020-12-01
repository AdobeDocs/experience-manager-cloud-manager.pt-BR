---
title: Notas da versão 2020.8.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.8.0
description: Siga esta página para obter informações sobre a versão 2020.8.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.8.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: c1d07c95088a279376ef495001a5165c7e459642
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 6%

---

# Notas da versão 2020.8.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.8.0.

## Data de lançamento {#release-date}

A data de lançamento da versão 2020.8.0 [!UICONTROL Cloud Manager] é 6 de agosto de 2020.

## Novidades {#whats-new}

Agora há suporte para Repositórios de Maven Privado com vínculo de autenticação.

## Correções de erros {#bug-fixes}

* Alguns plug-ins SonarQube desnecessários e indesejados estavam sendo executados como parte da verificação de qualidade de código.

* Na página de execução de pipeline, o nome da ramificação estava formatado incorretamente.

* Ao implantar topologias com uma única publicação, um único despachante e um autor em modo de espera frio, o despachante foi removido erroneamente do balanceador de carga.

* Em alguns casos, as execuções de pipeline concluídas não foram registradas com êxito como tendo sido concluídas, impedindo assim novas execuções do pipeline.

* Ocasionalmente, as execuções de pipeline ficariam *emperradas* devido a problemas de comunicação interna.

* A dica de ferramenta nos cartões de programa não estava consistentemente correta.

* Houve uma incompatibilidade de cores na página **Visão geral**.

* O teste de desempenho de sites agora suporta o uso opcional da autenticação.

* Os caches do Dispatcher para instâncias do autor são automaticamente liberados quando as configurações do dispatcher são implantadas por meio do Cloud Manager.

