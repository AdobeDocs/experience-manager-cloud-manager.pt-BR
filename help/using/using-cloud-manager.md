---
title: Usando o Experience Cloud Manager
seo-title: Uso do Adobe AEM Cloud Manager
description: Interface do usuário do Gerenciador do AEM Cloud explicado
seo-description: Interface do usuário do Gerenciador do Adobe AEM Cloud explicado
page-status-flag: nunca ativado
uuid: cef 44 d 35-75 ed -44 bb -9636-2 de 2 bca 5 e 458
contentOwner: jsyal
discoiquuid: c 37566 d 5-0 d 1 b -4 c 44-abd 7-b 271 ea 443 c 1 a
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Usando o Experience Cloud Manager{#using-cloud-manager}

Esta seção explica a Interface do usuário (IU) para [!UICONTROL Cloud Manager] e explica o fluxo de trabalho da configuração do programa para a implantação de código seguida por verificações de qualidade.

## Pré-requisitos {#prerequisites}

Antes de entrar em detalhes de uso do [!UICONTROL Cloud Manager], recomenda-se seguir as seguintes seções:

* [Entendendo os conceitos antes de usar [! Gerenciador de nuvem UICONTROL]](understanding-concepts.md)
* [Configuração das Configurações Gerais para [! Gerenciador de nuvem UICONTROL]](setting-configurations-for-cloud-manager.md)

## Introdução ao [!UICONTROL Cloud Manager]{#getting-started-with-cloud-manager}

Depois de configurar as configurações gerais, [!UICONTROL Cloud Manager]você estará pronto para usar [!UICONTROL Cloud Manager]o.

1. Faça logon na Adobe [!UICONTROL Experience Cloud] e você verá a lista de soluções.

   ![](assets/screen_shot_2018-04-22at92951am.png)

1. Selecione o programa e clique no ícone superior esquerdo para abrir [!UICONTROL Cloud Manager].

   ![](assets/screen_shot_2018-04-22at93346am.png)

## Configuração do programa {#setting-up-program}

Após a integração, o proprietário do negócio precisará fazer uma configuração inicial do programa. Isso envolve definir a descrição do programa e definir os kpis que serão usados para testes de desempenho. Opcionalmente, uma miniatura pode ser carregada.

Os kpis definidas servem como uma linha de base para o teste de desempenho passado cada vez que o pipeline é executado.

>[!NOTE]
>
>Os kpis definidos são medidos nos testes executados no ambiente **stage** . Normalmente, esses kpis são reduzidos para se ajustar aos recursos do ambiente stage.
>
>Por exemplo, um usuário esperando uma média de 1000 exibições de página por minuto no ambiente de produção e com quatro `dispatcher/publish` servidores na produção deve dimensionar isso para 250 visualizações de página por minuto (assumindo que o ambiente do palco consiste em apenas um par `dispatcher/publish` de servidor).
>
>Além disso, muitos usuários terão um CDN (Akamai, cloudfront) na frente do ambiente de produção. Como [!UICONTROL Cloud Manager] os testes com relação ao ambiente do palco diretamente, o KPI deve refletir somente o tráfego esperado para passar pelo CDN, ou seja, erros de cache. Geralmente, isso será um subconjunto relativamente pequeno do tráfego total de produção.

### Uso [!UICONTROL Cloud Manager] para definir kpis {#using-cloud-manager-to-define-kpis}

Siga as etapas abaixo para configurar o programa e definir kpis:

1. Clique em **Configuração Programa** para iniciar [!UICONTROL Cloud Manager]o processo de configuração.
1. A tela **Editar informações** do programa é exibida.

   Carregue uma miniatura em seu programa. Você também pode adicionar uma descrição relevante ao seu programa e clicar **em Avançar**.

1. A tela **Configurar usuários** é exibida.

   Você pode configurar suas funções e usuários de equipe. Clique em **Avançar**.

1. A tela **Configurar kpis** de negócios gerais é exibida.

   Você pode definir seus dois kpis (expectativas para cada implantação):

   1. O que é o 95 º tempo de resposta de percentil aceitável para você?

      1. Valor recomendado - 3 segundos
   1. Quantas exibições de página por minuto abaixo do pico de pico?

      1. Valor recomendado - 200 pv/m


1. Clique **em Enviar** para concluir o assistente de configuração.

   Você verá a tela inicial para [!UICONTROL Cloud Manager] alterar **a Implantação**.

## Ambientes disponíveis {#available-environments}

Os Ambientes **disponíveis** na [!UICONTROL Cloud Manager] lista de todos os ambientes AEM gerenciados.

Cada um dos ambientes listados terá um status associado a ele.

## Configuração do pipeline {#configuring-pipeline}

### Configuração do pipeline {#setting-up-pipeline}

>[!CAUTION]
>
>O pipeline não pode ser configurado até que o repositório git tenha pelo menos um ramificação.

Antes de começar a implantar seu código, você deve configurar as configurações do seu pipeline a partir do [!UICONTROL Cloud Manager].

Para saber mais sobre a configuração do pipeline, consulte **a seção Visão geral** do pipeline em** [Compreensão de conceitos antes de usar [! UICONTROL Cloud Manager]](understanding-concepts.md)**.

>[!NOTE]
>
>É possível alterar as configurações do pipeline após a configuração inicial.

### Configuração das Configurações do pipeline da [!UICONTROL Cloud Manager]{#configuring-pipeline-settings-from-the-cloud-manager}

Siga as etapas abaixo para [!UICONTROL Cloud Manager] configurar o bahavior e as preferências do seu pipeline:

1. Acesse a guia **Ramificação** para configurar o ramo do aplicativo.

   Selecione o ramo de git que você deseja configurar.

   >[!NOTE]
   >
   >As ramificações encontradas no repositório Git são vinculadas ao seu programa.

   ![](assets/screen_shot_2018-05-06at73604pm.png)

1. Acesse **a** guia Ambientes para selecionar **opções de Palco** e **Produção** .

   É possível definir o acionador que iniciará o pipeline:

   * **Manual** - alguém precisa clicar manualmente na interface do usuário para iniciar o pipeline.
   Agora, você define os parâmetros que controlam a implantação de produção. As três opções disponíveis são as seguintes:

   * **Usar aprovação em tempo real**- uma implantação deve ser aprovada manualmente por um proprietário de negócios, gerente de projeto ou gerente de implantação por meio da [!UICONTROL Cloud Manager] interface do usuário.
   * **Use a CSE Monitoring** - a CSE está envolvida para iniciar a implantação.
   ![](assets/screen_shot_2018-05-06at73715pm.png)

1. Acesse a **guia Teste** para definir seus critérios de teste para o programa.

   Agora, você pode configurar os parâmetros de teste de desempenho.

   ![](assets/screen_shot_2018-05-06at73750pm.png)

## Implantação do código {#deploying-code}

Depois de configurar o pipeline (repositório, ambiente e ambiente de teste), você está pronto para implantar seu código.

### Implantação do código a partir de [!UICONTROL Cloud Manager]{#deploying-code-from-cloud-manager}

Siga as etapas abaixo para implantar seu código no ambiente de produção:

1. Clique **em Implantar** a partir do [!UICONTROL Cloud Manager] processo de implantação.
1. A **tela Implantação** do palco é exibida.

   Clique **em Criar** para iniciar o processo.

1. O processo de compilação completo considera vários parâmetros para verificar e implantar seu código.

   Os seguintes parâmetros marcados são os seguintes:

   **Implantação do palco**

   * Repositório
   * Teste de unidade
   * Digitalização de código
   * Implantado no ambiente do palco
   **Teste de pré-produção**

   * Teste de segurança
   * Teste de desempenho
   >[!NOTE]
   >
   >Além disso, você pode exibir registros ou revisar os resultados dos critérios de teste mencionados acima.

## Resultados de verificações de qualidade {#results-from-quality-checks}

Há três passagens no pipeline: Qualidade do código, teste de desempenho e teste de segurança.

Para cada uma dessas porturas, há uma estrutura de três níveis para problemas identificados pelo portfólio.

* **Importante** - esses são problemas identificados pela portão que causam uma falha imediata do pipeline.
* **Importante** - esses são problemas identificados pela portão que fazem com que o pipeline insira um estado pausado. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode substituir os problemas, nesse caso, o pipeline continua ou pode aceitar os problemas, e nesse caso o pipeline é interrompido com uma falha.
* **Informações** - Esses são problemas identificados pela portão que são fornecidos exclusivamente para fins informativos e não afetam a execução do pipeline.

### Digitalização de código {#code-scanning}

![](assets/screen_shot_2018-04-22at101443am.png)

### Teste de desempenho {#performance-testing}

*O teste de desempenho* em [!UICONTROL Cloud Manager] é implementado usando um teste por 30 minutos.

Durante a configuração do pipeline, o gerenciador de implantação pode decidir quanto tráfego leva para cada grupo. Eles podem escolher em qualquer lugar de um a três grupos. A distribuição do tráfego é baseada no número de compartimentos selecionados, ou seja, se todos os três estiverem selecionados, 33% do total de exibições de página serão colocados em cada grupo; se duas estiverem selecionadas, 50% vai para cada conjunto; se uma estiver selecionada, 100% do tráfego vai para esse conjunto.

Por exemplo, digamos que há uma divisão de 50%/50% entre as páginas populares populares e novas páginas (neste exemplo, Outras páginas ativas não são usadas) e o conjunto Novas páginas contém 3000 páginas. As exibições de página por minuto KPI estão definidas como 200. Durante o período de teste de 30 minutos:

* Cada uma das 25 páginas no conjunto de Páginas ativas populares será atingida por 240 vezes - `((200 &#42; 0.5) / 25) &#42; 30 = 120`
* Cada uma das 3000 páginas no conjunto Novas páginas serão acessadas uma vez - `((200 &#42; 0.5) / 3000) &#42; 30 = 1`

![](assets/image2018-3-14_16-23-56.png)

### Métricas de teste de desempenho {#performance-test-metrics}

Durante o período de teste, várias métricas são capturadas e comparadas aos kpis definidas pelo proprietário do negócio ou pelas normas definidas pelo AMS.

Eles são relatados usando o sistema de rotação em três níveis da seguinte maneira:

### Portfólios de três níveis ao executar um pipeline {#three-tier-gates-while-running-a-pipeline}

Há três passagens no pipeline como Qualidade de código, Teste de desempenho e Teste de segurança.

Para cada uma dessas porturas, há uma estrutura de três níveis para os problemas identificados pela portão:

* **Crítica**: Esses são problemas identificados pela portão que causam uma falha imediata do pipeline.
* **Importante**: Esses são problemas identificados pela portão que fazem com que o pipeline insira um estado pausado. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode substituir os problemas, nesse caso, o pipeline continua ou pode aceitar os problemas, e nesse caso o pipeline é interrompido com uma falha.
* **Informações**: Esses são problemas identificados pela portão que são fornecidos exclusivamente para fins informativos e não afetam a execução do pipeline.

A tabela a seguir resume a matriz de teste de desempenho usando o sistema de rotação de três níveis:

| **Métrica** | **Categoria** | **Limite de falha** |
|---|---|---|
| Taxa de erro de solicitação de página % | Crítica | &gt;= 2% |
| Taxa de utilização da CPU | Crítica | &gt;= 80% |
| Tempo de espera do disco | Crítica | &gt;= 50% |
| Tempo de resposta de Percent5 percentil | Importante | &gt; = KPI de nível de programa |
| Tempo de resposta de pico | Importante | &gt; = 18 segundos |
| Exibições de página por minuto | Importante | &lt; KPI de nível de programa |
| Uso de largura de banda do disco | Importante | &gt;= 90% |
| Uso de largura de banda de rede | Importante | &gt;= 90% |
| Solicitações por minuto | Informações | &lt; 6000 |

### Teste de segurança {#security-testing}

[!UICONTROL Cloud Manager] executa as Verificações existentes *de segurança do AEM* no estágio após a implantação e relata seu status por meio da interface do usuário. Os resultados são agregados de todas as instâncias do AEM no ambiente.

Se qualquer uma das instâncias relatar uma falha para determinada verificação de integridade, o ambiente inteiro falhará essa verificação de integridade. Assim como com a Qualidade de código e o Teste de desempenho, essas verificações de integridade são organizadas em categorias e informadas usando o sistema de rotação em três níveis. A única distinção é que não há limite no caso de teste de segurança. Todas as verificações de integridade simplesmente passam ou falharam.

As verificações atuais são:

| **Verificação de integridade** | **Categoria** |
|---|---|
| Disponibilidade da API de anexo do firewall de desserialização | Crítica |
| Firewall de desserialização funcional | Crítica |
| Firewall de desserialização carregado | Crítica |
| Geração do nome do nó autorizada | Crítica |
| Contas padrão de logon | Crítica |
| Sling Get Servlet | Crítica |
| Configuração do Dispatcher do controle de qualidade | Crítica |
| Configuração do gerenciador de biblioteca HTML CQ | Crítica |
| Sling Java Script Handler | Crítica |
| Sling Jsp Script Handler | Crítica |
| Sling Referrer Filter | Crítica |
| Configuração do SSL | Crítica |
| Acesso padrão ao perfil de usuário | Crítica |
| Suporte do CRXDE | Importante |
| Verificação de integridade do DavEx | Importante |
| Pacotes de conteúdo de exemplo | Importante |
| Configuração de filtros WCM | Importante |
| Verificação de integridade do WebDAV | Importante |
| Configuração de servidor da Web | Importante |
| Reprodução e usuários de transporte | Informações |

### Implementação de verificação de qualidade por sonarqube {#quality-check-implementation-by-sonarqube}

Como parte do pipeline, conforme demonstrado acima, o código é digitalizado. Atualmente, isso é implementado por sonarqube. Temos 93 regras que são uma combinação de regras genéricas Java e regras específicas do AEM (incluindo alguns do conjunto de regras existente do Knowifide). Uma lista dessas regras pode ser encontrada aqui: [Regras sonarqube](assets/sonarqube-rules.xlsx)

A partir dessas regras, uma variedade de métricas é calculada, sendo que algumas são usadas como uma porta de qualidade antes de permitir uma implantação para o ambiente stage.

Estes são os limites atuais:

| Nome | Definição | Categoria | Limite de falha |
|--- |--- |--- |--- |
| Classificação de segurança | A = 0 Vulnerabilidade <br/>B = pelo menos 1 menor vulnerabilidade<br/> C = pelo menos 1 vulnerabilidade principal <br/>D = pelo menos 1 Vulnerabilidade crítica <br/>E = pelo menos 1 Vulnerability do bloqueador | Crítica | &lt; B |
| Classificação confiável | A = 0 Bug <br/>B = pelo menos 1 menor bug <br/>C = pelo menos 1 Bug principal <br/>D = pelo menos 1 Bug crítico E = pelo menos 1 Bug de bloqueador | Importante | &lt; C |
| Classificação de maintainability | O custo de reparo pendente para o código smells é: <br/><ul><li>&lt; = 5% do tempo que já passou no aplicativo, a classificação é A </li><li>entre 6 a 10% a classificação é B </li><li>entre 11 e 20% a classificação é um C </li><li>entre 21 e 50% a classificação é um D</li><li>qualquer coisa acima de 50% é um E</li></ul> | Importante | &lt; A |
| Cobertura | Uma combinação de cobertura de linha e cobertura de condição usando esta fórmula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`<br/>em que: CT = condições que foram avaliadas para&#39;true&#39;pelo menos uma vez <br/>CF = condições que foram avaliadas como&#39;false&#39;pelo menos uma vez <br/>LC = cover lines = lines_ to_ cover - uncovered_ lines <br/><br/> B = total de condições <br/>EL = o número total de linhas executáveis (linhas_ to_ capa) | Importante | &lt; 50% |
| Teste de unidade ignorado | Número de testes de unidade ignorados. | Informações | &gt; 1 |
| Problemas em aberto | Tipos de problemas gerais - Vulnerabilidades, erros e codificação de código | Informações | &gt; 1 |
| Linhas duplicadas | Número de linhas envolvidas em blocos duplicados. <br/>Para que um bloco de código seja considerado duplicado: <ul><li> **Projetos não Java:**</li><li>Deve haver pelo menos 100 tokens sucessivos e duplicados.</li><li>Esses tokens devem ser distribuídos pelo menos em: </li><li>30 linhas de código para COBOL </li><li>20 linhas de código para ABAP </li><li>10 linhas de código para outros idiomas</li></ul><ul><li>**Projetos Java:**</li><li> Deve haver pelo menos 10 declarações sucessivas e duplicadas, independentemente do número de tokens e linhas.</li></ul>Diferenças no recuo e em literais de string são ignoradas ao detectar duplicações. | Informações | &gt; 1% |

### Falsos positivos {#false-positives}

O processo de leitura de qualidade não é perfeito e, às vezes, identificará incorretamente os problemas que não são realmente problemáticos. Isso é chamado *de falso positivo* (embora *falso negativo* provavelmente seria mais semanticamente correto). Nesses casos, o código fonte pode ser anotado com a anotação padrão Java `@SuppressWarnings` que especifica a ID da regra como o atributo de anotação. Por exemplo, um problema comum é que a regra sonarqube para detectar senhas codificadas é muito liberal sobre o que considera uma senha codificada.

Para ver um exemplo específico, esse código seria muito comum em um projeto do AEM que tinha código para se conectar a algum serviço externo:

```java
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

Sonarqube vai levantar isso como uma Vulnerabilidade de bloqueador. Nesse caso, o cliente pode identificar que essa não é uma vulnerabilidade e anotar isso com a ID da regra apropriada:

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

No entanto, por outro lado, se o código foi, na verdade:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String SERVICE_PASSWORD = "password";
```

Em seguida, o cliente deve considerar o aviso sonarqube como coração e remover a senha codificada. Contudo, eles ainda precisarão adicionar a `@SuppressWarnings` anotação, pois a regra sonarqube está sendo acionada pelo termo `password`.

>[!NOTE]
>
>É uma prática recomendada tornar a `@SuppressWarnings` anotação o mais específica possível, isto é, anotar apenas a declaração ou bloco específico que causa o problema, é possível anotar em nível de classe.

