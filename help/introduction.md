---
title: Introdução ao Cloud Manager para AMS
description: Comece aqui para conhecer o Cloud Manager para Adobe Managed Services (AMS) e como ele permite que as organizações gerenciem manualmente o Adobe Experience Manager na nuvem.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: ht
source-wordcount: '1256'
ht-degree: 100%

---


# Introdução ao [!UICONTROL Cloud Manager] para AMS {#introduction-to-cloud-manager}

Comece aqui para conhecer o Cloud Manager para AMS (Adobe Managed Services) e como ele permite que as organizações gerenciem manualmente o Adobe Experience Manager na nuvem.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introdução ao Cloud Manager para AMS"
>abstract="Permite que as organizações gerenciem manualmente o Adobe Experience Manager na nuvem. Inclui uma estrutura de integração contínua e entrega contínua (CI/CD) que permite que as equipes de TI e os parceiros de implementação acelerem a entrega de personalizações ou atualizações, sem comprometer o desempenho ou a segurança."
>additional-url="https://experienceleague.adobe.com/pt-br/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Criar programas"
>additional-url="https://experienceleague.adobe.com/pt-br/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Criar ambientes"

## Introdução {#introduction}

O [!UICONTROL Cloud Manager] para Adobe Experience Manager oferece aos desenvolvedores a capacidade de criar experiências de cliente impactantes por meio de fluxos de trabalho simplificados, com base nas práticas recomendadas do Adobe Experience Manager. Os pipelines de CI/CD otimizados para o Adobe Experience Manager permitem mesclar facilmente os fluxos de trabalho de desenvolvimento com uma simples verificação de seu código, que pode então ser movido até estar pronto para produção. Durante a fase de criação, suas atualizações de código personalizadas são testadas minuciosamente em relação às práticas recomendadas para fornecer aplicativos confiáveis aos seus clientes. O Cloud Manager usa uma abordagem de API aberta e permite que você se integre aos seus sistemas sem interromper os processos e as ferramentas existentes.

>[!NOTE]
>
>Esta documentação descreve especificamente os recursos e as funções do Cloud Manager para Adobe Managed Services (AMS).
>
>A documentação equivalente para o AEM as a Cloud Service pode ser encontrada na [documentação do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/implementing/home).

Com o Cloud Manager, sua equipe de desenvolvimento se beneficia dos seguintes recursos:

* Integração/entrega contínua (CI/CD) de código para reduzir o tempo de comercialização de meses/semanas para dias/horas.

* Para minimizar interrupções, antes de prosseguir para a produção são realizadas inspeções de código, testes de desempenho e validações de segurança com base nas práticas recomendadas.

* Conectividade de API para complementar processos DevOps.

* Dimensionamento automático que detecta de forma inteligente a necessidade de maior capacidade e ativa automaticamente outros segmentos do Dispatcher/publicação.

Essa imagem ilustra o ![fluxo do processo de CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png) usado no [!UICONTROL Cloud Manager].

## Recursos principais do [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Veja a seguir em mais detalhes uma seleção dos principais recursos do Cloud Manager.

### Interface de autoatendimento {#self-service-interface}

A interface (UI) do [!UICONTROL Cloud Manager] permite acessar e gerenciar facilmente o ambiente de nuvem e o pipeline de CI/CD dos aplicativos do Adobe Experience Manager.

Você define os indicadores principais de desempenho (KPIs) específicos do aplicativo, como o pico de visualizações de página por minuto ou tempo de resposta esperado para o carregamento de uma página. Esses KPIs servem como base para medir o sucesso da implantação. As funções e permissões de diferentes membros da equipe podem ser facilmente definidas. A interface de autoatendimento oferece controle total. Ela também fornece links para recursos sobre práticas recomendadas e acesso a especialistas da Adobe para obter orientações quando necessário.

Para explorar e começar a usar a interface do [!UICONTROL Cloud Manager], consulte [Primeiro logon](/help/getting-started/first-time-login.md).

### Pipeline de CI/CD {#ci-cd-pipeline}

Um dos principais recursos do [!UICONTROL Cloud Manager] é a capacidade de utilizar um pipeline de CI/CD otimizado para acelerar a entrega de códigos personalizados ou atualizações, como a adição de novos componentes no site.

Por meio da interface do [!UICONTROL Cloud Manager], é possível configurar e iniciar o pipeline de CI/CD. Como parte desse pipeline, uma varredura de código completa é executada para garantir que somente aplicativos de alta qualidade passem para o ambiente de produção.

Para saber mais sobre como configurar um pipeline na interface do [!UICONTROL Cloud Manager], consulte os documentos [Configuração de pipelines de produção](/help/using/production-pipelines.md) e [Configuração de pipelines de não produção](/help/using/non-production-pipelines.md).

### Modos de implantação flexíveis {#flexible-deployment-modes}

O [!UICONTROL Cloud Manager] oferece modos de implantação flexíveis e configuráveis para que você possa proporcionar experiências de acordo com as demandas comerciais em constante mudança.

Com um modo de acionamento automático, o código é implantado automaticamente em um ambiente com base em eventos específicos, como a confirmação de código. Você também pode programar implantações de código durante períodos de tempo especificados, mesmo fora do horário comercial.

Independentemente do acionador de implantação, verificações de qualidade são realizadas como parte da execução do pipeline de CI/CD, sempre que uma implantação é acionada. As verificações de qualidade incluem inspeções de código, testes de segurança e de desempenho. Todas elas vêm prontas para uso e não exigem nenhum esforço da sua parte ou dos seus parceiros.

Para saber mais sobre a implantação das verificações de código e de qualidade, consulte [Implantação de código](/help/using/code-deployment.md).

## Recursos opcionais no Cloud Manager {#optional-features-in-cloud-manager}

O Cloud Manager oferece recursos adicionais e avançados que podem trazer benefícios para seu projeto, dependendo da configuração e das necessidades específicas do ambiente. Se esses recursos forem do seu interesse, entre em contato com o engenheiro de sucesso do cliente (CSE) ou representante da Adobe para mais detalhes.

### Dimensionamento automático {#autoscaling}

Quando o ambiente de produção é sujeito a uma carga excepcionalmente alta, o [!UICONTROL Cloud Manager] detecta a necessidade de capacidade adicional e a ativa automaticamente usando seu recurso de dimensionamento automático.

Durante um evento desse tipo, o [!UICONTROL Cloud Manager] aciona automaticamente o processo de provisionamento de dimensionamento automático, envia uma notificação do evento de dimensionamento automático e ativa a capacidade adicional em uma questão de minutos. A capacidade adicional é provisionada no ambiente de produção, nas mesmas regiões, e corresponde às mesmas especificações do sistema que os nós de Dispatcher/publicação em execução.

O recurso de dimensionamento automático se aplica à camada de Dispatcher/publicação, usando dimensionamento horizontal para adicionar de um a dez segmentos de pares de Dispatcher/publicação. Qualquer capacidade adicional fornecida é dimensionada manualmente em um período de dez dias úteis, conforme determinado pelo CSE (Customer Success Engineer, engenheiro de sucesso do cliente) da Adobe.

>[!NOTE]
>
>Se você tiver interesse em experimentar se o dimensionamento automático é adequado para o seu aplicativo, entre em contato com seu CSE ou representante da Adobe.

### Implantações azul/verde {#blue-green}

A implantação azul/verde é uma técnica que reduz o tempo de inatividade e o risco ao executar dois ambientes de produção idênticos chamados azul e verde.

A qualquer momento, apenas um dos ambientes está ativo, com o ambiente ativo atendendo todo o tráfego de produção. Em geral, azul será o ambiente ativo no momento e o verde estará ocioso.

* A implantação azul/verde é um complemento dos pipelines de CI/CD do Cloud Manager, no qual um segundo conjunto de instâncias de publicação e Dispatcher (verde) é criado e usado para implantações. As instâncias verdes são anexadas ao balanceador de carga de produção e as instâncias antigas (azul) são removidas e finalizadas.
* Essa implementação de azul/verde trata as instâncias como transitórias e cada iteração de um pipeline azul/verde cria um novo conjunto de servidores de publicação e do Dispatcher.
* Um balanceador de carga verde é criado como parte da configuração. Esse balanceador de carga nunca muda e é para ele que você deve apontar seu URL verde ou de “teste”.
* Durante uma implantação azul/verde, é criada uma réplica exata dos níveis existentes de Dispatcher/publicação.

#### Fluxo de implantação azul/verde {#flow}

Quando a implantação azul/verde está ativada, o fluxo de implantação é diferente do fluxo de implantação padrão do Cloud Service.

| Etapa | Implantação azul/verde | Implantação padrão |
|---|---|---|
| 1 | Implantação para autor | Implantação para autor |
| 2 | Pausar para teste | - |
| 3 | A infraestrutura verde é criada | - |
| 4 | Implantação para níveis verdes de publicação/dispatcher | Implantação para editor |
| 5 | Pausar para teste (até 24 horas) | - |
| 6 | A infraestrutura verde é adicionada ao balanceador de carga de produção | - |
| 7 | A infraestrutura azul é removida do balanceador de carga de produção- |
| 8 | Pausar para saída final (até 24 horas) | - |
| 9 | A infraestrutura azul é encerrada automaticamente | - |
| 10 | Pipeline completo | - |

#### Implementação azul/verde {#implementing}

Todos os usuários do AMS que usam o Cloud Manager para implantações de produção estão qualificados para usar a implantação azul/verde. No entanto, o uso da implantação azul/verde requer a validação adicional de seus ambientes e a configuração por um CSE da Adobe.

Se você tiver interesse na implantação azul/verde, considere os requisitos e limitações a seguir e entre em contato com o seu CSE.

#### Requisitos e limitações {#limitations}

* Azul/verde está disponível somente para pares de Dispatcher/publicação.
* A visualização de pares de Dispatcher/publicação não faz parte de implantações azuis/verdes.
* Cada par de Dispatcher/publicação é idêntico a qualquer outro par de Dispatcher/publicação.
* Azul/verde está disponível somente no ambiente de produção.
* Azul/verde está disponível no AWS e no Azure.
* Azul/verde não está disponível para clientes somente do Assets.
