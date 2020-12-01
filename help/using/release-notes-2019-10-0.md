---
title: Notas da versão 2019.10.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.10.0
description: Siga esta página para obter informações sobre a versão 2019.10.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.10.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 52c54568d8ab7b5091c25b3b65b4baa126bf61f5
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 4%

---

# Notas da versão 2019.10.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2019.10.0 e adiciona atualizações às etapas de implantação e ao gerenciamento de versões de projetos inteligentes.
Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A data de lançamento da versão [!UICONTROL Cloud Manager] 2019.10.0 é 10 de outubro de 2019.

## Novidades {#whats-new}

* Partes significativas das etapas de implantação tornaram-se mais eficientes.
* Quando apropriado, a versão do projeto Construir Maven agora incorporará a versão do projeto em git.
* No momento da criação, novas variáveis de ambiente estão disponíveis.
* Os Pipelines de não produção podem ser excluídos do cartão na página **Visão geral**, bem como na API.
* Há uma nova etapa de aprovação opcional imediatamente após a etapa de implantação da etapa, mas antes da etapa de teste de segurança.
* Ao configurar um pipeline CI/CD, a desanexação e a anexação de instâncias do dispatcher do balanceador de carga podem ser ignoradas para ambientes dev e stage.
Consulte **[Processo de implantação](deploying-code.md#deployment-process)** para obter mais detalhes.
* A CLI do Gerenciador de nuvem foi aumentada para oferecer suporte ao acesso aos registros de etapas de execução.
* A API do Gerenciador de nuvem agora oferece suporte à edição da ramificação configurada de um pipeline.
* As solicitações executadas durante o teste de desempenho agora incluem um token específico ***CloudManagerTest*** no agente do usuário.

## Correções de erros {#bug-fixes}

* Alguns dos cartões na página **Visão geral** não estavam alinhados verticalmente corretamente.
* Determinadas condições de falha não faziam com que execuções de pipeline fossem marcadas corretamente e evitavam execuções subsequentes.
