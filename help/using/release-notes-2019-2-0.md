---
title: Notas de versão para 2019.2.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.2.0
description: Siga esta página para obter informações sobre a versão 2019.2.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.2.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 98395c4413b1b6bfbb3a565388ffa32dc3880dff

---


# Notas de versão para 2019.2.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.2.0 adiciona um novo recurso de Monitoramento do sistema. Isso permite que os clientes visualizem o estado de seus ambientes Adobe Managed Services em um nível de sistema.


## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.2.0 é 21 de fevereiro de 2019.

## Novidades {#whats-new}

* Novo recurso de monitoramento de sistema. Consulte [Monitorar seus ambientes](monitor-your-environments.md) para saber mais.
* O módulo dispatcher em projetos gerados por assistente agora contém um arquivo README.
* A ordenação de problemas de digitalização de código foi aprimorada para corresponder à prioridade do problema.
* As instâncias de estágio agora são sempre restauradas para o balanceador de carga mesmo no caso de uma falha de implantação.
* Uma nova função de desenvolvedor de API está disponível no Admin Console, que permite que usuários específicos recebam a permissão para criar integrações no console de E/S da Adobe. Consulte [Gerenciar desenvolvedores](https://www.adobe.com/go/aac_api_prod_learn) para saber mais.
* A versão do Maven Archetype foi atualizada para a versão 16.
* A versão do Maven foi atualizada para a versão 3.6.0.

## Correções de erros {#bug-fixes}

* Em algumas circunstâncias, os pipelines não seriam executados quando o ambiente de destino era hospedado no Azure.
* A ordenação de ambientes era inconsistente.
* O teste de desempenho pode falhar quando os caminhos de página detectados continham um caractere vírgula.
* Quando uma execução de pipeline foi iniciada a partir da interface do usuário da Web, o botão Voltar do navegador não funcionava corretamente.
* Os links Saiba mais na página Visão geral não abriram uma nova guia.
* Ao carregar uma miniatura de programa, ela pode não ter sido imediatamente visível.
* Em alguns casos, a verificação de código falhou devido à configuração específica do projeto.
* O link Learn More (Saiba mais) no cartão Non-Production Pipelines foi para o local errado.
* Quando uma porta de qualidade era substituída, o status era exibido de forma inconsistente.
* Os clientes que usam topologias de espera frias receberam resultados incorretos para testes de segurança.
* Ao criar um novo projeto usando o assistente, não foi possível criar uma ramificação contendo o caractere traço.

## Problemas conhecidos {#known-issues}

* Quando os dados de monitoramento são atualizados, qualquer série oculta fica oculta.
* Os clientes que desejarem visualizar seus relatórios de SLA existentes precisarão navegar manualmente até a próxima versão.

   Para formular esse URL, siga o padrão (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`), por exemplo, se o URL da Experience Cloud for (`https://weretailprod.experiencecloud.adobe.com`), o URL do relatório do SLA será (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Isso deve ser resolvido na próxima versão com a disponibilidade de relatórios de SLA dentro [!UICONTROL Cloud Manager].
