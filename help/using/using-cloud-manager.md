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
source-git-commit: 4c1c6786db9b8972f9315bd2f12fc1752881492f

---


# Using Cloud Manager{#using-cloud-manager}

This section explains the User Interface (UI) for [!UICONTROL Cloud Manager] and explains the workflow from setting up the program to code deployment followed by quality checks.

## Pré-requisitos {#prerequisites}

Before you get into the details of using the [!UICONTROL Cloud Manager], it is recommended to go though the following sections:

* [Entendendo os conceitos antes de usar [! Gerenciador de nuvem UICONTROL]](understanding-concepts.md)
* [Configuração das Configurações Gerais para [! Gerenciador de nuvem UICONTROL]](setting-configurations-for-cloud-manager.md)

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Once you have setup the general configurations for [!UICONTROL Cloud Manager], you are ready to use the [!UICONTROL Cloud Manager].

1. Log in to the Adobe [!UICONTROL Experience Cloud] and you will see the list of solutions.

   ![](assets/screen_shot_2018-04-22at92951am.png)

1. Select the program and click on the top left icon to open [!UICONTROL Cloud Manager].

   ![](assets/screen_shot_2018-04-22at93346am.png)

## Setting Up Program {#setting-up-program}

Após a integração, o proprietário do negócio precisará fazer uma configuração inicial do programa. Isso envolve definir a descrição do programa e definir os kpis que serão usados para testes de desempenho. Opcionalmente, uma miniatura pode ser carregada.

Os kpis definidas servem como uma linha de base para o teste de desempenho passado cada vez que o pipeline é executado.

>[!NOTE]
>
>The KPIs defined are measured on tests run on the **stage** environment. Normalmente, esses kpis são reduzidos para se ajustar aos recursos do ambiente stage.
>
>For example, a user expecting an average of 1000 page views per minute in their production environment and having four `dispatcher/publish` servers in production should scale this to 250 page views per minute (assuming their stage environment consists of only a single `dispatcher/publish` server pair).
>
>Além disso, muitos usuários terão um CDN (Akamai, cloudfront) na frente do ambiente de produção. Since [!UICONTROL Cloud Manager] tests against the stage environment directly, the KPI should reflect only the traffic expected to pass through the CDN, that is, the cache misses. Geralmente, isso será um subconjunto relativamente pequeno do tráfego total de produção.

### Using [!UICONTROL Cloud Manager] to define KPIs {#using-cloud-manager-to-define-kpis}

Siga as etapas abaixo para configurar o programa e definir kpis:

1. Click **Setup Program** to start the setup process in [!UICONTROL Cloud Manager].
1. The **Edit Program Information** screen displays.

   Carregue uma miniatura em seu programa. You can also add a relevant description to your program and click **Next**.

1. The **Configure Users** screen displays.

   Você pode configurar suas funções e usuários de equipe. Clique em **Avançar**.

1. The **Configure General Business KPIs** screen displays.

   Você pode definir seus dois kpis (expectativas para cada implantação):

   1. O que é o 95 º tempo de resposta de percentil aceitável para você?

      1. Valor recomendado - 3 segundos
   1. Quantas exibições de página por minuto abaixo do pico de pico?

      1. Valor recomendado - 200 pv/m


1. Click **Submit** to complete the setup wizard.

   You will see the home screen for [!UICONTROL Cloud Manager] change to **Deploy**.

## Available Environments {#available-environments}

The **Available Environments** in the [!UICONTROL Cloud Manager] lists all the managed AEM environments.

Cada um dos ambientes listados terá um status associado a ele.

## Configuring Pipeline {#configuring-pipeline}

### Setting up Pipeline {#setting-up-pipeline}

>[!CAUTION]
>
>O pipeline não pode ser configurado até que o repositório git tenha pelo menos um ramificação.

Before you start to deploy your code, you must configure your pipeline settings from the [!UICONTROL Cloud Manager].

To learn more about pipeline configuration, see **Pipeline Overview** section in ** [Understanding Concepts before Using [!UICONTROL Cloud Manager]](understanding-concepts.md)**.

>[!NOTE]
>
>É possível alterar as configurações do pipeline após a configuração inicial.

### Configuring Pipeline Settings from the [!UICONTROL Cloud Manager] {#configuring-pipeline-settings-from-the-cloud-manager}

Follow the steps below from the [!UICONTROL Cloud Manager] to configure the bahavior and preferences for your pipeline:

1. Access the **Branch** tab to set up the application branch.

   Selecione o ramo de git que você deseja configurar.

   >[!NOTE]
   >
   >As ramificações encontradas no repositório Git são vinculadas ao seu programa.

   ![](assets/screen_shot_2018-05-06at73604pm.png)

1. Access the **Environments** tab to select **Stage** and **Production** options.

   É possível definir o acionador que iniciará o pipeline:

   * **Manual** - alguém precisa clicar manualmente na interface do usuário para iniciar o pipeline.
   Agora, você define os parâmetros que controlam a implantação de produção. As três opções disponíveis são as seguintes:

   * **Usar aprovação em tempo real**- uma implantação deve ser aprovada manualmente por um proprietário de negócios, gerente de projeto ou gerente de implantação por meio da [!UICONTROL Cloud Manager] interface do usuário.
   * **Use a CSE Monitoring** - a CSE está envolvida para iniciar a implantação.
   ![](assets/screen_shot_2018-05-06at73715pm.png)

1. Access the **Testing** tab to define your testing criteria for your program.

   Agora, você pode configurar os parâmetros de teste de desempenho.

   ![](assets/screen_shot_2018-05-06at73750pm.png)

## Deploying Code {#deploying-code}

Depois de configurar o pipeline (repositório, ambiente e ambiente de teste), você está pronto para implantar seu código.

### Deploying Code from [!UICONTROL Cloud Manager] {#deploying-code-from-cloud-manager}

Siga as etapas abaixo para implantar seu código no ambiente de produção:

1. Click **Deploy** from the [!UICONTROL Cloud Manager] to start the deployment process.
1. The **Stage Deployment** screen displays.

   Click **Build** to start the process.

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

## Results from Quality Checks {#results-from-quality-checks}

Há três passagens no pipeline: Qualidade do código, teste de desempenho e teste de segurança.

Para cada uma dessas porturas, há uma estrutura de três níveis para problemas identificados pelo portfólio.

* **Importante** - esses são problemas identificados pela portão que causam uma falha imediata do pipeline.
* **Importante** - esses são problemas identificados pela portão que fazem com que o pipeline insira um estado pausado. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode substituir os problemas, nesse caso, o pipeline continua ou pode aceitar os problemas, e nesse caso o pipeline é interrompido com uma falha.
* **Informações** - Esses são problemas identificados pela portão que são fornecidos exclusivamente para fins informativos e não afetam a execução do pipeline.

### Code Scanning {#code-scanning}

![](assets/screen_shot_2018-04-22at101443am.png)

### Performance Testing {#performance-testing}

*O teste de desempenho* em [!UICONTROL Cloud Manager] é implementado usando um teste por 30 minutos.

Durante a configuração do pipeline, o gerenciador de implantação pode decidir quanto tráfego leva para cada grupo. Eles podem escolher em qualquer lugar de um a três grupos. A distribuição do tráfego é baseada no número de compartimentos selecionados, ou seja, se todos os três estiverem selecionados, 33% do total de exibições de página serão colocados em cada grupo; se duas estiverem selecionadas, 50% vai para cada conjunto; se uma estiver selecionada, 100% do tráfego vai para esse conjunto.

Por exemplo, digamos que há uma divisão de 50%/50% entre as páginas populares populares e novas páginas (neste exemplo, Outras páginas ativas não são usadas) e o conjunto Novas páginas contém 3000 páginas. As exibições de página por minuto KPI estão definidas como 200. Durante o período de teste de 30 minutos:

* Each of the 25 pages in the Popular Live Pages set will be hit 240 times - `((200 &#42; 0.5) / 25) &#42; 30 = 120`
* Each of the 3000 pages in the New Pages set will be hit once - `((200 &#42; 0.5) / 3000) &#42; 30 = 1`

![](assets/image2018-3-14_16-23-56.png)

### Performance Test Metrics {#performance-test-metrics}

Durante o período de teste, várias métricas são capturadas e comparadas aos kpis definidas pelo proprietário do negócio ou pelas normas definidas pelo AMS.

Eles são relatados usando o sistema de rotação em três níveis da seguinte maneira:

### Three-Tier Gates while Running a Pipeline {#three-tier-gates-while-running-a-pipeline}

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

### Security Testing {#security-testing}

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

### Quality Check Implementation by SonarQube {#quality-check-implementation-by-sonarqube}

Como parte do pipeline, conforme demonstrado acima, o código é digitalizado. Atualmente, isso é implementado por sonarqube. Temos 93 regras que são uma combinação de regras genéricas Java e regras específicas do AEM (incluindo alguns do conjunto de regras existente do Knowifide). A list of these rules can be found here: [code-quality-rules.xlsx](/help/using/assets/code-quality-rules.xlsx)

A partir dessas regras, uma variedade de métricas é calculada, sendo que algumas são usadas como uma porta de qualidade antes de permitir uma implantação para o ambiente stage.

Estes são os limites atuais:

| Nome | Definição | Categoria | Limite de falha |
|--- |--- |--- |--- |
| Classificação de segurança | A = 0 Vulnerability <br/>B = at least 1 Minor Vulnerability<br/> C = at least 1 Major Vulnerability <br/>D = at least 1 Critical Vulnerability <br/>E = at least 1 Blocker Vulnerability | Crítica | &lt; B |
| Classificação confiável | A = 0 Bug <br/>B = at least 1 Minor Bug <br/>C = at least 1 Major Bug <br/>D = at least 1 Critical Bug E = at least 1 Blocker Bug | Importante | &lt; C |
| Classificação de maintainability | Outstanding remediation cost for code smells is: <br/><ul><li>&lt; = 5% do tempo que já passou no aplicativo, a classificação é A </li><li>entre 6 a 10% a classificação é B </li><li>entre 11 e 20% a classificação é um C </li><li>entre 21 e 50% a classificação é um D</li><li>qualquer coisa acima de 50% é um E</li></ul> | Importante | &lt; A |
| Cobertura | A mix of line coverage and condition coverage using this formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where: CT = conditions that have been evaluated to &#39;true&#39; at least once <br/>CF = conditions that have been evaluated to &#39;false&#39; at least once <br/>LC = covered lines = lines_to_cover - uncovered_lines <br/><br/> B = total number of conditions <br/>EL = total number of executable lines (lines_to_cover) | Importante | &lt; 50% |
| Teste de unidade ignorado | Número de testes de unidade ignorados. | Informações | &gt; 1 |
| Problemas em aberto | Tipos de problemas gerais - Vulnerabilidades, erros e codificação de código | Informações | &gt; 1 |
| Linhas duplicadas | Número de linhas envolvidas em blocos duplicados. <br/>Para que um bloco de código seja considerado duplicado: <ul><li> **Projetos não Java:**</li><li>Deve haver pelo menos 100 tokens sucessivos e duplicados.</li><li>Esses tokens devem ser distribuídos pelo menos em: </li><li>30 linhas de código para COBOL </li><li>20 linhas de código para ABAP </li><li>10 linhas de código para outros idiomas</li></ul><ul><li>**Projetos Java:**</li><li> Deve haver pelo menos 10 declarações sucessivas e duplicadas, independentemente do número de tokens e linhas.</li></ul>Diferenças no recuo e em literais de string são ignoradas ao detectar duplicações. | Informações | &gt; 1% |

### False Positives {#false-positives}

O processo de leitura de qualidade não é perfeito e, às vezes, identificará incorretamente os problemas que não são realmente problemáticos. This is called a *false positive* (although *false negative* would probably be more semantically correct). In these cases, the source code can be annotated with the standard Java `@SuppressWarnings` annotation specifying the rule ID as the annotation attribute. Por exemplo, um problema comum é que a regra sonarqube para detectar senhas codificadas é muito liberal sobre o que considera uma senha codificada.

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

Em seguida, o cliente deve considerar o aviso sonarqube como coração e remover a senha codificada. They will still, however, need to add the `@SuppressWarnings` annotation since the SonarQube rule is actually being triggered by the term `password`.

>[!NOTE]
>
>It is a best practice to make the `@SuppressWarnings` annotation as specific as possible, i.e. annotate only the specific statement or block causing the issue, it is possible to annotate at a class level.

