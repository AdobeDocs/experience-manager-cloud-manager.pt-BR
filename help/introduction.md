---
title: Introdução ao Cloud Manager para AMS
description: Comece aqui para conhecer o Cloud Manager para Adobe Managed Services (AMS) e como ele permite que as organizações gerenciem manualmente o Adobe Experience Manager na nuvem.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 14e35882765783b234ca35da14257279af5130a0
workflow-type: ht
source-wordcount: '1311'
ht-degree: 100%

---


# Introdução ao [!UICONTROL Cloud Manager] para AMS {#introduction-to-cloud-manager}

Comece aqui para conhecer o Cloud Manager para Adobe Manage Services (AMS) e como ele permite que as organizações gerenciem manualmente o Adobe Experience Manager na nuvem.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introdução ao Cloud Manager para AMS"
>abstract="Permite que as organizações gerenciem manualmente o Adobe Experience Manager na nuvem. Inclui uma estrutura de integração contínua e entrega contínua (CI/CD) que permite que as equipes de TI e os parceiros de implementação acelerem a entrega de personalizações ou atualizações, sem comprometer o desempenho ou a segurança."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=pt-BR#cloud-manager" text="Criar programas"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=pt-BR#cloud-manager" text="Criar ambientes"

## Introdução {#introduction}

O [!UICONTROL Cloud Manager] para Adobe Experience Manager oferece aos desenvolvedores a capacidade de criar experiências de cliente impactantes por meio de fluxos de trabalho simplificados, com base nas práticas recomendadas do Adobe Experience Manager. Os pipelines de CI/CD otimizados para o Adobe Experience Manager permitem mesclar facilmente os fluxos de trabalho de desenvolvimento com uma simples verificação de seu código, que pode então movimentar-se até estar pronto para produção. Durante a fase de criação, suas atualizações de código personalizadas são testadas minuciosamente em relação às práticas recomendadas para fornecer aplicativos confiáveis aos seus clientes. O Cloud Manager usa uma abordagem de API aberta e permite que você se integre aos seus sistemas sem interromper os processos e as ferramentas existentes.

>[!NOTE]
>
>Esta documentação descreve especificamente os recursos e as funções do Cloud Manager para Adobe Managed Services (AMS).
>
>A documentação equivalente para o AEM as a Cloud Service pode ser encontrada na [documentação do AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html?lang=pt-BR)

Com o Cloud Manager, sua equipe de desenvolvimento se beneficia dos seguintes recursos:

* Integração/entrega contínua (CI/CD) de código para reduzir o tempo de comercialização de meses e semanas para dias e horas.

* Para minimizar interrupções, antes de prosseguir para a produção são realizadas inspeções de código, testes de desempenho e validações de segurança com base nas práticas recomendadas.

* Conectividade de API para complementar processos DevOps existentes.

* Dimensionamento automático que detecta de forma inteligente a necessidade de maior capacidade e ativa automaticamente outros segmentos do Dispatcher e de publicação.

Essa imagem ilustra o fluxo do processo de CI/CD usado no [!UICONTROL Cloud Manager]:

![Fluxo de CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Principais recursos no [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Veja a seguir em mais detalhes uma seleção dos principais recursos do Cloud Manager.

### Interface de autoatendimento {#self-service-interface}

A interface (UI) do [!UICONTROL Cloud Manager] permite acessar e gerenciar facilmente o ambiente de nuvem e o pipeline de CI/CD dos aplicativos do Adobe Experience Manager.

Os clientes definem os KPIs (Key Performance Indicators, Indicadores-chave de desempenho) específicos do aplicativo (como o pico de visualizações de página por minuto e o tempo de resposta esperado para o carregamento de uma página) que formam a base para medir uma implantação bem-sucedida. As funções e permissões de diferentes membros da equipe podem ser facilmente definidas. Embora a nova interface de autoatendimento coloque o controle em suas mãos, ela também oferece links para as práticas recomendadas e acesso a especialistas da Adobe que podem fornecer orientações oportunas, conforme necessário.

Para explorar e começar a usar a interface do [!UICONTROL Cloud Manager], consulte o documento [Primeiro logon.](/help/getting-started/first-time-login.md)

### Pipeline de CI/CD {#ci-cd-pipeline}

Um dos principais recursos do [!UICONTROL Cloud Manager] é a capacidade de utilizar um pipeline de CI/CD otimizado para acelerar a entrega de códigos personalizados ou atualizações, como a adição de novos componentes no site.

Por meio da interface do [!UICONTROL Cloud Manager], é possível configurar e iniciar o pipeline de CI/CD. Como parte desse pipeline, uma varredura de código completa é executada para garantir que somente aplicativos de alta qualidade passem para o ambiente de produção.

Para saber mais sobre como configurar o pipeline na interface do [!UICONTROL Cloud Manager], consulte os documentos [Configurar pipelines de produção](/help/using/production-pipelines.md) e [Configurar pipelines de não produção.](/help/using/non-production-pipelines.md)

### Modos de implantação flexíveis {#flexible-deployment-modes}

O [!UICONTROL Cloud Manager] oferece modos de implantação flexíveis e configuráveis para que você possa proporcionar experiências de acordo com as demandas comerciais em constante mudança.

Com um modo de acionamento automático, o código é implantado automaticamente em um ambiente com base em eventos específicos, como a confirmação de código. Você também pode programar implantações de código durante períodos de tempo especificados, mesmo fora do horário comercial.

Independentemente do acionador de implantação, verificações de qualidade são realizadas como parte da execução do pipeline de CI/CD, sempre que uma implantação é acionada. As verificações de qualidade incluem inspeções de código, testes de segurança e de desempenho. Todas elas são prontas para uso e não exigem nenhum esforço da sua parte ou dos seus parceiros.

Para saber mais sobre a implantação das verificações de código e de qualidade, consulte o documento [Implantar código.](/help/using/code-deployment.md)

## Recursos opcionais no Cloud Manager {#optional-features-in-cloud-manager}

O Cloud Manager oferece recursos adicionais e avançados que podem trazer benefícios para seu projeto, dependendo da configuração e das necessidades específicas do ambiente. Se esses recursos forem de seu interesse, entre em contato com o engenheiro de sucesso do cliente (CSE) ou representante da Adobe para saber mais detalhes.

### Dimensionamento automático {#autoscaling}

Quando o ambiente de produção é sujeito a uma carga excepcionalmente alta, o [!UICONTROL Cloud Manager] detecta a necessidade de capacidade adicional e a ativa automaticamente usando seu recurso de dimensionamento automático.

Durante um evento desse tipo, o [!UICONTROL Cloud Manager] aciona automaticamente o processo de provisionamento de dimensionamento automático, envia uma notificação do evento de dimensionamento automático e ativa a capacidade adicional em uma questão de minutos. A capacidade adicional será provisionada no ambiente de produção, na(s) mesma(s) região(ões), e corresponderá às mesmas especificações do sistema que os nós do(a) Dispatcher/publicação em execução.

O recurso de dimensionamento automático se aplica somente à camada do(a) Dispatcher/publicação e será executado usando um método de dimensionamento horizontal, com no mínimo um segmento adicional de um par do(a) Dispatcher/publicação e até no máximo dez segmentos. Qualquer capacidade adicional fornecida será dimensionada manualmente em um período de dez dias úteis, conforme determinado pelo CSE (Customer Success Engineer, engenheiro especializado na fidelização de clientes).

>[!NOTE]
>
>Se você estiver interessado em explorar se o dimensionamento automático é adequado para seu aplicativo, entre em contato com seu CSE ou representante da Adobe.

### Implantações azul/verde {#blue-green}

A implantação azul/verde é uma técnica que reduz o tempo de inatividade e o risco ao executar dois ambientes de produção idênticos chamados azul e verde.

A qualquer momento, apenas um dos ambientes está ativo, com o ambiente ativo atendendo todo o tráfego de produção. Em geral, azul será o ambiente ativo no momento e o verde estará ocioso.

* A implantação azul/verde é um complemento dos pipelines de CI/CD do Cloud Manager, no qual um segundo conjunto de instâncias de publicação e Dispatcher (verde) é criado e usado para implantações. As instâncias verdes são anexadas ao balanceador de carga de produção e as instâncias antigas (azul) são removidas e finalizadas.
* Essa implementação de azul/verde trata as instâncias como transitórias e cada iteração de um pipeline azul/verde criará um novo conjunto de servidores de publicação e do Dispatcher.
* Um balanceador de carga verde será criado como parte da configuração. Este balanceador de carga nunca mudará e é para o que você deve apontar seu URL verde ou de &quot;teste&quot;.
* Durante uma implantação azul/verde, uma réplica exata dos níveis existentes de publicação/Dispatcher será criada.

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
| 8 | A infraestrutura azul é encerrada automaticamente | - |

#### Implementação de azul/verde {#implementing}

Todos os usuários do AMS que usam o Cloud Manager para implantações de produção estão qualificados para usar a implantação azul/verde. No entanto, o uso da implantação azul/verde requer a validação adicional de seus ambientes e a configuração por um Adobe CSE.

Se você estiver interessado na implantação azul/verde, considere os seguintes requisitos e limitações e entre em contato com seu CSE.

#### Requisitos e limitações {#limitations}

* Azul/verde está disponível somente para pares de publicação/Dispatcher.
* Visualizar pares do Dispatcher/publicação não faz parte de implantações azuis/verdes.
* Cada par do Dispatcher/publicação é idêntico a qualquer outro par do Dispatcher/publicação.
* Azul/verde está disponível somente no ambiente de produção.
* Azul/verde está disponível no AWS e no Azure.
* Azul/verde não está disponível somente para clientes do Assets.
