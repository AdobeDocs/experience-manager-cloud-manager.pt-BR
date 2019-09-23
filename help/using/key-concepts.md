---
title: Principais conceitos
seo-title: Principais conceitos
description: Esta página lista os termos principais associados ao Cloud Manager.
seo-description: Siga esta página para entender os termos principais associados ao Cloud Manager.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introdução
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
translation-type: tm+mt
source-git-commit: aa4ff4eb2f3292fe4cb0baf8087b4d0213443cf4

---


# Principais conceitos {#key-concepts}

Esta página descreve algumas terminologias básicas usadas no Cloud Manager. Recomendamos que você leia esta página antes de consultar o restante da documentação do Cloud Manager.

**Aplicativo** O conjunto de personalizações e configurações criadas por um cliente (ou seu personalizador) para adaptar a solução subjacente aos casos e necessidades de uso específicos. Um aplicativo é uma unidade lógica que pode ser composta de vários artefatos.

Por exemplo, *We.Retail*.

**Artefato** Uma unidade implantável. O resultado de algum processo de compilação que transforma o código fonte em uma única unidade. Por exemplo, um arquivo Zip contendo o código-fonte.

**Repositório** de artefatos Um local de armazenamento onde artefatos específicos do cliente são salvos e protegidos.

**Ambiente** Um único cluster de máquinas virtuais dentro de um programa. Para o AEM, ele é composto de uma instância do autor (opcionalmente com uma instância adicional de autor em espera), zero ou mais instâncias de publicação, uma ou mais instâncias do dispatcher e um balanceador de carga.

**Repositório** Git Um local onde o código fonte específico do cliente é armazenado, acessível usando o protocolo Git.

**Instância** Um servidor virtual específico que executa a solução AEM. As instâncias representam uma única unidade lógica de uma perspectiva de implantação.

**Construção da Adobe da organização** que representa um cliente Enterprise. Uma empresa pode ter várias organizações, dependendo de como elas foram originalmente provisionadas no Sistema de Gerenciamento de Identidades da Adobe.

**Pipeline** Um conjunto de etapas de implantação executadas em sequência.

**Produto** Um conjunto específico de funcionalidades em uma solução licenciada por uma organização. Diferentes programas dentro de uma organização podem ter direito a diferentes conjuntos de produtos. Por exemplo, Sites, Ativos de formulários.

**Programa** Um conjunto de ambientes que oferecem suporte a um agrupamento lógico de iniciativas de clientes, geralmente correspondente a um SLA (Service Level Agreements, contratos de nível de serviço) adquirido. Cada programa tem exatamente um ambiente de produção e pode ter muitos ambientes que não sejam de produção.

**Solução** Uma das [!UICONTROL Experience Cloud] soluções da Adobe. Por exemplo, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

**Etapa** Um conjunto de instruções configurado que realiza alguma unidade de trabalho, bloco de construção de um pipeline.
