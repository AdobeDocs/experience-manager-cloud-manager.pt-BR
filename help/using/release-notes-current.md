---
title: Notas da versão 2021.3.0
seo-title: Notas de versão do AEM Cloud Manager para 2021.3.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.3.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2021.3.0
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 5%

---

# Notas da versão 2021.3.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2021.3.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2021.3.0 é 11 de março de 2021.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* Uma nova ferramenta de qualidade de código foi introduzida para validar a configuração do dispatcher do cliente (Ferramenta de Otimização do Dispatcher).

* Os usuários agora podem ver suas funções do Cloud Manager selecionando a opção **Exibir função(ões) do Cloud Manager** após navegar até o ícone Perfil do usuário (canto superior direito) do Unified Shell.

* O rótulo **Application for Approval** foi renomeado para **Production Approval** para maior clareza.

* O rótulo **Version** foi renomeado para **Git Tag** na tela de execução do pipeline de Produção.

* Os rótulos que definem o comportamento quando métricas importantes não alcançam o limite definido foram renomeados para refletir seu comportamento verdadeiro - Cancelar imediatamente e Aprovar imediatamente.

* As listas de desaprovação de classe e método foram atualizadas com base na versão `2021.3.4997.20210303T022849Z-210225` do SDK do Cloud Service AEM.

## Correções de erros {#bug-fixes}

* Alguns problemas de qualidade não foram detectados corretamente quando os pacotes eram incorporados em outros pacotes.

* Ocasionalmente, se o usuário sair da página de execução do pipeline imediatamente após iniciar um pipeline, uma mensagem de erro será exibida informando que a ação falhou, embora a execução realmente comece.