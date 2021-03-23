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
feature: Introdução
level: Iniciante
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 2%

---


# Principais conceitos {#key-concepts}

Esta página descreve algumas terminologias básicas usadas no Cloud Manager. Recomendamos que você leia esta página antes de revisar o restante da documentação do Cloud Manager.

**** AplicativoO conjunto de personalizações e configurações criadas por um cliente para adaptar a solução subjacente para seus casos de uso e necessidades específicas. Uma aplicação é uma unidade lógica que pode ser composta por vários artefatos.

Por exemplo, *We.Retail*.

**** ArtefatoUma unidade implantável. O resultado de algum processo de build que transforma o código fonte em uma única unidade. Por exemplo, um arquivo Zip contendo o código-fonte.

**Repositório** de artefatos Um local de armazenamento onde artefatos específicos do cliente são salvos e protegidos.

**** AmbienteUm único cluster de máquinas virtuais em um programa. Para AEM, é composto por uma instância de autor (opcionalmente com uma instância adicional de autor de standby), zero ou mais instâncias de publicação, uma ou mais instâncias de dispatcher e um balanceador de carga.

**** Repositório GitUm local onde o código-fonte específico do cliente é armazenado, acessível por meio do protocolo Git.

**** Instância: um servidor virtual específico que executa a solução de AEM. As instâncias representam uma única unidade lógica de uma perspectiva de implantação.

**** OrganizaçãoConstrução da Adobe que representa um cliente Enterprise. Uma empresa pode ter várias organizações dependendo de como elas foram originalmente provisionadas no Adobe Identity Management System.

**** PipelineUm conjunto de etapas de implantação que são executadas em sequência.

**** Produto Um conjunto específico de funcionalidades em uma solução licenciada por uma organização. Os diferentes programas de uma organização podem ter direito a diferentes conjuntos de produtos. Por exemplo, Sites, Ativos da Forms.

**** ProgramaUm conjunto de ambientes que oferecem suporte a um agrupamento lógico de iniciativas de clientes, geralmente correspondendo a um SLA (Service Level Agreements, contratos de nível de serviço) adquirido. Cada programa tem exatamente um ambiente de produção e pode ter muitos ambientes não relacionados à produção.

**** SoluçãoUma das  [!UICONTROL Experience Cloud] soluções do Adobe. Por exemplo, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

**** EtapaUm conjunto de instruções configurado que realiza alguma unidade de trabalho, bloco de construção de um pipeline.
