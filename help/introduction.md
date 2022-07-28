---
title: Introdução ao Cloud Manager para AMS
description: Comece aqui para conhecer o Cloud Manager for Adobe Managed Services (AMS) e como ele permite que as organizações autogerenciem o Adobe Experience Manager na nuvem.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 14e35882765783b234ca35da14257279af5130a0
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 10%

---


# Introdução ao [!UICONTROL Cloud Manager] para AMS {#introduction-to-cloud-manager}

Comece aqui para conhecer o Cloud Manager for Adobe Manage Services (AMS) e como ele permite que as organizações autogerenciem o Adobe Experience Manager na nuvem.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introdução ao Cloud Manager para AMS"
>abstract="Permite que as organizações autogerenciem o Adobe Experience Manager na nuvem. Inclui uma estrutura de integração contínua e entrega contínua (CI/CD) que permite que as equipes de TI e os parceiros de implementação acelerem a entrega de personalizações ou atualizações, sem comprometer o desempenho ou a segurança."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="Criar programas"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="Criar ambientes"

## Introdução {#introduction}

[!UICONTROL Cloud Manager] O para Adobe Experience Manager oferece aos desenvolvedores a capacidade de criar experiências de cliente impactantes por meio de fluxos de trabalho simplificados, com base nas práticas recomendadas da Adobe Experience Manager. Os pipelines de CI/CD otimizados para o Adobe Experience Manager permitem mesclar facilmente os workflows de desenvolvimento, simplesmente verificando seu código, que pode então se mover até o ponto de estar pronto para produção. Durante a fase de criação, suas atualizações de código personalizadas são totalmente testadas em relação às práticas recomendadas para fornecer aplicativos confiáveis para seus clientes. O Cloud Manager usa uma abordagem de API aberta e permite que você se integre aos seus sistemas sem interromper os processos e as ferramentas existentes.

>[!NOTE]
>
>Esta documentação descreve especificamente os recursos e as funções do Cloud Manager para Adobe Managed Services (AMS).
>
>A documentação equivalente para AEM as a Cloud Service pode ser encontrada no [AEM documentação as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html)

Com o Cloud Manager, sua equipe de desenvolvimento se beneficia dos seguintes recursos:

* Integração contínua/entrega contínua (CI/CD) de código para reduzir o tempo de comercialização de meses/semanas para dias/horas

* Inspeção de código, teste de desempenho e validação de segurança com base nas práticas recomendadas antes de levar à produção para minimizar as interrupções da produção

* Conectividade de API para complementar processos DevOps existentes

* Dimensionamento automático que detecta de forma inteligente a necessidade de maior capacidade e traz automaticamente outros segmentos do Dispatcher/Publicação online

Esta imagem ilustra o fluxo do processo CI/CD usado em [!UICONTROL Cloud Manager]:

![Fluxo CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Principais recursos em [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Veja a seguir um mergulho mais profundo nos principais recursos selecionados do Cloud Manager.

### Interface de autoatendimento {#self-service-interface}

A interface do usuário (UI) para [!UICONTROL Cloud Manager] O permite acessar e gerenciar facilmente o ambiente de nuvem e o pipeline de CI/CD para seus aplicativos Adobe Experience Manager.

Você define KPIs (Key Performance Indicators, indicadores-chave de desempenho específicos do aplicativo) (como o pico de exibições de página por minuto e o tempo de resposta esperado para um carregamento de página) que formam a base para medir uma implantação bem-sucedida. As funções e permissões de diferentes membros da equipe podem ser facilmente definidas. A interface de autoatendimento coloca o controle em suas mãos, mas também oferece links para os recursos de práticas recomendadas e acesso a especialistas no Adobe, que podem fornecer as orientações necessárias, conforme necessário.

Para explorar e começar a usar [!UICONTROL Cloud Manager]da interface do usuário do , consulte o documento [Primeiro logon.](/help/getting-started/first-time-login.md)

### Pipeline de CI/CD {#ci-cd-pipeline}

Um dos principais recursos do [!UICONTROL Cloud Manager] é a capacidade de utilizar um pipeline de CI/CD otimizado para acelerar a entrega de códigos personalizados ou atualizações, como a adição de novos componentes no site.

Por meio da [!UICONTROL Cloud Manager] Na interface do usuário, você pode configurar e iniciar o pipeline de CI/CD. Como parte desse pipeline, uma varredura de código completa é executada para garantir que somente aplicativos de alta qualidade passem para o ambiente de produção.

Para saber mais sobre como configurar o pipeline no [!UICONTROL Cloud Manager]interface do usuário do , consulte os documentos [Configuração de pipeline de produção](/help/using/production-pipelines.md) e [Configuração de pipeline de não produção.](/help/using/non-production-pipelines.md)

### Modos de implantação flexíveis {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] O oferece modos de implantação flexíveis e configuráveis para que você possa proporcionar experiências de acordo com as demandas comerciais em constante mudança.

Com um modo de acionamento automático, o código é implantado automaticamente em um ambiente com base em eventos específicos, como a confirmação de código. Você também pode programar implantações de código durante períodos de tempo especificados, mesmo fora do horário comercial.

Independentemente do acionador de implantação, as verificações de qualidade são sempre realizadas como parte da execução do pipeline de CI/CD sempre que uma implantação é acionada. As verificações de qualidade incluem inspeção de código, teste de segurança e teste de desempenho, sendo que todos são fornecidos prontos para uso sem nenhum esforço necessário de você ou de seus parceiros.

Para saber mais sobre a implantação das verificações de código e qualidade, consulte o documento [Implantação do código.](/help/using/code-deployment.md)

## Recursos opcionais no Cloud Manager {#optional-features-in-cloud-manager}

O Cloud Manager oferece recursos adicionais e avançados que podem ser benéficos para o seu projeto, dependendo da configuração e das necessidades específicas do ambiente. Se esses recursos forem de seu interesse, entre em contato com o engenheiro de sucesso do cliente (CSE) ou representante do Adobe para discutir mais sobre isso.

### Dimensionamento automático {#autoscaling}

Quando o ambiente de produção estiver sujeito a uma carga excepcionalmente alta, [!UICONTROL Cloud Manager] O detecta a necessidade de capacidade adicional e automaticamente adiciona capacidade adicional online usando seu recurso de dimensionamento automático.

Nesse caso, [!UICONTROL Cloud Manager] O aciona automaticamente o processo de provisionamento de dimensionamento automático, envia uma notificação do evento de dimensionamento automático e oferece capacidade adicional online em minutos. A capacidade adicional é provisionada no ambiente de produção, nas mesmas regiões e corresponde às mesmas especificações do sistema que os nós do Dispatcher/publicação em execução.

O recurso de dimensionamento automático se aplica somente à camada do Dispatcher/publicação e é executado usando um método de dimensionamento horizontal, com no mínimo um segmento adicional de um par do Dispatcher/publicação até no máximo dez segmentos. Qualquer capacidade adicional fornecida será dimensionada manualmente em um período de dez dias úteis, conforme determinado pelo CSE (Customer Success Engineer, Engenheiro especializado na fidelização de clientes).

>[!NOTE]
>
>Se você estiver interessado em explorar se o dimensionamento automático é adequado para seu aplicativo, entre em contato com seu representante de CSE ou Adobe.

### Implantações azul/verde {#blue-green}

A implantação azul/verde é uma técnica que reduz o tempo de inatividade e o risco ao executar dois ambientes de produção idênticos chamados azul e verde.

A qualquer momento, apenas um dos ambientes está ao vivo, com o ambiente ativo servindo todo o tráfego de produção. Em geral, azul é o ambiente atualmente em funcionamento e verde está ocioso.

* A implantação azul/verde é um complemento dos pipelines CI/CD do Cloud Manager, no qual um segundo conjunto de instâncias de publicação e Dispatcher (verde) é criado e usado para implantações. As instâncias verdes são anexadas ao balanceador de carga de produção e as instâncias antigas (azul) são removidas e finalizadas.
* Essa implementação de azul/verde trata as instâncias como transitórias e cada iteração de um pipeline azul/verde criará um novo conjunto de servidores de publicação e Dispatcher.
* Um balanceador de carga verde será criado como parte da configuração. Esse balanceador de carga nunca mudará e é para o que você deve apontar seu URL verde ou &quot;teste&quot;.
* Durante uma implantação azul/verde, uma réplica exata dos níveis existentes de publicação/Dispatcher será criada.

#### Fluxo de implantação azul/verde {#flow}

Quando a implantação azul/verde está ativada, o fluxo de implantação é diferente do fluxo de implantação do Cloud Service padrão.

| Etapa | Implantação azul/verde | Implantação padrão |
|---|---|---|
| 1 | Implantação para autor | Implantação para autor |
| 2 | Pausar para teste | - |
| 3 | A infraestrutura verde é criada | - |
| 4 | Implantação para níveis verdes de publicação/dispatcher | Implantação para editor |
| 5 | Pausar para teste (até 24 horas) | - |
| 6 | A infraestrutura verde é adicionada ao balanceador de carga de produção | - |
| 7 | A infraestrutura azul é removida do balanceador de carga de produção- |
| 8 | A infraestrutura azul é encerrada automaticamente | - |

#### Implementação de azul/verde {#implementing}

Todos os usuários do AMS que usam o Cloud Manager para implantações de produção estão qualificados para usar a implantação azul/verde. No entanto, o uso da implantação azul/verde requer a validação adicional de seus ambientes e a configuração por um Adobe CSE.

Se você estiver interessado em implantação azul/verde, considere os seguintes requisitos e limitações e entre em contato com seu CSE.

#### Requisitos e limitações {#limitations}

* Azul/verde está disponível somente para pares de publicação/Dispatcher.
* Visualizar pares do Dispatcher/publicar não fazem parte de implantações azuis/verdes.
* Cada par Dispatcher/publish é idêntico a qualquer outro par Dispatcher/publish.
* Azul/verde está disponível somente no ambiente de produção.
* Azul/verde está disponível no AWS e no Azure.
* Azul/verde não está disponível somente para clientes do Assets.
