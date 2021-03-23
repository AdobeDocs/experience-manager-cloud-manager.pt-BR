---
title: Notas da versão 2020.11.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.11.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2020.11.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2020.11.0
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 8%

---

# Notas da versão 2020.11.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2020.11.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2020.11.0 é 12 de novembro de 2020.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* A guia **Aprendizagem** no Cloud Manager é atualizada com novas imagens na interface do usuário.

## Correções de erros {#bug-fixes}

* Certos erros de implantação causados pelo cliente agora serão explicitamente encontrados nos logs de implantação.

* O carregamento de dependências feitas antes da execução da build requer o download de um plug-in Maven.

* O link do rodapé do Cloud Manager para selecionar um idioma agora irá navegar até o local correto.

* Às vezes, durante a verificação do código, o processo SonarQube não era iniciado. Isso será detectado automaticamente e uma reinicialização tentada.

* Durante o processo de rastreamento do site usado em testes de desempenho, as solicitações que expirarem nos três primeiros níveis de percurso profundo serão repetidas automaticamente.