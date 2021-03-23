---
title: Introdução ao Cloud Manager
seo-title: Introdução ao Cloud Manager
description: 'Esta página serve como ponto de partida para saber mais sobre o Cloud Manager. '
seo-description: 'Esta página serve como ponto de partida para saber mais sobre o Adobe AEM Cloud Manager e destaca os benefícios e os principais recursos. '
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
feature: Introdução
level: Iniciante
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 85%

---


# Introdução à [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introdução ao Cloud Manager"
>abstract="Permite que as organizações autogerenciem o Experience Manager na nuvem. Inclui uma estrutura de integração contínua e entrega contínua (CI/CD) que permite que as equipes de TI e os parceiros de implementação acelerem a entrega de personalizações ou atualizações, sem comprometer o desempenho ou a segurança."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="Criar programas"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="Criar ambientes"

## Introdução {#introduction}

[!UICONTROL Cloud Manager], parte do Adobe Experience Manager (AEM) na Cloud, permite que as organizações autogerenciem o Experience Manager na nuvem. Inclui uma estrutura de integração contínua e entrega contínua (CI/CD) que permite que as equipes de TI e os parceiros de implementação acelerem a entrega de personalizações ou atualizações, sem comprometer o desempenho ou a segurança.

Com o uso do [!UICONTROL Cloud Manager]portal de autoatendimento do cliente, as **empresas** podem realizar/potencializar o seguinte:

* **Integração contínua / entrega contínua** de código para reduzir o tempo de comercialização de meses/semanas para dias/horas.
* **Inspeção de código, teste de desempenho e validação de segurança** com base nas práticas recomendadas, antes de levar à produção para minimizar as interrupções da produção.
* **Implantação automática, agendada ou manual**, mesmo fora do horário comercial, para obter o máximo de flexibilidade e controle.
* **O recurso de dimensionamento automático** detecta de forma inteligente a necessidade de maior capacidade e traz automaticamente outros segmentos do Dispatcher/Publish online.

A imagem a seguir ilustra o fluxo do processo CI/CD usado em [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Principais recursos em [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

As empresas podem aproveitar os seguintes recursos, com [!UICONTROL Cloud Manager]:

### Interface de autoatendimento {#self-service-interface}

A interface do usuário (UI) para [!UICONTROL Cloud Manager] permite que os clientes acessem e gerenciem facilmente o ambiente de nuvem e o pipeline de CI/CD para seus aplicativos do Experience Manager.

Os clientes definem os KPIs (Key Performance Indicators, Indicadores-chave de desempenho) específicos do aplicativo - pico de exibições de página por minuto e tempo de resposta esperado para um carregamento de página, que formam a base para medir uma implantação bem-sucedida. As funções e permissões de diferentes membros da equipe podem ser facilmente definidas. Embora a nova interface de autoatendimento devolva o controle para você, ela também oferece links para as práticas recomendadas e acesso a especialistas na Adobe que podem fornecer as orientações necessárias, conforme necessário.

Para explorar e começar a usar a interface do usuário de [!UICONTROL Cloud Manager], consulte [Primeiro logon](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html).

### Pipeline de CI/CD {#ci-cd-pipeline}

Um dos principais recursos do [!UICONTROL Cloud Manager] é a capacidade de utilizar um pipeline de CI/CD otimizado para acelerar a entrega de códigos personalizados ou atualizações, como a adição de novos componentes no site.

Por meio da interface do usuário do [!UICONTROL Cloud Manager], os clientes podem configurar e iniciar o pipeline de CI/CD. Durante esse pipeline, uma varredura de código completa é executada para garantir que somente aplicativos de alta qualidade passem para o ambiente de produção.

Para saber mais sobre como configurar o pipeline da interface do usuário de [!UICONTROL Cloud Manager], consulte [Configurar o pipeline de CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).

### Modos de implantação flexíveis {#flexible-deployment-modes}

O [!UICONTROL Cloud Manager] oferece aos clientes modos de implantação flexíveis e configuráveis para que possam proporcionar experiências de acordo com as demandas comerciais em constante mudança.

Com um modo de acionamento automático, o código é implantado automaticamente em um ambiente com base em eventos específicos, como a confirmação de código. Você também pode programar implantações de código durante períodos de tempo especificados, mesmo fora do horário comercial.

Independentemente do acionador de implantação, as verificações de qualidade são sempre realizadas como parte da execução do pipeline de CI/CD, sempre que uma implantação é acionada. As verificações de qualidade incluem inspeção de código, teste de segurança e teste de desempenho, oferecidos prontos para uso, sem nenhum esforço dos clientes ou parceiros.

Para saber mais sobre a implantação das verificações de código e qualidade, consulte [Implantar o código](deploying-code.md)

### Dimensionamento automático {#autoscaling}

O [!UICONTROL Cloud Manager] detecta a necessidade de capacidade adicional quando o ambiente de produção está sujeito a uma carga excepcionalmente alta e automaticamente oferece capacidade adicional online por meio do recurso de dimensionamento automático.

Durante um evento de dimensionamento automático, o [!UICONTROL Cloud Manager] aciona automaticamente o processo de provisionamento de dimensionamento automático, envia uma notificação do evento de dimensionamento automático e fornece a capacidade adicional online em minutos. A capacidade adicional será provisionada no ambiente de produção, nas mesmas regiões, e corresponderá às mesmas especificações do sistema que os nós do Dispatcher/Publish em execução.

O recurso de dimensionamento automático se aplica somente à camada do Dispatcher/Publish e sempre será executado usando um método de dimensionamento horizontal, com no mínimo um segmento adicional de um par do Dispatcher/Publish e até no máximo dez segmentos. Qualquer capacidade adicional fornecida será dimensionada manualmente em um período de dez dias úteis, conforme determinado pelo CSE (Customer Success Engineer, Engenheiro especializado na fidelização de clientes).

>[!NOTE]
>Os clientes interessados em explorar se o dimensionamento automático é adequado para seu aplicativo devem entrar em contato com o representante do CSE ou do Adobe.
