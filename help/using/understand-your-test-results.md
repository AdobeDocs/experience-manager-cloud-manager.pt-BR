---
title: Entender os resultados do teste
seo-title: Entender os resultados do teste
description: 'null'
seo-description: Siga esta página para saber mais sobre três faixas de níveis ao executar um pipeline, digitalização de código, desempenho e testes de segurança validando seu programa no Cloud Manager.
uuid: 93 caa 01 f -0 df 2-4 a 6 f -81 dc -23 dfee 24 dc 93
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: usando
discoiquuid: 83299 ed 8-4 b 7 a -4 b 1 c-bd 56-1 bfc 7 e 7318 d 4
translation-type: tm+mt
source-git-commit: 4c1c6786db9b8972f9315bd2f12fc1752881492f

---


# Understand your Test Results {#understand-your-test-results}

During the **Pipeline** process, a number of metrics are captured and compared to either the Key Performance Indicators (KPIs) defined by the business owner, or standards set by Adobe Managed Services.

Eles são relatados usando o sistema de rotação de três níveis, conforme definido nesta seção.

## Three-Tier Gates while Running a Pipeline  {#three-tier-gates-while-running-a-pipeline}

Há três passagens no pipeline:

* Qualidade do código
* Teste de desempenho
* Teste de segurança

Para cada uma dessas porturas, há uma estrutura de três níveis para problemas identificados pelo portfólio.

* **Importante** - esses são problemas identificados pela portão que causam uma falha imediata do pipeline.
* **Importante** - esses são problemas identificados pela portão que fazem com que o pipeline insira um estado pausado. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode substituir os problemas, nesse caso, o pipeline continua ou pode aceitar os problemas, e nesse caso o pipeline é interrompido com uma falha.
* **Informações** - Esses são problemas identificados pela portão que são fornecidos exclusivamente para fins informativos e não afetam a execução do pipeline.

## Code Quality Testing {#code-quality-testing}

Como parte do pipeline, o código fonte é digitalizado para garantir que as implantações atendam a determinados critérios de qualidade. Atualmente, isso é implementado por uma combinação de sonarqube e de conteúdo de conteúdo a nível de pacote usando o oakpal. Há mais de 100 regras combinando regras genéricas Java e regras específicas do AEM. A tabela a seguir resume a classificação para critérios de teste:

| Nome | Definição | Categoria | Limite de falha |
|--- |--- |--- |--- |
| Classificação de segurança | A = 0 Vulnerability <br/>B = at least 1 Minor Vulnerability<br/> C = at least 1 Major Vulnerability <br/>D = at least 1 Critical Vulnerability <br/>E = at least 1 Blocker Vulnerability | Crítica | &lt; B |
| Classificação confiável | A = 0 Bug <br/>B = at least 1 Minor Bug <br/>C = at least 1 Major Bug <br/>D = at least 1 Critical Bug E = at least 1 Blocker Bug | Importante | &lt; C |
| Classificação de maintainability | Outstanding remediation cost for code smells is: <br/><ul><li>&lt; = 5% do tempo que já passou no aplicativo, a classificação é A </li><li>entre 6 a 10% a classificação é B </li><li>entre 11 e 20% a classificação é um C </li><li>entre 21 e 50% a classificação é um D</li><li>qualquer coisa acima de 50% é um E</li></ul> | Importante | &lt; A |
| Cobertura | A mix of unit test line coverage and condition coverage using this formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where: CT = conditions that have been evaluated to &#39;true&#39; at least once while running unit tests <br/>CF = conditions that have been evaluated to &#39;false&#39; at least once while running unit tests <br/>LC = covered lines = lines_to_cover - uncovered_lines <br/><br/> B = total number of conditions <br/>EL = total number of executable lines (lines_to_cover) | Importante | &lt; 50% |
| Teste de unidade ignorado | Número de testes de unidade ignorados. | Informações | &gt; 1 |
| Problemas em aberto | Tipos de problemas gerais - Vulnerabilidades, erros e codificação de código | Informações | &gt; 1 |
| Linhas duplicadas | Número de linhas envolvidas em blocos duplicados. <br/>Para que um bloco de código seja considerado duplicado: <br/><ul><li>**Projetos não Java:**</li><li>Deve haver pelo menos 100 tokens sucessivos e duplicados.</li><li>Esses tokens devem ser distribuídos pelo menos em: </li><li>30 linhas de código para COBOL </li><li>20 linhas de código para ABAP </li><li>10 linhas de código para outros idiomas</li><li>**Projetos Java:**</li><li> Deve haver pelo menos 10 declarações sucessivas e duplicadas, independentemente do número de tokens e linhas.</li></ul> <br/>Diferenças no recuo e em literais de string são ignoradas ao detectar duplicações. | Informações | &gt; 1% |


>[!NOTE]
>
>Refer to [Metric Definitions](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) for more detailed definitions.

You can download the list of rules here [code-quality-rules.xlsx](/help/using/assets/code-quality-rules.xlsx)

>[!NOTE]
>
>To learn more about the custom code quality rules executed by [!UICONTROL Cloud Manager], please refer to [Custom Code Quality Rules](custom-code-quality-rules.md).

### Dealing with False Positives {#dealing-with-false-positives}

O processo de leitura de qualidade não é perfeito e, às vezes, identificará incorretamente os problemas que não são realmente problemáticos. Isso é conhecido como &quot;falso positivo&quot;.

In these cases, the source code can be annotated with the standard Java `@SuppressWarnings` annotation specifying the rule ID as the annotation attribute. Por exemplo, um problema comum é que a regra sonarqube para detectar senhas codificadas pode ser agressiva sobre como uma senha codificada é identificada.

Para ver um exemplo específico, esse código seria muito comum em um projeto do AEM que tinha código para se conectar a algum serviço externo:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Sonarqube então aumentará uma Vulnerabilidade do bloqueador. Depois de revisar o código, você identifica que essa não é uma vulnerabilidade e pode anotar isso com a ID de regra apropriada.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

No entanto, por outro lado, se o código foi, na verdade:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Em seguida, a solução correta é remover a senha codificada.

>[!NOTE]
>
>While it is a best practice to make the `@SuppressWarnings` annotation as specific as possible, i.e. annotate only the specific statement or block causing the issue, it is possible to annotate at a class level.

## Security Testing {#security-testing}

[!UICONTROL Cloud Manager] executa as Verificações existentes ***de segurança do AEM*** no estágio após a implantação e relata o status por meio da interface do usuário. Os resultados são agregados de todas as instâncias do AEM no ambiente.

If any of the **Instances** report a failure for a given health check, the entire **Environment** fails that health check. Assim como com a Qualidade de código e o Teste de desempenho, essas verificações de integridade são organizadas em categorias e informadas usando o sistema de rotação em três níveis. A única distinção é que não há limite no caso de teste de segurança. Todas as verificações de integridade simplesmente passam ou falharam.

A tabela a seguir lista as verificações atuais:

| **Nome** | **Implementação de verificação de integridade** | **Categoria** |
|---|---|---|
| O firewall de desserialização Anexar a API está em um estado aceitável | Disponibilidade da API de anexo do firewall de desserialização | Crítica |
| O firewall de dessserialização está funcionando | Firewall de desserialização funcional | Crítica |
| O firewall de dessserialização é carregado | Firewall de desserialização carregado | Crítica |
| A implementação de authorizablenodename não expõe a ID autorizável no nome/caminho do nó. | Geração do nome do nó autorizada | Crítica |
| As senhas padrão foram alteradas | Contas padrão de logon | Crítica |
| O servlet GET de Sling é protegido contra ataques do DOS. | Sling Get Servlet | Crítica |
| O Dispatcher está filtrando solicitações corretamente | Configuração do Dispatcher do controle de qualidade | Crítica |
| O Adobe Granite HTML Library Manager está configurado adequadamente | Configuração do gerenciador de biblioteca HTML CQ | Crítica |
| O Sling Java Script Handler está configurado adequadamente | Sling Java Script Handler | Crítica |
| O Sling JSP Script Handler é configurado adequadamente | Sling JSP Script Handler | Crítica |
| O Filtro de referência de sling está configurado para impedir ataques CSRF | Sling Referrer Filter | Crítica |
| O SSL está configurado corretamente | Configuração do SSL | Crítica |
| Não há, obviamente, políticas de perfil de usuário inseguras encontradas | Acesso padrão ao perfil de usuário | Crítica |
| O pacote de suporte do CRXDE está desativado | Suporte do CRXDE | Importante |
| O pacote e o servlet Sling davex estão desativados | Verificação de integridade do DavEx | Importante |
| O conteúdo de amostra não está instalado | Pacotes de conteúdo de exemplo | Importante |
| O Filtro de solicitação WCM e o Filtro de depuração WCM estão desativados | Configuração de filtros WCM | Importante |
| O pacote e o servlet Sling webdav estão configurados adequadamente | Verificação de integridade do WebDAV | Importante |
| O servidor Web está configurado para impedir o clickjacking | Configuração de servidor da Web | Importante |
| A replicação não está usando o usuário &quot;admin&quot; | Reprodução e usuários de transporte | Informações |

## Performance Testing {#performance-testing}

*O teste de desempenho* em [!UICONTROL Cloud Manager] é implementado usando um teste de 30 minutos.

Durante a configuração do pipeline, o gerenciador de implantação pode decidir quanto tráfego leva para cada grupo.

You can learn more about bucket controls, from [Configure your CI/CD Pipeline](configuring-pipeline.md).

>[!NOTE]
>
>To setup your program and define your KPIs, see [Setup your Program](setting-up-program.md).

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

### Performance Testing Results Graphs {#performance-testing-results-graphs}

Novos gráficos e opções de download foram adicionados à caixa de diálogo Resultados do teste de desempenho.

Quando você abre a caixa de diálogo Teste de desempenho, os painéis de métricas podem ser expandidos para exibir um gráfico, fornecer um link para o download ou ambos.

For [!UICONTROL Cloud Manager] Release 2018.7.0, this functionality is available for the following metrics:

* **Utilização da CPU**
   * Um gráfico da utilização da CPU durante o período de teste.

* **Tempo de espera do disco E/E**
   * Um gráfico de Tempo de espera I/O durante o período de teste.

* **Taxa de erro de página**
   * Um gráfico de erros de página por minuto durante o período de teste.
   * Um arquivo CSV que lista páginas que produziram um erro durante o teste.

* **Uso de largura de banda do disco**
   * Um gráfico de utilização de largura de banda do disco durante o período de teste.

* **Uso de largura de banda de rede**
   * Um gráfico de utilização de largura de banda de rede durante o período de teste.

* **Tempo de resposta de pico**
   * Um gráfico de tempo de resposta por minuto durante o período de teste.

* **Tempo de resposta de Percent5 º percentil**
   * Um gráfico de 95% de tempo de resposta por minuto durante o período de teste.
   * Um arquivo CSV que lista páginas cujo time 5 º percentil de resposta excedeu o KPI definido.

As imagens a seguir exibem os gráficos de teste de desempenho:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

