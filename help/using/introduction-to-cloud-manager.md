---
title: Introdução ao Experience Cloud Manager
seo-title: Introdução ao Experience Cloud Manager
description: 'Esta página serve como um ponto de partida para aprender sobre o Experience Cloud Manager. '
seo-description: 'Esta página serve como um ponto de partida para aprender sobre o Adobe AEM Cloud Manager e destaca os benefícios e os recursos principais. '
uuid: 62 d 68 e 79-c 2 ba -4 d 8 b-ba 7 d -33709014 d 5 b 6
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introdução
discoiquuid: ebcc 91 a 5-be 9 e -4684-8146-d 88 f 4013 d 4 d 1
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Introdução ao [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

## Introdução {#introduction}

[!UICONTROL Cloud Manager], parte do Adobe Managed Cloud Services, permite que as organizações gerenciem automaticamente o Experience Manager na nuvem. Ela inclui uma integração contínua e uma estrutura de entrega contínua (CI/CD) que permite que equipes de TI e parceiros de implementação agilizem a entrega de personalizações ou atualizações sem comprometer o desempenho ou a segurança.

Usando o portal do cliente [!UICONTROL Cloud Manager] de autoatendimento, **as organizações** podem executar/aproveitar o seguinte:

* **Integração contínua/Entrega contínua** de código para reduzir o tempo de comercialização de meses/semanas para dias/horas.
* **Inspeção de código, teste de desempenho e validação de segurança** com base nas práticas recomendadas antes de pressionar para produção para minimizar as interrupções de produção.
* **Implantação** automática, programada ou manual, mesmo fora do horário comercial, para maior flexibilidade e controle.
* **O** recurso de rastreamento automático detecta a necessidade de aumentar a capacidade e traz automaticamente segmentos adicionais on-line do Dispatcher/Publish.

A imagem a seguir ilustra o fluxo de processo CI/CD usado em [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Principais recursos em [!UICONTROL Cloud Manager]{#key-features-in-cloud-manager}

As organizações podem aproveitar os seguintes recursos, com [!UICONTROL Cloud Manager]:

### Interface de autoatendimento {#self-service-interface}

A interface do usuário (IU) para [!UICONTROL Cloud Manager] permitir que os clientes acessem e gerenciem facilmente o ambiente em nuvem e o pipeline CI/CD para seus aplicativos do Experience Manager.

Os clientes definem Indicadores-chave de desempenho específicos do aplicativo (kpis) - visualizações de página por minuto e tempo de resposta esperado para um carregamento de página, que em última análise formam a base para medir uma implantação bem-sucedida. As funções e permissões para diferentes membros da equipe podem ser facilmente definidas. Embora a nova interface de autoatendimento coloque o controle novamente em suas mãos, também oferece links para práticas recomendadas e acesso a especialistas da Adobe que podem fornecer as orientações necessárias, conforme necessário.

Para explorar e começar a usar [!UICONTROL Cloud Manager]a interface do usuário, consulte [Login na primeira vez](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html).

### Pipeline CI/CD {#ci-cd-pipeline}

Um dos principais recursos da [!UICONTROL Cloud Manager] é a capacidade de implantar um pipeline CI/CD otimizado para acelerar a entrega de código personalizado ou atualizações, como adicionar novos componentes no site.

Por meio da [!UICONTROL Cloud Manager] interface do usuário, os clientes podem configurar e desligar seu pipeline CI/CD. Durante esse pipeline, uma varredura de código detalhada é executada para garantir que somente aplicativos de alta qualidade passem até o ambiente de produção.

To learn more about configuring pipeline from [!UICONTROL Cloud Manager]&#39;s UI, see [Configure your CI/CD Pipeline](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).

### Modos de implantação flexíveis {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] oferece aos clientes modos de implantação flexíveis e configuráveis para que eles possam fornecer experiências de acordo com as mudanças de negócios.

Com um modo de acionamento automático, o código é implantado automaticamente em um ambiente com base em eventos específicos, como confirmação de código. Também é possível programar implantações de código durante intervalos de tempo especificados, mesmo fora do horário comercial.

Independentemente do acionador de implantação, as verificações de qualidade são sempre executadas como parte da execução do pipeline CI/CD, sempre que uma implantação é acionada. As verificações de qualidade incluem, inspeção de código, teste de segurança e teste de desempenho entregue da caixa, com literalmente nenhum esforço necessário de clientes ou parceiros.

Para saber mais sobre a implantação de verificações de código e qualidade, consulte [Implantar seu código](deploying-code.md)

### Calibração automática {#autoscaling}

[!UICONTROL Cloud Manager] detecta a necessidade de mais capacidade quando o ambiente de produção está sujeito a carregamento excepcionalmente alto e traz automaticamente mais capacidade online por meio de um recurso de rastreamento automático.

Durante um evento de rastreamento automático, [!UICONTROL Cloud Manager] aciona automaticamente o processo de provisionamento automático, envia uma notificação do evento de rastreamento automático e traz a capacidade adicional dentro de minutos. A capacidade adicional será provisionada no ambiente de produção, na (s) mesma (s) região (s) e correspondente às mesmas especificações do sistema que os nós de execução Dispatcher/Publish.

O recurso de rastreamento automático será aplicado somente ao nível Dispatcher/Publish e será sempre executado usando um método de escala horizontal, com no mínimo um segmento adicional de um par de Dispatcher/Publish e até um máximo de dez segmentos. Qualquer capacidade adicional fornecida será redimensionada manualmente dentro de um período de dez dias úteis, conforme determinado pelo CSE (Engenheiro de sucesso do cliente).
