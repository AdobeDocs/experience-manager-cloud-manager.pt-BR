---
title: Entender os resultados de teste
seo-title: Entender os resultados de teste
description: Saiba mais sobre portas de três camadas ao executar um pipeline no Cloud Manager
seo-description: Siga esta página para saber mais sobre portas de três níveis ao executar um pipeline, verificação de código, desempenho e testes de segurança que validam seu programa no Cloud Manager.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 7%

---


# Entender os resultados de teste {#understand-your-test-results}

Durante a execução do pipeline, várias métricas são capturadas e comparadas com os Indicadores-chave de desempenho (KPIs) definidos pelo proprietário do negócio ou com os padrões definidos pelo Adobe Managed Services.

Elas são reportadas usando o sistema de marcação de três níveis conforme definido nesta seção.

## Portas de três níveis ao executar um pipeline {#three-tier-gates-while-running-a-pipeline}

Há três portas no pipeline:

* Qualidade do código
* Teste de desempenho
* Teste de segurança

Para cada uma dessas portas, existe uma estrutura em três níveis para as questões identificadas pela porta.

* **Crítico**  - São problemas identificados pela porta que causam uma falha imediata do pipeline.
* **Importante** : esses são problemas identificados pela porta que fazem com que o pipeline entre em um estado pausado. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode substituir os problemas, caso o pipeline continue, ou pode aceitar os problemas, caso o pipeline pare com uma falha.
* **Informações**  - São problemas identificados pela porta, que são fornecidos apenas para fins informativos e não têm impacto na execução do pipeline.

>[!NOTE]
>
>Em um pipeline somente de qualidade de código, falhas importantes na porta de testes de qualidade do código não podem ser substituídas, pois a etapa Teste de qualidade do código é a etapa final no pipeline.

## Teste de qualidade do código {#code-quality-testing}

Esta etapa avalia a qualidade do código de seu aplicativo. É o objetivo principal de um pipeline somente de qualidade de código e é executado imediatamente após a etapa de build em todos os pipelines de não produção e produção. Consulte [Configuração do pipeline de CI-CD](/help/using/configuring-pipeline.md) para saber mais sobre diferentes tipos de pipelines.

### Noções básicas sobre o teste de qualidade do código {#understanding-code-quality-testing}

Em Teste de qualidade do código, o código-fonte é digitalizado para garantir que atenda a determinados critérios de qualidade. Atualmente, isso é implementado por uma combinação de SonarQube, exame de nível de pacote de conteúdo usando OakPAL e validação do dispatcher usando a Ferramenta de Otimização do Dispatcher. Há mais de 100 regras que combinam regras Java genéricas e regras específicas de AEM. Algumas das regras específicas do AEM são criadas com base nas práticas recomendadas AEM engenharia e são chamadas de [Regras de qualidade de código personalizadas](/help/using/custom-code-quality-rules.md).

>[!NOTE]
>Você pode baixar a lista completa de regras [aqui](/help/using/assets/CodeQuality-rules-AMS.xlsx).

Os resultados desta etapa são fornecidos como *Rating*. A tabela abaixo resume as classificações para vários critérios de teste:

| Nome | Definição | Categoria | Limite de Falhas |
|--- |--- |--- |--- |
| Classificação de segurança | A = 0 Vulnerabilidade <br/>B = pelo menos 1 Menor Vulnerabilidade<br/> C = pelo menos 1 Maior Vulnerabilidade <br/>D = pelo menos 1 Vulnerabilidade Crítica <br/>E = pelo menos 1 Vulnerabilidade do Bloqueador | Crítico | &lt; B |
| Classificação da confiabilidade | A = 0 Bug <br/>B = pelo menos 1 Bug Menor <br/>C = pelo menos 1 Bug Major <br/>D = pelo menos 1 Bug Crítico<br/>E = pelo menos 1 Bug Bloqueador | Importante | &lt; C |
| Classificação da capacidade de manutenção | O custo excepcional da correção para cheiros de código é: <br/><ul><li>&lt;> </li><li>entre 6 e 10%, a classificação é de </li><li>entre 11 e 20% a classificação é de C </li><li>entre 21 e 50%, a classificação é de D</li><li>qualquer coisa acima de 50% é um E</li></ul> | Importante | &lt; A |
| Cobertura | Uma combinação da cobertura da linha de ensaio da unidade e da cobertura da condição utilizando esta fórmula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>em que: CT = condições que foram avaliadas como &#39;true&#39; pelo menos uma vez durante a execução de testes de unidade <br/>CF = condições que foram avaliadas como &#39;false&#39; pelo menos uma vez durante a execução de testes de unidade <br/>LC = linhas cobertas = linhas_to_cover - linhas_não cobertas <br/><br/> B = número total de condições <br/>EL = número total de linhas executáveis (lines_to_cover) | Importante | &lt; 50% |
| Testes de Unidade Ignorados | Número de testes de unidade ignorados. | Informações | > 1 |
| Problemas em aberto | Tipos de problemas gerais - Vulnerabilidades, Erros e Cheiros de código | Informações | > 0 |
| Linhas Duplicadas | Número de linhas envolvidas em blocos duplicados. <br/>Para que um bloco de código seja considerado como duplicado:  <br/><ul><li>**Projetos não Java:**</li><li>Deve haver pelo menos 100 tokens sucessivos e duplicados.</li><li>Esses tokens devem ser distribuídos pelo menos em: </li><li>30 linhas de código para COBOL </li><li>20 linhas de código para ABAP </li><li>10 linhas de código para outras línguas</li><li>**Projetos Java:**</li><li> Deve haver pelo menos 10 declarações sucessivas e duplicadas, independentemente do número de tokens e linhas.</li></ul> <br/>As diferenças no recuo, bem como nos literais de string são ignoradas ao detectar duplicações. | Informações | > 1% |
| Compatibilidade Cloud Service | Número de problemas de compatibilidade de Cloud Service identificados. | Informações | > 0 |


>[!NOTE]
>
>Consulte [Definições de métrica](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) para obter definições mais detalhadas.

>[!NOTE]
>
>Para saber mais sobre as regras de qualidade do código personalizado executadas por [!UICONTROL Cloud Manager], consulte [Regras de qualidade de código personalizadas](custom-code-quality-rules.md).

### Lidar com falsos positivos {#dealing-with-false-positives}

O processo de verificação da qualidade não é perfeito e, por vezes, identifica incorretamente questões que não são realmente problemáticas. Isso é chamado de &quot;falso positivo&quot;.

Nesses casos, o código-fonte pode ser anotado com a anotação Java padrão `@SuppressWarnings` especificando a ID da regra como o atributo de anotação. Por exemplo, um problema comum é que a regra SonarQube para detectar senhas codificadas pode ser agressiva sobre como uma senha codificada é identificada.

Para observar um exemplo específico, esse código seria bastante comum em um projeto AEM que tem código para se conectar a algum serviço externo:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube aumentará a Vulnerabilidade do Bloqueador. Após revisar o código, você identifica que isso não é uma vulnerabilidade e pode anotar com a ID de regra apropriada.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

No entanto, por outro lado, se o código era realmente este:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Em seguida, a solução correta é remover a senha codificada.

>[!NOTE]
>
>Embora seja uma prática recomendada tornar a anotação `@SuppressWarnings` o mais específica possível, ou seja, anotar apenas a declaração ou bloco específico que causa o problema, é possível anotar em nível de classe.

## Teste de segurança {#security-testing}

[!UICONTROL Cloud Manager] executa o estágio  ***AEM Security Heath*** Checkson existente após a implantação e relata o status pela interface do usuário. Os resultados são agregados de todas as instâncias AEM no ambiente.

Se qualquer um dos relatórios **Instâncias** falhar em uma determinada verificação de integridade, todo o **Ambiente** falhará nessa verificação de integridade. Como acontece com o teste de qualidade e desempenho do código, essas verificações de integridade são organizadas em categorias e relatadas por meio do sistema de marcação de três níveis. A única distinção é que não existe qualquer limiar no caso dos testes de segurança. Todos os controlos de saúde são pura e simplesmente aprovados ou reprovados.

A tabela a seguir lista as verificações atuais:

| **Nome** | **Implementação de verificação de integridade** | **Categoria** |
|---|---|---|
| A opção Anexar disponibilidade da API do firewall de desserialização está em um estado aceitável | Disponibilidade da API de anexo do firewall de desserialização | Crítico |
| O firewall de desserialização está funcionando | Firewall de desserialização funcional | Crítico |
| O firewall de desserialização é carregado | Firewall de desserialização carregado | Crítico |
| A implementação AuthorizableNodeName não expõe a ID autorizável no nome/caminho do nó. | Geração do nome do nó autorizada | Crítico |
| As senhas padrão foram alteradas | Contas padrão de logon | Crítico |
| O servlet de GET padrão Sling é protegido contra ataques de DOS. | Sling Get Servlet | Crítico |
| O Manipulador de Sling Java Script está configurado adequadamente | Sling Java Script Handler | Crítico |
| O Manipulador de Script JSP do Sling está configurado adequadamente | Manipulador de script JSP Sling | Crítico |
| O SSL está configurado corretamente | Configuração do SSL | Crítico |
| Nenhuma política de perfil de usuário obviamente insegura encontrada | Acesso padrão ao perfil de usuário | Crítico |
| O Sling Referrer Filter é configurado para impedir ataques de CSRF | Sling Referrer Filter | Importante |
| O Gerenciador de biblioteca HTML do Adobe Granite está configurado adequadamente | Configuração do gerenciador de biblioteca HTML CQ | Importante |
| O pacote de suporte CRXDE está desativado | Suporte do CRXDE | Importante |
| O pacote e o servlet Sling DavEx estão desativados | Verificação de integridade do DavEx | Importante |
| O conteúdo de amostra não está instalado | Pacotes de conteúdo de exemplo | Importante |
| O Filtro de Solicitação WCM e o Filtro de Depuração do WCM estão desativados | Configuração de filtros WCM | Importante |
| O pacote e o servlet do Sling WebDAV estão configurados adequadamente | Verificação de integridade do WebDAV | Importante |
| O servidor da Web está configurado para impedir o clickjacking | Configuração de servidor da Web | Importante |
| A replicação não está usando o usuário &#39;admin&#39; | Reprodução e usuários de transporte | Informações |

## Teste de desempenho {#performance-testing}

*O* teste de desempenho  [!UICONTROL Cloud Manager] é implementado com o uso de um teste de 30 minutos.

Durante a configuração do pipeline, o gerente de implantação pode decidir quanto tráfego direcionar para cada bucket.

Você pode saber mais sobre controles de bucket, em [Configurar o pipeline de CI/CD](configuring-pipeline.md).

>[!NOTE]
>
>Para configurar seu programa e definir seus KPIs, consulte [Configurar seu programa](setting-up-program.md).

A tabela a seguir resume a matriz de teste de desempenho usando o sistema de marcação de três níveis:

| **Métrica** | **Categoria** | **Limite de Falhas** |
|---|---|---|
| Taxa de Erro de Solicitação de Página % | Crítico | >= 2% |
| Taxa de Utilização da CPU | Crítico | >= 80% |
| Tempo de espera de E/S de disco | Crítico | >= 50% |
| Tempo de Resposta de 95% | Importante | >= KPI de nível de programa |
| Tempo de Resposta Pico | Importante | >= 18 segundos |
| Exibições de página por minuto | Importante | &lt; Program-level=&quot;&quot; KPI=&quot;&quot;> |
| Utilização da Largura de Banda do Disco | Importante | >= 90% |
| Utilização da largura de banda da rede | Importante | >= 90% |
| Solicitações por minuto | Informações | >= 6000 |

### Gráficos de resultados de testes de desempenho {#performance-testing-results-graphs}

Novos gráficos e opções de download foram adicionados à caixa de diálogo Resultados do teste de desempenho .

Ao abrir a caixa de diálogo Teste de desempenho , os painéis de métrica podem ser expandidos para exibir um gráfico, fornecer um link para um download ou ambos.

Para [!UICONTROL Cloud Manager] Versão 2018.7.0, essa funcionalidade está disponível para as seguintes métricas:

* **Utilização da CPU**
   * Gráfico de Utilização da CPU durante o período de teste.

* **Tempo de espera de E/S de disco**
   * Um gráfico de Tempo de Espera de E/S de Disco durante o período de teste.

* **Taxa de erro da página**
   * Um gráfico de erros de página por minuto durante o período de teste.
   * Um arquivo CSV que lista páginas que geraram um erro durante o teste.

* **Utilização da Largura de Banda do Disco**
   * Gráfico de Utilização da Largura de Banda do Disco durante o período de teste.

* **Utilização da largura de banda da rede**
   * Gráfico de Utilização da Largura de Banda da Rede durante o período de teste.

* **Tempo de Resposta Pico**
   * Um gráfico do tempo de resposta de pico por minuto durante o período de teste.

* **95º Tempo de resposta do percentual**
   * Gráfico do 95º percentil de tempo de resposta por minuto durante o período de teste.
   * Um arquivo CSV que lista páginas cujo tempo de resposta do percentil 95 excedeu o KPI definido.

As imagens a seguir exibem os gráficos de teste de desempenho:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

