---
title: Teste de qualidade do código
description: Saiba como o teste de qualidade de código de pipelines funciona e como ele pode melhorar a qualidade de suas implantações.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '2863'
ht-degree: 100%

---


# Teste de qualidade do código {#code-quality-testing}

Saiba como o teste de qualidade de código de pipelines funciona e como ele pode melhorar a qualidade de suas implantações.

## Introdução {#introduction}

Durante a execução do pipeline, várias métricas são capturadas e comparadas com os indicadores-chave de desempenho (KPIs) definidos pelo proprietário do negócio ou com os padrões definidos pelo Adobe Managed Services.

Estes dados são comunicados utilizando um sistema de classificação em três níveis.

## Classificações de três níveis {#three-tiered-ratings}

Há três portas no pipeline:

* Qualidade do código
* Teste de desempenho
* Teste de segurança

Para cada uma dessas portas, existe uma estrutura em três camadas para os problemas identificados pela porta.

* **Crítico** - São problemas que causam uma falha imediata do pipeline.
* **Importante** - Esses são problemas que fazem com que o pipeline entre no estado pausado. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode ignorar os problemas, caso no qual o pipeline continua, ou pode aceitar os problemas, caso no qual o pipeline para com uma falha. Ignorar falhas importantes está sujeito a um [tempo limite.](/help/using/code-deployment.md#timeouts)
* **Informações** - Estes são problemas que são apresentados exclusivamente para fins informativos e não têm impacto na execução do pipeline.

>[!NOTE]
>
>Em um pipeline somente de qualidade de código, falhas importantes na porta de qualidade do código não podem ser ignoradas, pois a etapa de teste de qualidade do código é a etapa final no pipeline.

## Teste de qualidade do código {#code-quality-testing-step}

Essa etapa avalia a qualidade do código do aplicativo, que é o objetivo principal de um pipeline somente de qualidade de código, e é executada imediatamente após a etapa de criação em todos os pipelines de não-produção e de produção. Consulte o documento [Configuração de pipeline de não produção](/help/using/non-production-pipelines.md) para saber mais.

O teste de qualidade do código verifica o código-fonte para garantir que ele atenda a determinados critérios de qualidade. Isso é implementado por uma combinação de análise do SonarQube, exame de nível de pacote de conteúdo usando o OakPAL e validação do Dispatcher usando a Ferramenta de otimização do Dispatcher.

Há mais de 100 regras que combinam regras do Java genéricas e regras específicas do AEM. Algumas das regras específicas do AEM são criadas com base nas práticas recomendadas da equipe de engenharia do AEM e são chamadas de [Regras de qualidade do código personalizado.](/help/using/custom-code-quality-rules.md)

>[!TIP]
>
>Você pode baixar a lista completa de regras [usando este link.](/help/assets/CodeQuality-rules-latest-AMS.xlsx)

Os resultados do teste de qualidade do código são fornecidos em forma de classificação, conforme resumido neste quadro.

| Nome | Definição | Categoria | Limite de falhas |
|--- |--- |--- |--- |
| Classificação de segurança | A = Sem vulnerabilidades<br/>B = Pelo menos 1 vulnerabilidade secundária<br/>C = Pelo menos 1 vulnerabilidade principal<br/>D = Pelo menos 1 vulnerabilidade crítica<br/>E = Pelo menos 1 vulnerabilidade bloqueadora | Crítico | &lt; B |
| Classificação da confiabilidade | A = Sem erros<br/>B = Pelo menos 1 erro secundário <br/>C = Pelo menos 1 erro primário<br/>D = Pelo menos 1 erro crítico<br/>E = Pelo menos 1 erro bloqueador | Importante | &lt; C |
| Classificação da capacidade de manutenção | Definido pelo custo de remediação pendente para code smells como uma porcentagem do tempo que já passou para o aplicativo<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | Importante | &lt; A |
| Cobertura | Definida por uma combinação de cobertura de linha de teste unitário e cobertura da condição utilizando a fórmula: <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Condições que foram avaliadas como `true` pelo menos uma vez durante a execução dos testes unitários</li><li>`CF` = Condições que foram avaliadas como `false` pelo menos uma vez durante a execução dos testes unitários</li><li>`LC` = Linhas cobertas = lines_to_cover - uncovered_lines</li><li>`B` = número total de condições</li><li>`EL` = número total de linhas executáveis (lines_to_cover)</li></ul> | Importante | &lt; 50% |
| Testes unitários ignorados | Número de testes de unidade ignorados | Informações | > 1 |
| Problemas em aberto | Tipos de problemas gerais - vulnerabilidades, erros e code smells | Informações | > 0 |
| Linhas duplicadas | Definido como o número de linhas envolvidas em blocos duplicados. Um bloco de código é considerado duplicado nas seguintes condições.<br>Projetos não Java:<ul><li>Deve haver pelo menos 100 tokens sucessivos e duplicados.</li><li>Esses tokens devem estar distribuídos em pelo menos: </li><li>30 linhas de código para COBOL </li><li>20 linhas de código para ABAP </li><li>10 linhas de código para outras linguagens</li></ul>Projetos Java:<ul></li><li> Deve haver pelo menos 10 declarações sucessivas e duplicadas, independentemente do número de tokens e linhas.</li></ul>As diferenças no recuo, bem como nos literais de string são ignoradas ao detectar duplicadas. | Informações | > 1% |
| Compatibilidade do Cloud Service | Número de problemas de compatibilidade do Cloud Service identificados | Informações | > 0 |

>[!NOTE]
>
>Consulte as [Definições de métrica da SonarQube](https://docs.sonarqube.org/latest/user-guide/metric-definitions/) para obter informações mais detalhadas.

>[!NOTE]
>
>Para saber mais sobre as regras de qualidade do código personalizado executadas pelo [!UICONTROL Cloud Manager], consulte o documento [Regras de qualidade do código personalizado.](custom-code-quality-rules.md)

### Lidar com falsos positivos {#dealing-with-false-positives}

O processo de verificação da qualidade não é perfeito e, por vezes, identifica incorretamente questões que não são realmente problemáticas. Isso é chamado de falso positivo.

Nesses casos, o código-fonte pode ser anotado com a anotação Java padrão `@SuppressWarnings`, especificando a ID da regra como o atributo de anotação. Por exemplo, um falso positivo comum é que a regra do SonarQube para detectar senhas fixas no código pode ser agressiva sobre como uma senha fixa no código é identificada.

O código a seguir é bastante comum em um projeto do AEM, que tem código para se conectar a algum serviço externo.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

O SonarQube levantará uma vulnerabilidade do bloqueador. Mas, depois de revisar o código, você percebe que isso não é uma vulnerabilidade e pode anotar o código com a ID de regra apropriada.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

No entanto, se o código fosse na verdade este:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Então, a solução correta seria remover a senha fixa no código.

>[!NOTE]
>
>Embora seja recomendado fazer a anotação `@SuppressWarnings` a mais específica possível (ou seja, anotar apenas a declaração ou bloco específico que causa o problema), é possível anotar em nível de classe.

## Teste de segurança {#security-testing}

O [!UICONTROL Cloud Manager] executa as verificações de integridade de segurança do AEM existentes no ambiente de preparo após a implantação e relata o status por meio da interface. Os resultados são agregados de todas as instâncias do AEM no ambiente.

Essas mesmas verificações de integridade podem ser executadas a qualquer momento pelo Console da Web ou pelo painel de operações.

Se qualquer uma das instâncias relatar uma falha em uma determinada verificação de integridade, todo o ambiente falhará nessa verificação. Assim como no caso dos testes de qualidade e desempenho do código, essas verificações de integridade são organizadas em categorias e comunicadas através do sistema de marcação em três níveis. A única distinção é que não há qualquer limite no caso de testes de segurança. Todas as verificações de integridade são aprovadas ou reprovadas.

A tabela a seguir lista as verificações de integridade.

| Nome | Implementação da verificação de integridade | Categoria |
|---|---|---|
| A opção Disponibilidade da API de anexo do firewall de desserialização está em um estado aceitável. | [Disponibilidade da API de anexo do firewall de desserialização](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=pt-BR#security) | Crítico |
| O firewall de desserialização está funcionando. | [Firewall de desserialização funcional](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=pt-BR#security) | Crítico |
| O firewall de desserialização está carregado. | [Firewall de desserialização carregado](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=pt-BR#security) | Crítico |
| A implementação do `AuthorizableNodeName` não expõe a ID autorizável no nome/caminho do nó. | [Geração do nome do nó autorizada](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=pt-BR#security) | Crítico |
| As senhas padrão foram alteradas. | [Contas padrão de logon](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=pt-BR#users-and-groups-in-aem) | Crítico |
| O servlet de GET padrão do Sling está protegido contra ataques de DOS. | Sling Get Servlet | Crítico |
| O Sling Java Script Handler está configurado adequadamente. | Sling Java Script Handler | Crítico |
| O Sling JSP Script Handler está configurado adequadamente. | Sling JSP Script Handler | Crítico |
| O SSL está configurado corretamente. | Configuração do SSL | Crítico |
| Nenhuma política de perfil de usuário obviamente insegura foi encontrada. | Acesso padrão ao perfil de usuário | Crítico |
| O Sling Referrer Filter está configurado para impedir ataques de CSRF. | [Sling Referrer Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=pt-BR#security) | Importante |
| O gerenciador de bibliotecas HTML do Adobe Granite está configurado adequadamente. | Configuração do gerenciador de biblioteca HTML CQ | Importante |
| O pacote de suporte CRXDE está desativado. | Suporte do CRXDE | Importante |
| O pacote e o servlet DavEx do Sling estão desativados. | Verificação de integridade do DavEx | Importante |
| O conteúdo de amostra não está instalado. | Pacotes de conteúdo de exemplo | Importante |
| O filtro de solicitação WCM e o filtro de depuração WCM estão desativados. | [Configuração de filtros WCM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html?lang=pt-BR#configuring) | Importante |
| O pacote e o servlet WebDAV do Sling estão configurados adequadamente. | Verificação de integridade do WebDAV | Importante |
| O servidor da Web está configurado para impedir o clickjacking. | Configuração de servidor da Web | Importante |
| A replicação não está usando o usuário `admin`. | Reprodução e usuários de transporte | Informações |

## Teste de desempenho {#performance-testing}

### AEM Sites {#aem-sites}

O Cloud Manager executa testes de desempenho para programas do AEM Sites. O teste de desempenho é executado por aproximadamente 30 minutos, ativando usuários virtuais (contêineres) que simulam usuários reais para acessar páginas em ambientes de preparo para simular o tráfego. Essas páginas são encontradas usando um crawler.

#### Usuários virtuais {#virtual-users}

O número de usuários ou contêineres virtuais gerados pelo Cloud Manager é determinado pelos KPIs (tempo de resposta e visualizações de página por minuto) definidos pelo usuário com a função **Proprietário da empresa** ao [criar ou editar o programa.](/help/getting-started/program-setup.md) Com base nos KPIs definidos, até 10 contêineres que simulam usuários reais serão gerados. As páginas selecionadas para teste são divididas e atribuídas a cada usuário virtual.

#### Crawler {#crawler}

Antes do início do período de teste de 30 minutos, o Cloud Manager rastreará o ambiente de preparo usando um conjunto de um ou mais URLs de propagação configurados pelo engenheiro de sucesso do cliente. A partir desses URLs, o HTML de cada página é inspecionado e os links são percorridos de uma maneira ampla.

* Por padrão, esse processo de rastreamento é limitado a no máximo 5.000 páginas.
* O número máximo de páginas a serem testadas pode ser substituído pela configuração da [variável de ambiente](/help/getting-started/build-environment.md#environment-variables) `MAX_PAGES`.
   * Os valores permitidos são `2000` - `7000`.
* As solicitações do crawler têm um tempo limite fixo de 10 segundos.

#### Conjuntos de páginas para teste {#page-sets}

As páginas são selecionadas por três conjuntos de páginas. O Cloud Manager usa os logs de acesso das instâncias do AEM em ambientes de produção e de preparo para determinar os seguintes buckets.

* **Páginas ativas populares** - essa opção é selecionada para garantir que as páginas mais populares acessadas por clientes ativos sejam testadas. O Cloud Manager lerá o log de acesso e determinará as 25 páginas mais acessadas por clientes em tempo real para gerar uma lista das principais `Popular Live Pages`. A interseção dessas páginas, que também estão presentes no ambiente de preparo, é então rastreada no ambiente de preparo.

* **Outras páginas ativas** - essa opção é selecionada para garantir que as páginas que estão fora das 25 páginas ativas populares que podem não ser populares, mas são importantes para o teste, sejam testadas. Semelhante às páginas ativas populares, elas são extraídas do log de acesso e também devem estar presentes no ambiente de preparo.

* **Novas páginas** - essa opção é selecionada para testar novas páginas que podem ter sido implantadas apenas no ambiente de preparo e não ainda na produção, mas devem ser testadas.

##### Distribuição de tráfego em conjuntos de páginas selecionados {#distribution-of-traffic}

Você pode escolher entre um e três conjuntos na guia **Teste** da sua [configuração de pipeline.](/help/using/production-pipelines.md) A distribuição do tráfego é baseada no número de conjuntos selecionados. Ou seja, se todos os três forem selecionados, 33% do total de visualizações de página serão colocadas em cada conjunto. Se dois forem selecionados, 50% serão direcionadas a cada conjunto. Se um for selecionado, 100% do tráfego será direcionado para esse conjunto.

Consideremos este exemplo.

* Há uma divisão meio a meio entre as páginas ativas populares e os novos conjuntos de páginas.
* Outras páginas ativas não são usadas.
* O novo conjunto de páginas contém 3.000 páginas.
* O KPI de visualizações de página por minuto está definido em 200.

Durante o período de teste de 30 minutos:

* Cada uma das 25 páginas no conjunto de páginas ativas populares será acessada 120 vezes: `((200 * 0.5) / 25) * 30 = 120`
* Cada uma das 3.000 páginas no novo conjunto de páginas será acessada uma vez: `((200 * 0.5) / 3000) * 30 = 1`

#### Testes e relatórios {#testing-reporting}

O Cloud Manager executa testes de desempenho para programas do AEM Sites, solicitando páginas como um usuário não autenticado por padrão no servidor de publicação de preparo por um período de teste de 30 minutos. Ele mede as métricas geradas pelo usuário virtual (tempo de resposta, taxa de erro, exibições por minuto etc.) para cada página, bem como várias métricas no nível do sistema (CPU, memória, dados de rede) para todas as instâncias.

A tabela a seguir resume a matriz de teste de desempenho usando o sistema de marcação em três níveis.

| Métrica | Categoria | Limite de falhas |
|---|---|---|
| Taxa de erro da solicitação de página | Crítico | >= 2% |
| Taxa de utilização da CPU | Crítico | >= 80% |
| Tempo de espera de E/S de disco | Crítico | >= 50% |
| Tempo de resposta do 95º percentil | Importante | >= KPI de nível de programa |
| Tempo de resposta máximo | Importante | >= 18 segundos |
| Visualizações de página por minuto | Importante | &lt; KPI de nível de programa |
| Utilização da largura de banda do disco | Importante | >= 90% |
| Utilização da largura de banda da rede | Importante | >= 90% |
| Solicitações por minuto | Informações | >= 6000 |

Consulte a seção [Teste de desempenho autenticado](#authenticated-performance-testing) para obter mais detalhes sobre como usar a autenticação básica para testes de desempenho do Sites e do Assets.

>[!NOTE]
>
>As instâncias de autor e de publicação são monitoradas durante o período do teste. Se alguma métrica não for obtida para uma instância, essa métrica será relatada como desconhecida e a etapa correspondente falhará.

#### Teste de desempenho autenticado {#authenticated-performance-testing}

Se necessário, os clientes do AMS com sites autenticados podem especificar um nome de usuário e senha que o Cloud Manager usará para acessar o site durante os testes de desempenho.

O nome de usuário e a senha são especificados como variáveis de pipeline com os nomes `CM_PERF_TEST_BASIC_USERNAME` e `CM_PERF_TEST_BASIC_PASSWORD`.

O nome de usuário deve ser armazenado em uma variável `string` e a senha deve ser armazenada em uma variável `secretString`. Se ambos forem especificados, cada solicitação do crawler de teste de desempenho e dos usuários virtuais de teste conterá essas credenciais como uma autenticação básica de HTTP.

Para definir essas variáveis usando a CLI do Cloud Manager, execute:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Consulte a documentação [Correção das variáveis do pipeline do usuário](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) para saber como usar a API.

### AEM Assets {#aem-assets}

O Cloud Manager executa testes de desempenho para programas do AEM Assets fazendo o upload de ativos repetidamente por um período de teste de 30 minutos.

#### Requisitos de integração {#onboarding-requirement}

Para testes de desempenho do Assets, o engenheiro de sucesso do cliente criará um usuário e senha do `cloudmanager` durante a integração do autor no ambiente de preparo. As etapas do teste de desempenho exigem um usuário chamado `cloudmanager` e a senha associada configurada pelo seu CSE. Isso não deve ser removido da instância do autor e suas permissões não devem ser alteradas. Fazer isso provavelmente causaria uma falha no teste de desempenho do Assets.

#### Imagens e ativos para teste {#assets-for-testing}

Os clientes podem fazer upload de seus próprios ativos para testes. Isso pode ser feito a partir da tela **Configuração de pipeline** ou **Editar**. Formatos de imagem comuns, como JPEG, PNG, GIF e BMP são compatíveis, assim como arquivos do Photoshop, Illustrator e Postscript.

Se nenhuma imagem for carregada, o Cloud Manager usará uma imagem padrão e documentos de PDF para testes.

#### Distribuição de ativos para teste {#distribution-of-assets}

A distribuição de quantos ativos de cada tipo são carregados por minuto é definida na tela **Configuração de pipeline** ou **Editar**.

Por exemplo, se uma divisão 70/30 for usada e houver 10 ativos carregados por minuto, 7 imagens e 3 documentos serão carregados por minuto.

#### Testes e relatórios {#testing-and-reporting}

O Cloud Manager criará uma pasta na instância do autor usando o nome de usuário e a senha configurados pelo CSE. Os ativos são carregados na pasta usando uma biblioteca de código aberto. Os testes executados pela etapa de teste do Assets são gravados usando uma [biblioteca de código aberto.](https://github.com/adobe/toughday2) Os tempos de processamento de cada ativo e de várias métricas no nível do sistema são medidos durante o teste de 30 minutos. Esse recurso pode carregar imagens e documentos PDF.

>[!TIP]
>
>Consulte o documento [Configurar pipelines de produção](/help/using/production-pipelines.md) para saber mais. Consulte o documento [Configuração do programa](/help/getting-started/program-setup.md) para saber como configurar seu programa e definir seus KPIs.

### Gráficos de resultados dos testes de desempenho {#performance-testing-results-graphs}

Várias métricas estão disponíveis na **Caixa de diálogo Teste de desempenho**

![Lista de métricas](/help/assets/understand_test-results-screen1.png)

Os painéis de métricas podem ser expandidos para exibir um gráfico, fornecer um link para um download ou ambos.

![Métricas expandidas como gráfico](/help/assets/screen_shot_2018-09-05at83933pm.png)

Essa funcionalidade está disponível para as seguintes métricas.

* **Utilização da CPU** - um gráfico da utilização da CPU durante o período de teste

* **Tempo de espera de E/S de disco** - um gráfico do tempo de espera de E/S de disco durante o período de teste

* **Taxa de erro da página** - um gráfico de erros de página por minuto durante o período de teste
   * Um arquivo CSV listando páginas que geraram um erro durante o teste

* **Utilização da largura de banda do disco** - um gráfico da utilização da largura de banda do disco durante o período de teste

* **Utilização da largura de banda da rede** - um gráfico da utilização da largura de banda da rede durante o período de teste

* **Tempo de resposta máximo** - um gráfico do tempo de resposta máximo por minuto durante o período de teste

* **Tempo de resposta do percentil 95** - um gráfico do tempo de resposta do percentil 95 por minuto durante o período de teste
   * Um arquivo CSV que lista páginas cujo tempo de resposta do percentil 95 excedeu o KPI definido

## Otimização da verificação do pacote de conteúdo {#content-package-scanning-optimization}

Como parte do processo de análise de qualidade, o Cloud Manager realiza a análise dos pacotes de conteúdo produzidos pelo build do Maven. O Cloud Manager oferece otimizações para acelerar esse processo, que são eficazes quando determinadas restrições de empacotamento são observadas. Mais importante é a otimização executada para projetos que geram um único pacote de conteúdo, geralmente chamado de pacote “all”, que contém vários outros pacotes de conteúdo produzidos pela build, que são marcados como ignorados. Quando o Cloud Manager detecta esse cenário, em vez de descompactar o pacote “all”, os pacotes de conteúdo individuais são verificados diretamente e classificados com base nas dependências. Por exemplo, considere a seguinte saída de build.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (pacote de conteúdo)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (pacote de conteúdo ignorados)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (pacote de conteúdo ignorados)

Se os únicos itens dentro de `myco-all-1.0.0-SNAPSHOT.zip` são os dois pacotes de conteúdo ignorados, então os dois pacotes incorporados serão verificados no lugar do pacote de conteúdo “all”.

Para projetos que produzem dezenas de pacotes incorporados, essa otimização economiza mais de 10 minutos por execução de pipeline.

Um caso especial pode ocorrer quando o pacote de conteúdo “all” contiver uma combinação de pacotes de conteúdo ignorados e pacotes OSGi. Por exemplo, se o `myco-all-1.0.0-SNAPSHOT.zip` continha os dois pacotes incorporados mencionados anteriormente, bem como um ou mais pacotes OSGi, então um novo pacote de conteúdo mínimo é construído apenas com os pacotes OSGi. Este pacote é sempre chamado de `cloudmanager-synthetic-jar-package` e os pacotes contidos são colocados em `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Essa otimização não afeta os pacotes implantados no AEM.
>* Como a correspondência entre os pacotes de conteúdo incorporados e os pacotes de conteúdo ignorados se baseia em nomes de arquivo, essa otimização não pode ser executada se vários pacotes de conteúdo ignorados tiverem exatamente o mesmo nome de arquivo ou se o nome do arquivo for alterado durante a incorporação.

