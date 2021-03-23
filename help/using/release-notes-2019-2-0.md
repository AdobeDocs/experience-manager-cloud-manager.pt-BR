---
title: Notas da versão 2019.2.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.2.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.2.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.2.0.
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 4%

---


# Notas da versão 2019.2.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.2.0 adiciona um novo recurso de Monitoramento de Sistema. Isso permite que os clientes visualizem o estado de seus ambientes do Adobe Managed Services em um nível de sistema.


## Data de lançamento {#release-date}

A Data de lançamento da versão [!UICONTROL Cloud Manager] 2019.2.0 é 21 de fevereiro de 2019.

## Novidades {#whats-new}

* Novo recurso de Monitoramento de sistema. Consulte [Monitorar os ambientes](monitor-your-environments.md) para saber mais.
* O módulo Dispatcher em projetos gerados por assistente agora contém um arquivo README.
* A ordem de classificação dos problemas de Varredura de código foi aprimorada para corresponder à prioridade do problema.
* Agora, as instâncias de preparo são sempre restauradas para o balanceador de carga mesmo no caso de uma falha de implantação.
* Uma nova função de Desenvolvedor de API está disponível no Admin Console, que permite que usuários específicos recebam permissão para criar integrações no console do Adobe I/O. Consulte [Gerenciar desenvolvedores](https://www.adobe.com/go/aac_api_prod_learn) para saber mais.
* A versão do Arquétipo Maven foi atualizada para a versão 16.
* A versão do Maven foi atualizada para a versão 3.6.0.

## Correções de erros {#bug-fixes}

* Em algumas circunstâncias, os pipelines não seriam executados quando o ambiente de destino era hospedado no Azure.
* A ordenação de ambientes era inconsistente.
* O teste de desempenho pode falhar quando os caminhos de página descobertos continham um caractere vírgula.
* Quando uma execução de pipeline era iniciada a partir da interface do usuário da Web, o botão Voltar do navegador não funcionava corretamente.
* Os links Saiba mais na página Visão geral não abriram uma nova guia.
* Ao carregar uma miniatura de programa, ela pode não ter sido imediatamente visível.
* Em alguns casos, a Verificação de código falhou devido à configuração específica do projeto.
* O link Saiba mais no cartão Pipelines de não produção foi para o local errado.
* Quando uma porta de qualidade era substituída, o status era exibido de forma inconsistente.
* Os clientes que usavam topologias de standby frio receberam resultados incorretos para testes de segurança.
* Ao criar um novo projeto usando o assistente, não foi possível criar uma ramificação contendo o caractere traço.

## Problemas conhecidos {#known-issues}

* Quando os dados de monitoramento são atualizados, qualquer série oculta fica oculta.
* Os clientes que desejarem visualizar seus relatórios de SLA existentes precisarão navegar manualmente até a próxima versão.

   Para formular esse URL, siga o padrão (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`), por exemplo, se o URL do seu Experience Cloud for (`https://weretailprod.experiencecloud.adobe.com`), o URL do seu SLA relata ser (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Isso deve ser resolvido na próxima versão com a disponibilidade dos relatórios de SLA dentro de [!UICONTROL Cloud Manager].
