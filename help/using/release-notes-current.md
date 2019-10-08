---
title: Notas de versão para 2019.10.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.10.0
description: Siga esta página para obter informações sobre a versão 2019.10.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.10.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: de9d2834ffa6c235e580227bd020fb8a0b94d22c

---

# Notas de versão para 2019.10.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.10.0 atualiza os critérios de teste de segurança, adiciona gráficos de monitoramento disponíveis para download e corrige alguns problemas de usabilidade relatados pelo cliente.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.10.0 é 12 de outubro de 2019.

## Novidades {#whats-new}

* Partes significativas das etapas de implantação tornaram-se mais eficientes.
* Quando apropriado, a versão do projeto build Maven agora incorporará a versão do projeto em git.
* No momento da criação, novas variáveis de ambiente estão disponíveis.
* Os Pipelines de não produção podem ser excluídos do cartão na página Visão geral, bem como na API.
* Há uma nova etapa de aprovação opcional imediatamente após a etapa de implantação da etapa, mas antes da etapa de teste de segurança.
* Ao configurar um pipeline de CI/CD, a desconexão e a anexação de instâncias de dispatcher do balanceador de carga podem ser ignoradas para ambientes dev e stage.
* A CLI do Gerenciador de nuvem foi aumentada para oferecer suporte ao acesso aos registros de etapas de execução.
* A API do Gerenciador de nuvem agora oferece suporte à edição da ramificação configurada de um pipeline.
* As solicitações executadas durante o teste de desempenho agora incluem um token específico ("CloudManagerTest") no agente do usuário.

## Correções de erros {#bug-fixes}

* Alguns cartões na página Visão geral não estavam alinhados verticalmente corretamente.
* Algumas condições de falha não faziam com que as execuções de pipeline fossem marcadas corretamente e evitavam execuções subsequentes.
