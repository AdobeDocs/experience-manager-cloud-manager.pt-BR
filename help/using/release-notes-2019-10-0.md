---
title: Notas da versão 2019.10.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.10.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.10.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.10.0.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 5%

---

# Notas da versão 2019.10.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2019.10.0 e adiciona atualizações às etapas de implantação e ao manuseio da versão do projeto maven.
Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A Data de lançamento da versão [!UICONTROL Cloud Manager] 2019.10.0 é 10 de outubro de 2019.

## Novidades {#whats-new}

* Partes significativas das etapas de implantação tiveram um desempenho maior.
* Quando apropriado, a versão do projeto build Maven agora incorporará a versão do projeto no git.
* No momento da criação, novas variáveis de ambiente estão disponíveis.
* Os pipeline de não produção podem ser excluídos do cartão na página **Visão geral** , bem como na API.
* Há uma nova etapa de aprovação opcional imediatamente após a etapa de implantação do estágio, mas antes da etapa de teste de segurança.
* Ao configurar um pipeline de CI/CD, a desconexão e a anexação de instâncias do dispatcher do balanceador de carga podem ser ignoradas para ambientes de desenvolvimento e de preparo.
Consulte **[Processo de Implantação](deploying-code.md#deployment-process)** para obter mais detalhes.
* A CLI do Cloud Manager foi aumentada para oferecer suporte ao acesso a logs de etapas de execução.
* A API do Cloud Manager agora é compatível com a edição da ramificação configurada de um pipeline.
* As solicitações executadas durante o teste de desempenho agora incluem um token específico ***CloudManagerTest*** no agente do usuário.

## Correções de erros {#bug-fixes}

* Alguns dos cartões na página **Visão geral** não estavam alinhados verticalmente corretamente.
* Determinadas condições de falha não faziam com que as execuções de pipeline fossem marcadas corretamente e impediam execuções subsequentes.
