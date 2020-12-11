---
title: Notas da versão 2020.11.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.11.0
description: Siga esta página para obter informações sobre a versão 2020.11.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.11.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 5688e956c4c21968ce691b560a6ce519496f7563
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 7%

---

# Notas da versão 2020.11.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.11.0.

## Data de lançamento {#release-date}

A data de lançamento da versão 2020.11.0 [!UICONTROL Cloud Manager] é 12 de novembro de 2020.

## Novidades {#whats-new}

* A guia **Learn** no Cloud Manager é atualizada com novas imagens na interface do usuário.

## Correções de erros {#bug-fixes}

* Determinados erros de implantação causados pelo cliente agora serão explicitamente encontrados nos logs de implantação.

* O carregamento de dependências feitas antes da execução da compilação exigia o download de um plug-in Maven.

* O link do rodapé do Gerenciador de nuvem para selecionar um idioma agora navegará até o local correto.

* Às vezes, durante a digitalização do código, o processo SonarQube não era start. Isso será detectado automaticamente e uma tentativa de reinicialização será feita.

* Durante o processo de rastreamento do site usado no teste de desempenho, as solicitações que expirarem nos três primeiros níveis de detalhamento serão automaticamente repetidas.