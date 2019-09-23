---
title: Introdução ao Cloud Manager
seo-title: Introdução ao Cloud Manager
description: 'Esta página serve como ponto de partida para aprender sobre o Cloud Manager. '
seo-description: 'Esta página serve como ponto de partida para aprender sobre o Adobe AEM Cloud Manager e destaca os benefícios e os principais recursos. '
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introdução
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: d7c9ab3795fb3df02ab7dffd1328760ccd914a18

---


# Introdução à [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

## Introdução {#introduction}

[!UICONTROL Cloud Manager], parte dos Serviços da Adobe Managed Cloud, permite que as organizações gerenciem automaticamente o Experience Manager na nuvem. Inclui uma estrutura contínua de integração e entrega contínua (CI/CD) que permite que as equipes de TI e os parceiros de implementação acelerem a entrega de personalizações ou atualizações sem comprometer o desempenho ou a segurança.

Usando o portal do cliente de [!UICONTROL Cloud Manager] autoatendimento, **as organizações** podem executar/aproveitar o seguinte:

* **Integração contínua/fornecimento** contínuo de código para reduzir o tempo de comercialização de meses/semanas para dias/horas.
* **Inspeção de código, teste de desempenho e validação** de segurança com base nas práticas recomendadas antes de levar à produção para minimizar as interrupções da produção.
* **Implantação** automática, programada ou manual, mesmo fora do horário comercial, para obter o máximo de flexibilidade e controle.
* **O recurso de dimensionamento** automático detecta de forma inteligente a necessidade de maior capacidade e traz automaticamente outros segmentos do Dispatcher/Publish online.

A imagem a seguir ilustra o fluxo do processo CI/CD usado em [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Principais recursos em [!UICONTROL Cloud Manager]{#key-features-in-cloud-manager}

As organizações podem aproveitar os seguintes recursos, com [!UICONTROL Cloud Manager]:

### Interface de autoatendimento {#self-service-interface}

A interface do usuário (UI) para [!UICONTROL Cloud Manager] permite que os clientes acessem e gerenciem facilmente o ambiente de nuvem e o pipeline CI/CD para seus aplicativos Experience Manager.

Os clientes definem KPIs (Indicadores-chave de desempenho) específicos do aplicativo - exibições de página de pico por minuto e tempo de resposta esperado para uma carga de página, que formam a base para medir uma implantação bem-sucedida. As funções e permissões de diferentes membros da equipe podem ser facilmente definidas. Embora a nova interface de autoatendimento coloque o controle de volta em suas mãos, ela também oferece links para as práticas recomendadas e acesso a especialistas na Adobe que podem fornecer as orientações necessárias, conforme necessário.

Para explorar e começar a usar [!UICONTROL Cloud Manager]a interface do usuário do, consulte [Logon](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html)pela primeira vez.

### Pipeline CI/CD {#ci-cd-pipeline}

Um dos principais recursos do é [!UICONTROL Cloud Manager] a capacidade de utilizar um pipeline de CI/CD otimizado para acelerar a entrega de códigos personalizados ou atualizações, como a adição de novos componentes no site.

Por meio da [!UICONTROL Cloud Manager] interface do usuário, os clientes podem configurar e iniciar seu pipeline de CI/CD. Durante esse pipeline, uma varredura de código completa é executada para garantir que somente aplicativos de alta qualidade passem para o ambiente de produção.

Para saber mais sobre como configurar o pipeline da interface do usuário [!UICONTROL Cloud Manager]do, consulte [Configurar o pipeline CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).

### Modos de implantação flexíveis {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] oferece aos clientes modos de implantação flexíveis e configuráveis para que possam oferecer experiências de acordo com as demandas comerciais em constante mudança.

Com um modo de disparo automático, o código é implantado automaticamente em um ambiente com base em eventos específicos, como a confirmação de código. Você também pode programar implantações de código durante períodos de tempo especificados, mesmo fora do horário comercial.

Independentemente do acionador de implantação, as verificações de qualidade são sempre realizadas como parte da execução do pipeline de CI/CD, sempre que uma implantação é acionada. As verificações de qualidade incluem, inspeção de código, teste de segurança e teste de desempenho fornecidos prontos para uso, sem nenhum esforço dos clientes ou parceiros.

Para saber mais sobre a implantação de verificações de código e qualidade, consulte [Implantar seu código](deploying-code.md)

### Autoescala {#autoscaling}

[!UICONTROL Cloud Manager] detecta a necessidade de capacidade adicional quando o ambiente de produção está sujeito a uma carga excepcionalmente alta e automaticamente traz capacidade adicional on-line por meio do recurso de dimensionamento automático.

Durante um evento de dimensionamento automático, o aciona [!UICONTROL Cloud Manager] automaticamente o processo de provisionamento de dimensionamento automático, envia uma notificação do evento de dimensionamento automático e traz a capacidade adicional on-line em minutos. A capacidade adicional será provisionada no ambiente de produção, nas mesmas regiões e corresponderá às mesmas especificações do sistema que os nós Dispatcher/Publish em execução.

O recurso de dimensionamento automático se aplica somente à camada do Dispatcher/Publish e sempre será executado usando um método de dimensionamento horizontal, com um mínimo de um segmento adicional de um par do Dispatcher/Publish e até um máximo de dez segmentos. Qualquer capacidade adicional fornecida será dimensionada manualmente dentro de um período de dez dias úteis, conforme determinado pelo CSE (Customer Success Engineer).
