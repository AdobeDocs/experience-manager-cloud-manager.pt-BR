---
title: Notas de versão para 2020.4.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.4.0
description: Siga esta página para obter informações sobre a versão 2020.4.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.4.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d

---

# Notas de versão para 2020.4.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.4.0.

## Release Date {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2020.4.0 é 9 de abril de 2020.

## Novidades {#whats-new}

* Alterações na página de visão geral do CM de navegação para permitir que o usuário edite ou alterne o programa da página de visão geral do CM.
* Alterações para permitir que o usuário edite o programa do cartão de programa na landing page CM.
* Novo status de pipeline &quot;Pipeline Running&quot; exibido no ambiente ao qual está associado.
* Melhorias na compreensão da página de execução de pipeline. Isso inclui a exibição do nome do Pipeline (somente pipeline de não produção) e do Tipo e um selo para indicar se o status do pipeline está Em andamento/Cancelado/Com falha.
* O processo usado para gerar senhas git tornou-se mais resiliente a problemas na camada de serviço subjacente.

## Correções de erros {#bug-fixes}

* Os dados de monitorização podem, por vezes, ser apresentados de forma incorreta ou não ser apresentados de forma alguma com base em variações menores de valores técnicos.
* A configuração Maven usada no container build foi atualizada para evitar bloqueios ao baixar metadados de artefato.
* Ocasionalmente, o processo de teste de desempenho do Assets não conseguia descriptografar a senha do AEM, causando falha no teste.
* Determinadas topologias com instâncias stand-by podem ter falsos negativos em testes de segurança.
* Se o ambiente stage contivesse uma instância interrompida, a etapa de teste de segurança às vezes falharia.
* As notificações da Experience Cloud não foram recebidas de forma consistente.

