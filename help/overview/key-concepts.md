---
title: Principais conceitos
description: Como qualquer ferramenta avançada, o Cloud Manager contém muitos conceitos e termos. Este documento resume alguns dos mais importantes para se começar a usar o Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 75baacd1fd6f36ca1d6ea5c1993516569ab6ef47
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 95%

---


# Principais conceitos {#key-concepts}

Como qualquer ferramenta avançada, o Cloud Manager contém muitos conceitos e termos. Este documento resume alguns dos mais importantes para se começar a usar o Cloud Manager.

## Aplicativo {#application}

Aplicativo é o conjunto de personalizações e configurações criadas por um(a) cliente para adaptar a [solução](#solution) subjacente (como o AEM Sites ou o AEM Assets) para casos de uso e necessidades específicos. Um aplicativo é uma unidade lógica que pode ser composta por vários [artefatos](#artifact).

Um exemplo é o fictício [aplicativo de estilo de vida WKND](https://experienceleague.adobe.com/pt-br/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview).

## Artefato {#artifact}

Um artefato é uma unidade implantável e o resultado de um processo de build que transforma o código-fonte em uma só unidade. Por exemplo, um arquivo .zip que contém o código-fonte.

## Repositório de artefatos {#artifact-repository}

Um repositório de artefatos é um local onde [artefatos](#artifact) específicos do cliente são salvos e armazenados.

## Ambiente {#environment}

Um ambiente é um mesmo grupo de máquinas virtuais dentro de um [programa](#program). Para o AEM, esse ambiente é composto por uma instância de criação (opcionalmente com uma instância de criação adicional em espera), zero ou mais instâncias de publicação, uma ou mais instâncias do Dispatcher e um balanceador de carga.

## Repositório Git {#git-repository}

Um repositório Git é um local onde o código-fonte específico do cliente é armazenado e fica acessível [por meio do Git](https://git-scm.com).

## Instância {#instance}

Uma instância é um servidor virtual específico que executa a [solução](#solution) do AEM. As instâncias representam uma unidade lógica do ponto de vista da implantação.

## Organização {#organization}

Uma organização é uma construção da Adobe que representa um cliente corporativo. Uma empresa pode ter várias organizações dependendo de como elas são provisionadas no Identity Management System (IMS) da Adobe.

## Pipeline {#pipeline}

Um pipeline é um conjunto de etapas de implantação executadas em sequência.

## Produto {#product}

Um produto é um conjunto específico de funcionalidades dentro de uma [solução](#solution) licenciada por uma organização. Diferentes [programas](#program) em uma organização podem ter direito a diferentes conjuntos de produtos, por exemplo, AEM Sites, AEM Assets ou AEM Forms.

## Programa {#program}

Um programa é um conjunto de ambientes que aceitam um agrupamento lógico de iniciativas do cliente, geralmente correspondendo a um contrato de nível de serviço (SLA) adquirido. Cada programa tem exatamente um ambiente de produção e pode ter muitos ambientes de não produção.

## Solução {#solution}

Uma solução é uma das soluções da Adobe [!UICONTROL Experience Cloud]. Por exemplo, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

## Etapa {#step}

Uma etapa é um conjunto de instruções configurado que realiza uma unidade de trabalho como um bloco de construção de um [pipeline](#pipeline).
