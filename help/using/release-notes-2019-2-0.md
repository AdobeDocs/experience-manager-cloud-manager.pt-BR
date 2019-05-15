---
title: Notas de versão de 2019.2.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2019.2.0
description: Siga esta página para obter informações sobre a versão 2019.2.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2019.2.0 do Gerenciador de AEM Cloud.
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de versão de 2019.2.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.2.0 adiciona um novo recurso de Monitoramento de sistema. Isso permite que os clientes visualizem o estado dos ambientes dos Adobe Managed Services em nível de sistema.


## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2019.2.0 é February 1 de fevereiro de 21 19.

## Novidades {#whats-new}

* Novo recurso de Monitoramento do sistema. Consulte [Monitorar seus ambientes](monitor-your-environments.md) para saber mais.
* O módulo do dispatcher em projetos gerados pelo assistente agora contém um arquivo README.
* A ordem de classificação de problemas de leitura de código foi aprimorada para corresponder à prioridade do problema.
* As instâncias do palco agora são restauradas sempre para o balanceador de carga, mesmo no caso de uma falha de implantação.
* Uma nova função de desenvolvedor de API está disponível no Admin Console, permitindo que usuários específicos tenham permissão para criar integrações no console da Adobe I/O. Consulte [Gerenciar desenvolvedores](https://www.adobe.com/go/aac_api_prod_learn) para saber mais.
* A versão do arquivo Maven Archetype foi atualizada para a versão 16.
* A versão de Maven foi atualizada para a versão 3.6.0.

## Correções de erros {#bug-fixes}

* Em algumas circunstâncias, os pipeline não eram executados quando o ambiente de destino era hospedado no Azure.
* A ordenação de ambientes era inconsistente.
* O teste de desempenho pode falhar quando os caminhos de página encontrados contiverem um caractere de vírgula.
* Quando uma execução de pipeline era iniciada na interface do usuário da Web, o botão Voltar do navegador não funcionava corretamente.
* Os links Saiba mais na página Visão geral não abriram uma nova guia.
* Ao carregar uma miniatura do programa, pode não estar imediatamente visível.
* Em alguns casos, a Digitalização de código falhou devido à configuração específica do projeto.
* O link Saiba mais no cartão de Pipeline de não produção foi para o local errado.
* Quando um portfólio de qualidade foi substituído, o status era exibido inconsistentemente.
* Os clientes que usam topologias de standby frio recebiam resultados incorretos para testes de segurança.
* Ao criar um novo projeto usando o assistente, não era possível criar uma ramificação contendo o caractere traço.

## Problemas conhecidos {#known-issues}

* Quando os dados de monitoramento são atualizados, qualquer série oculta fica inativa.
* Os clientes que quiserem visualizar seus relatórios SLA existentes precisam navegar manualmente até a próxima versão.

   Para definir esse URL, siga o padrão (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`), por exemplo, se o URL da Experience Cloud for (`https://weretailprod.experiencecloud.adobe.com`), então o URL dos relatórios SLA é (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Espera-se que isso seja resolvido na próxima versão com a disponibilidade dos relatórios SLA dentro [!UICONTROL Cloud Manager].
