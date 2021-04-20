---
title: Notas da versão 2019.4.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.4.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.4.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.4.0.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 7%

---


# Notas da versão 2019.4.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.4.0 não contém alterações funcionais significativas. Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A Data de lançamento da versão [!UICONTROL Cloud Manager] 2019.4.0 é 18 de abril de 2019.

## Novidades {#whats-new}

* A interface do usuário do Cloud Manager agora está disponível em inglês, francês, alemão e japonês.
* As etapas de implantação agora contêm o processo em execução, ou seja, quando um backup é executado, os pacotes estão sendo instalados e os balanceadores de carga estão sendo reconfigurados

## Correções de erros {#bug-fixes}

* A abordagem de implantação usada para alterações do Dispatcher foi aprimorada para lidar com casos de uso adicionais.
* Alguns tipos de tamanho de instância não eram exibidos corretamente na página Ambientes .
* As regras de qualidade do código CQBP-84-dependencies produziram falsos positivos para bibliotecas Adobe incorporadas, como Componentes principais do WCM e Compartilhamento de ativos Commons.
* O botão de detalhes da etapa de verificação de código foi ativado quando os detalhes estavam indisponíveis.
* A mensagem de erro ao especificar um valor inválido para exibições de página por minuto KPI tinha o limite inferior errado.
* A categoria de implantação em um pipeline de não produção foi capitalizada incorretamente.
* A chamada para o cartão de ação na página **Visão Geral** tinha texto incorreto quando o repositório Git não estava configurado corretamente.

## Problemas conhecidos {#known-issues}

* Os valores de SLA podem ser arredondados incorretamente.
