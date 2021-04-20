---
title: Notas da versão 2019.1.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.1.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.1.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.1.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Release Information
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 4%

---


# Notas da versão 2019.1.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.9.0 adiciona suporte a programas AEM Assets de teste, bem como tipos de pipeline adicionais que executam as etapas de criação e qualidade de código, implantando opcionalmente em um ambiente de não produção.

## Data de lançamento {#release-date}

A Data de lançamento da versão [!UICONTROL Cloud Manager] 2019.1.0 é 17 de janeiro de 2019.

## Novidades {#whats-new}

* Adição de suporte para teste de desempenho do AEM Assets. Consulte Configurar o [CI/CD Pipeline](configuring-pipeline.md)para obter mais detalhes.
* Adição de suporte para pipelines que executam apenas etapas de criação e qualidade de código e pipelines que são implantados em ambientes não relacionados à produção. Consulte a seção **Pipelines de não produção e qualidade de código somente** em [Configurar o pipeline de CI/CD](configuring-pipeline.md) para obter mais detalhes.
* Adição de suporte para variáveis de ambiente personalizadas no ambiente de criação.
* Para clientes com vários ambientes de estágio ou de produção, a seleção do ambiente para o qual será implantado como parte do pipeline de produção está disponível na página [Configure seu pipeline de CI/CD](configuring-pipeline.md) .
* httxt2dbm foi adicionado ao contêiner de criação.
* Todos os itens do menu de ajuda abrem uma nova guia.

## Correções de erros {#bug-fixes}

* Ao editar um programa, foi possível desmarcar todos os conjuntos de páginas.
* A etapa de aprovação foi intitulada incorretamente.
* Em algumas situações, o logotipo do programa era correspondido incorretamente.
* Se apenas o pacote de configuração do dispatcher fosse criado, a etapa de implantação falharia.
* Os ambientes que continham instâncias de espera passiva não eram tratados corretamente.
* Alguns programas terminados apareceram no alternador de programas.
* Se uma nova ramificação foi adicionada ao repositório Git enquanto o pipeline estava sendo editado, ela pode não ter sido imediatamente selecionável.
* Em algumas telas, o ícone do Developer Connection no menu Ajuda não estava visível.
* A tecla tab não foi manipulada corretamente na caixa de diálogo de configuração de liberação do dispatcher.

## Problemas conhecidos {#known-issues}

* Ao abrir um programa que tem Sites, mas não Ativos, KPIs definidos, todos os usuários veem uma chamada para cartão de ação com um botão **Programa de instalação**. No entanto, somente os usuários na função Proprietário comercial podem clicar no botão **Programa de instalação**.