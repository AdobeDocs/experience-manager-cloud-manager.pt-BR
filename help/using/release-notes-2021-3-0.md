---
title: Notas da versão 2021.3.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.3.0
feature: Release Information
source-git-commit: 09dd8fe608d95cd9dbc95129cf86b9693c2839b5
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 5%

---

# Notas da versão 2021.3.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais de [!UICONTROL Cloud Manager] Versão 2021.3.0.

## Data de lançamento {#release-date}

A data de lançamento para [!UICONTROL Cloud Manager] A versão 2021.3.0 é 11 de março de 2021.
A próxima versão está planejada para 8 de abril de 2021.

## Novidades {#whats-new}

* Uma nova ferramenta de qualidade de código [Ferramenta de otimização do Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) foi introduzido para validar a configuração do dispatcher do cliente.

* Agora, os usuários podem ver suas funções do Cloud Manager selecionando o **Exibir função(ões) do Cloud Manager** após navegar até o ícone Perfil do usuário (canto superior direito) do Unified Shell.

* O rótulo **Pedido de aprovação** foi renomeado para **Aprovação de produção** para maior clareza.

* O **Versão** foi renomeado para **Tag Git** na tela Production pipeline execution .

* Os rótulos que definem o comportamento quando métricas importantes não alcançam o limite definido foram renomeados para refletir seu comportamento verdadeiro - **Cancelar imediatamente** e **Aprovar imediatamente**. Consulte [Definição das configurações de pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) para obter mais detalhes.

* As listas de desaprovação de classe e método foram atualizadas com base na versão `2021.3.4997.20210303T022849Z-210225` do SDK do AEM Cloud Service.

## Correções de erros {#bug-fixes}

* Alguns problemas de qualidade não foram detectados corretamente quando os pacotes eram incorporados em outros pacotes.

* Ocasionalmente, se o usuário sair da página de execução do pipeline imediatamente após iniciar um pipeline, uma mensagem de erro será exibida informando que a ação falhou, embora a execução realmente comece.
