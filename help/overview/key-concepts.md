---
title: Principais conceitos
description: Como todas as ferramentas poderosas, o Cloud Manager abrange muitos conceitos e termos. Este documento resume alguns dos mais importantes para você, ao começar a usar o Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 73e322cf93dc7709b7581860974079c8d94034ba
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 4%

---


# Principais conceitos {#key-concepts}

Como todas as ferramentas poderosas, o Cloud Manager abrange muitos conceitos e termos. Este documento resume alguns dos mais importantes para você, ao começar a usar o Cloud Manager.

## Aplicativo {#application}

E aplicativo é o conjunto de personalizações e configurações criadas por um cliente para adaptar a [solução](#solution) (como AEM Sites ou AEM Assets) para seus casos de uso e necessidades específicas. Um aplicativo é uma unidade lógica que pode ser composta por vários [artefatos.](#artifact)

Um exemplo de aplicativo é o ficcional [Aplicativo de estilo de vida WKND.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=pt-BR)

## Artefato {#artifact}

Um artefato é uma unidade implantável e é o resultado de algum processo de compilação que transforma o código fonte em uma única unidade. Por exemplo, um arquivo .zip contendo o código-fonte.

## Repositório de artefatos {#artifact-repository}

Um repositório de artefatos é um local de armazenamento onde o cliente específico [artefatos](#artifact) são salvas e seguras.

## Autor {#environment}

Um ambiente é um único cluster de máquinas virtuais em um [programa.](#program) Para AEM, é composto por uma instância de criação (opcionalmente com uma instância de criação adicional de standby frio), zero ou mais instâncias de publicação, uma ou mais instâncias do dispatcher e um balanceador de carga.

## repositório Git {#git-repository}

Um repositório Git é um local onde o código-fonte específico do cliente é armazenado e acessível [usando git.](https://git-scm.com)

## Instância {#instance}

Uma instância é um servidor virtual específico que executa o AEM [solução.](#solution) As instâncias representam uma única unidade lógica de uma perspectiva de implantação.

## Organização {#organization}

Uma organização é uma construção de Adobe que representa um cliente corporativo. Uma empresa pode ter várias organizações dependendo de como elas foram provisionadas no Sistema Identity Management (IMS).

## Pipeline {#pipeline}

Um pipeline é um conjunto de etapas de implantação que são executadas em sequência.

## Produto {#product}

Um produto é um conjunto específico de funcionalidades dentro de um [solução](#solution) licenciado por uma organização. Different [programas](#program) em uma organização pode ter direito a diferentes conjuntos de produtos, por exemplo, AEM Sites, AEM Assets ou AEM Forms.

## Programa {#program}

Um programa é um conjunto de ambientes que oferecem suporte a um agrupamento lógico de iniciativas de clientes, geralmente correspondendo a um SLA (Service Level Agreements, contratos de nível de serviço) adquirido. Cada programa tem exatamente um ambiente de produção e pode ter muitos ambientes não relacionados à produção.

## Solução {#solution}

Uma solução é um dos Adobe [!UICONTROL Experience Cloud] soluções. Por exemplo, Adobe Experience Manager, Adobe Target ou Adobe Analytics.

## Etapa {#step}

Uma etapa é um conjunto de instruções configurado que realiza alguma unidade de trabalho como um bloco de construção de um [pipeline.](#pipeline)
