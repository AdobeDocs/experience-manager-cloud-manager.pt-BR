---
title: Principais conceitos
seo-title: Principais conceitos
description: Esta página lista os termos principais associados ao Cloud Manager.
seo-description: Siga esta página para entender os termos principais associados ao Cloud Manager.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 1%

---


# Principais conceitos {#key-concepts}

Esta página descreve algumas terminologias básicas usadas no Cloud Manager. Recomendamos que você leia esta página antes de revisar o restante da documentação do Cloud Manager.

**** AplicativoO conjunto de personalizações e configurações criadas por um cliente para adaptar a solução subjacente aos casos e necessidades de uso específicos. Um aplicativo é uma unidade lógica que pode ser composta de vários artefatos.

Por exemplo, *We.Retail*.

**** ArtefatoUma unidade implantável. O resultado de algum processo de compilação que transforma o código fonte em uma única unidade. Por exemplo, um arquivo Zip contendo o código-fonte.

**Repositório** de artefatosUm local de armazenamento onde artefatos específicos do cliente são salvos e protegidos.

**** AmbienteUm único cluster de máquinas virtuais em um programa. Para AEM, é composto por uma instância do autor (opcionalmente com uma instância adicional de autor em espera), zero ou mais instâncias de publicação, uma ou mais instâncias do dispatcher e um balanceador de carga.

**Repositório** de GitUm local onde o código fonte específico do cliente é armazenado, acessível usando o protocolo Git.

**** InstânciaUm servidor virtual específico executando a solução AEM. As instâncias representam uma única unidade lógica de uma perspectiva de implantação.

**Construção** OrganizationAdobe representando um cliente Enterprise. Uma empresa pode ter várias organizações, dependendo de como elas foram originalmente provisionadas no Adobe System.

**** PipelineUm conjunto de etapas de implantação executadas em sequência.

**** ProdutoUm conjunto específico de funcionalidades em uma solução licenciada por uma organização. Diferentes programas dentro de uma organização podem ter direito a diferentes conjuntos de produtos. Por exemplo, Sites, Ativos do Forms.

**** ProgramaUm conjunto de ambientes que oferecem suporte a um agrupamento lógico de iniciativas de clientes, geralmente correspondente a um SLA (Service Level Agreements, contratos de nível de serviço) adquirido. Cada programa tem exatamente um ambiente de produção e pode ter muitos ambientes que não são de produção.

**** SoluçãoUma das  [!UICONTROL Experience Cloud] soluções Adobe. Por exemplo, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

**** EtapaUm conjunto de instruções configurado que realiza alguma unidade de trabalho, bloco de construção de um pipeline.
