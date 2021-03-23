---
title: Notas da versão 2020.8.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.8.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2020.8.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2020.8.0
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 7%

---

# Notas da versão 2020.8.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2020.8.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2020.8.0 é 6 de agosto de 2020.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

Agora há suporte para Repositórios Maven privados vinculados à autenticação.

## Correções de erros {#bug-fixes}

* Alguns plug-ins desnecessários e indesejados do SonarQube estavam sendo executados como parte da verificação de qualidade do código.

* Na página de execução do pipeline, o nome da ramificação estava formatado incorretamente.

* Ao implantar topologias com uma única publicação, um único dispatcher e um autor de standby frio, o dispatcher foi removido erroneamente do balanceador de carga.

* Em alguns casos, as execuções de pipeline concluídas não foram registradas com êxito como tendo sido concluídas, impedindo assim novas execuções do pipeline.

* Ocasionalmente, as execuções de pipeline ficariam *presas* devido a problemas de comunicação interna.

* A dica de ferramenta nos cartões de programa não estava consistentemente correta.

* Havia uma incompatibilidade de cores na página **Visão geral**.

* O Teste de desempenho de sites agora é compatível com o uso opcional da autenticação.

* Os caches do Dispatcher para instâncias de autor são automaticamente liberados quando as configurações do dispatcher são implantadas por meio do Cloud Manager.

