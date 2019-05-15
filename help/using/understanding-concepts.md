---
title: Entendendo os conceitos antes de usar o Experience Cloud Manager
seo-title: Entendendo os conceitos antes de usar o Experience Cloud Manager
description: 'null'
seo-description: 'null'
page-status-flag: nunca ativado
uuid: 55 cc 551 a-e 812-4102-96 c 8-13 d 2 cdd 79 c 84
contentOwner: jsyal
discoiquuid: c 3 fd 3 f 4 e -0 b 57-4377-b 923-a 440 c 74773 d 8
preview: verdadeiro
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Entendendo os conceitos antes de usar o Experience Cloud Manager{#understanding-concepts-before-using-cloud-manager}

Esta seção fornece conceitos e terminações que são boas para saber antes de trabalhar no Cloud Manager e abranger os seguintes tópicos:

* **Ambiente de implantação**
* **Repositório de código-fonte**
* **Segurança e privacidade**
* **Visão geral do pipeline**
* **Recursos de ajuda**

## Ambiente de implantação {#deployment-environment}

Você pode ser novo no Adobe Experience Manager (AEM) 6.4 ou precisa de uma atualização para o AEM 6.4.

Se você for um novo AEM 6.4, você já terá acesso ao Experience Cloud Manager.

Se você for um cliente existente, precisará atualizar para o AEM 6.4 para ter acesso ao Gerenciador de nuvem. Você pode começar a usar o Experience Cloud Manager depois de receber URL e credenciais de Engenheiros de sucesso do cliente (CSE).

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:19:24.147-0400

Section is redundant with the section in the Overview topic

 -->

## Repositório de código-fonte {#source-code-repository}

**Vários servidores Git**: Em alguns casos, os clientes terão um repositório git existente e desejam continuar usando.

Nesses casos, você pode usar o suporte do git para vários repositórios remotos. O desenvolvimento do dia para o dia continuaria a ocorrer no seu repositório de git. Quando uma implantação é desejada, basta mover o código mais recente para o repositório do git do Experience Cloud Manager.

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:20:46.002-0400

Looks like we lost some content, compared to the previous version

 -->

## Segurança e privacidade {#security-and-privacy}

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-04-21T02:38:21.417-0400

Query for Brad B.

 -->

## Visão geral do pipeline {#pipeline-overview}

O Cloud Manager oferecerá suporte a um único pipeline por programa (definição acima), que manipula implantações para estágio e produção. ****

A ramificação do git usada para implantações de estágio e produção é mestre.

>[!NOTE]
>
>É uma prática recomendada usar mestre como um ramo de git para stage e production, mas você pode usar qualquer uma da ramificação enquanto configura o pipeline.

O único processo de pipeline é ilustrado abaixo:

![](assets/screen_shot_2018-04-30at30318pm.png)

### Como entender o fluxo {#understanding-the-flow}

Você pode configurar seu pipeline no [!UICONTROL Pipeline Settings] bloco da interface do usuário do Experience Cloud Manager.

Consulte [Usar o Experience Cloud Manager](hhttps://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) para obter mais informações.

O Gerenciador de implantação é responsável pela configuração do pipeline, isto é:

* atribuição de ramificação do aplicativo
* como atribuir ambientes de implantação
* como definir opções de teste

Ao fazer isso, primeiro selecione uma ramificação a partir do repositório do git. Em seguida, defina o acionador que iniciará o pipeline.

Em seguida, é possível definir os parâmetros que controlam a implantação de produção.

Por fim, você poderá configurar os parâmetros de teste de desempenho.

>[!NOTE]
>
>Para saber como configurar o comportamento e as preferências do seu pipeline, consulte **Configuração de pipeline** em [Uso do Gerenciador de nuvem](using-cloud-manager.md).

### Recursos de ajuda {#help-resources}

Entre em contato com o Engenheiro de sucesso do cliente Adobe Managed Services para obter suporte.

### Próximas etapas {#the-next-steps}

Agora você tem melhor compreensão dos conceitos do Experience Cloud Manager.

Para configurar o projeto, o ambiente e a equipe (usuário e funções), consulte [Configuração de configurações gerais para o Gerenciador](setting-configurations-for-cloud-manager.md)de nuvem.
