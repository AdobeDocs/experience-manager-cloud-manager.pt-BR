---
title: Principais conceitos
seo-title: Principais conceitos
description: Esta página lista os termos principais associados ao Cloud Manager.
seo-description: Siga esta página para entender os termos principais associados ao Cloud Manager.
uuid: 2 a 37810 b -98 f 8-4 f 01-90 de -1 e 52 c 754 ad 16
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introdução
discoiquuid: b 702 dfc 0-3534-4 d 90-af 19-8559 d 8 baf 6 a 6
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Principais conceitos {#key-concepts}

Esta página descreve uma terminologia básica usada no Experience Cloud Manager. Recomendamos que você leia essa página antes de revisar o restante da documentação do Gerenciador de nuvem.

**Aplicativo** O conjunto de personalizações e configurações criadas por um cliente (ou seu personalizador) para adaptar a solução subjacente para casos de uso e necessidades específicos. Um aplicativo é uma unidade lógica que pode ser composta por vários artefatos.

Por exemplo *, We. Retail*.

**Artefato** Uma unidade implantável. O resultado de um processo de compilação que transforma o código fonte em uma única unidade. Por exemplo, um arquivo Zip que contém o código-fonte.

**Local de armazenamento do Artefato** A no local em que artefatos específicos do cliente são salvos e protegidos.

**Ambiente** Um único cluster de máquinas virtuais em um programa. Para o AEM, isso é composto por uma instância do autor (opcionalmente com uma instância de autor de aguardulação fria adicional), uma ou mais instâncias de publicação, uma ou mais instâncias do dispatcher e um balanceador de carga.

**Local do Repositório** de Git Em que o código fonte específico do cliente é armazenado, acessível usando o protocolo Git.

**Instância** Um servidor virtual específico executando a solução AEM. Instâncias representam uma unidade lógica única a partir de uma perspectiva de implantação.

**Organização da** Adobe que representa a representação de um cliente do Enterprise. Uma empresa pode ter várias organizações dependendo de como eles foram provisionados originalmente no Sistema de gerenciamento de identidade da Adobe.

**Pipeline** Um conjunto de etapas de implantação que são executadas em sequência.

**Produto** Um conjunto específico de funcionalidades em uma solução licenciada por uma organização. Diferentes programas dentro de uma organização podem ser atribuídos a diferentes conjuntos de produtos. Por exemplo, Sites, Ativos do Forms.

**Programa** Um conjunto de ambientes que suporta um agrupamento lógico das iniciativas do cliente, geralmente correspondendo a um SLA (Serviço de nível de serviço) adquirido. Cada programa tem exatamente um ambiente de produção e pode ter muitos ambientes de não produção.

**Solução** Uma [!UICONTROL Experience Cloud] das soluções da Adobe. Por exemplo, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

**Etapa** Um conjunto de instruções configurado que executa uma certa unidade de trabalho, construção de bloco de um pipeline.
