---
title: Notas de versão para 2019.10.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.10.0
description: Siga esta página para obter informações sobre a versão 2019.10.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.10.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 1e927076e6bc84e8e1761e33a86cff61a3be0d2f

---

# Notas de versão para 2019.10.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] versão 2018.10.0 e adiciona atualizações às etapas de implantação e ao manuseio da versão do projeto inteligente.
Siga a página abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.10.0 é 12 de outubro de 2019.

## Novidades {#whats-new}

* Partes significativas das etapas de implantação tornaram-se mais eficientes.
* Quando apropriado, a versão do projeto build Maven agora incorporará a versão do projeto em git.
* No momento da criação, novas variáveis de ambiente estão disponíveis.
* Os Pipelines de não produção podem ser excluídos do cartão na página Visão geral, bem como na API.
* Há uma nova etapa de aprovação opcional imediatamente após a etapa de implantação da etapa, mas antes da etapa de teste de segurança.
* Ao configurar um pipeline de CI/CD, a desconexão e a anexação de instâncias de dispatcher do balanceador de carga podem ser ignoradas para ambientes dev e stage.
Consulte o Processo **[](deploying-code.md#deployment-process)** de implantação para obter mais detalhes.
* A CLI do Gerenciador de nuvem foi aumentada para oferecer suporte ao acesso aos registros de etapas de execução.
* A API do Gerenciador de nuvem agora oferece suporte à edição da ramificação configurada de um pipeline.
* As solicitações executadas durante o teste de desempenho agora incluem um token específico ***CloudManagerTest*** no agente do usuário.

## Correções de erros {#bug-fixes}

* Alguns cartões na página **Visão geral** não estavam alinhados verticalmente corretamente.
* Algumas condições de falha não faziam com que as execuções de pipeline fossem marcadas corretamente e evitavam execuções subsequentes.
