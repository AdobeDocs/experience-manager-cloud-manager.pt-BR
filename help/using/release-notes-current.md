---
title: Notas da versão 2021.3.0
seo-title: Notas de versão do AEM Cloud Manager para 2021.3.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.3.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2021.3.0
translation-type: tm+mt
source-git-commit: 5542942da33efc2926e62cce00ea39e3c65b3e16
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 4%

---

# Notas da versão 2021.3.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2021.3.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2021.3.0 é 11 de março de 2021.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* Os usuários com a permissão necessária agora podem editar o programa, permitindo que façam o seguinte de maneira automatizada:

   * Adicionar a solução Sites a um programa existente com Ativos (ou vice-versa).
   * Remova Sites (ou Ativos) de um programa existente com Sites e Ativos.
   * Adicionar (voltar) uma solução pode ser feita ao programa existente ou como um novo Programa.

* Uma nova ferramenta de qualidade de código [Ferramenta de Otimização do Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) foi introduzida para validar a configuração do dispatcher do cliente.

* Os usuários agora podem ver suas funções do Cloud Manager selecionando a opção **Exibir função(ões) do Cloud Manager** após navegar até o ícone Perfil do usuário (canto superior direito) do Unified Shell.

* O rótulo **Application for Approval** foi renomeado para **Production Approval** para maior clareza.

* O rótulo **Version** foi renomeado para **Git Tag** na tela de execução do pipeline de Produção.

* Os rótulos que definem o comportamento quando métricas importantes não atingem o limite definido foram renomeados para refletir seu comportamento verdadeiro - **Cancelar imediatamente** e **Aprovar imediatamente**.

* As listas de desaprovação de classe e método foram atualizadas com base na versão `2021.3.4997.20210303T022849Z-210225` do SDK do Cloud Service AEM.

## Correções de erros {#bug-fixes}

* Alguns problemas de qualidade não foram detectados corretamente quando os pacotes eram incorporados em outros pacotes.

* Ocasionalmente, se o usuário sair da página de execução do pipeline imediatamente após iniciar um pipeline, uma mensagem de erro será exibida informando que a ação falhou, embora a execução realmente comece.