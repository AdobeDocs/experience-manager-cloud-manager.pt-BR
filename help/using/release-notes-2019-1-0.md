---
title: Notas da versão 2019.1.0
seo-title: AEM Cloud Manager Release Notes for 2019.1.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.1.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.1.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Release Information
exl-id: 383ca5a0-4b0b-48e9-aa48-1d1388875329
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 4%

---

# Notas da versão 2019.1.0 {#release-notes-for}

O [!UICONTROL Cloud Manager] A versão 2018.9.0 adiciona suporte a testes de programas AEM Assets, bem como tipos de pipeline adicionais que executam as etapas de criação e qualidade de código, implantando opcionalmente em um ambiente não relacionado à produção.

## Data de lançamento {#release-date}

A data de lançamento para [!UICONTROL Cloud Manager] A versão 2019.1.0 é 17 de janeiro de 2019.

## Novidades {#whats-new}

* Adição de suporte para teste de desempenho do AEM Assets. Consulte o documento [Configurar pipeline de produção](configuring-production-pipelines.md) para saber mais.
* Adição de suporte para pipelines que executam apenas etapas de criação e qualidade de código e pipelines que são implantados em ambientes não relacionados à produção. Consulte o documento [Configurar pipeline de não produção](configuring-non-production-pipelines.md) para saber mais.
* Adição de suporte para variáveis de ambiente personalizadas no ambiente de criação.
* Para clientes com vários ambientes de estágio ou produção, a seleção de qual ambiente será implantado como parte do pipeline de produção está disponível. Consulte o documento [Configurar pipeline de produção](configuring-production-pipelines.md) para saber mais.
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

* Ao abrir um programa que tem Sites, mas não Ativos, KPIs definidos, todos os usuários veem uma chamada para cartão de ação com um **Programa de configuração** botão. No entanto, somente usuários na função Proprietário comercial podem clicar no **Programa de configuração** botão.
