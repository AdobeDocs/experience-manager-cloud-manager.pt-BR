---
title: Notas da versão 2020.4.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.4.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2020.4.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2020.4.0
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 38%

---

# Notas da versão 2020.4.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2020.4.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2020.4.0 é 9 de abril de 2020.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* Alterações na página de visão geral do Cloud Manager de navegação para permitir que o usuário edite ou alterne o programa.
* Alterações para permitir que o usuário edite o programa no cartão de programa na página de aterrissagem do Cloud Manager.
* Novo status de pipeline **Pipeline Running** exibido no ambiente ao qual está associado.
* Melhorias na compreensão da página de execução do pipeline. Isso inclui a exibição do Nome do pipeline (somente para pipeline de não produção) e Tipo, e um selo para indicar se o status do pipeline é Em andamento/Cancelado/Com falha.
* O processo usado para gerar senhas git tornou-se mais resiliente aos problemas na camada de serviço subjacente.

## Correções de erros {#bug-fixes}

* Os dados de monitoramento podem, às vezes, ser exibidos de forma incorreta ou não de forma alguma com base em pequenas variações em valores técnicos.
* A configuração de Maven usada em Criar contêiner foi atualizada para evitar bloqueios ao baixar metadados de artefato.
* Ocasionalmente, o processo de teste de desempenho do Assets não conseguia descriptografar a senha do AEM, causando falha no teste.
* Determinadas topologias com instâncias de standby podem ter falsos negativos em testes de segurança.
* Se o ambiente de preparo contivesse uma instância interrompida, a etapa de teste de segurança às vezes falharia.
* As notificações da Experience Cloud não eram recebidas de forma consistente.

