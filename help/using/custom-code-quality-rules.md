---
title: Regras de qualidade do código personalizado
description: Saiba mais sobre as regras de qualidade de código personalizado executadas pelo Cloud Manager como parte do teste de qualidade de código, com base nas práticas recomendadas da engenharia do AEM.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 1ba4ed6c311eeaff9c71313d265531f427ef2736
workflow-type: tm+mt
source-wordcount: '3566'
ht-degree: 99%

---


# Regras de qualidade do código personalizado {#custom-code-quality-rules}

Saiba mais sobre as regras de qualidade do código personalizado executadas pelo Cloud Manager como parte do [teste da qualidade do código](/help/using/code-quality-testing.md), com base nas práticas recomendadas da engenharia do AEM.

>[!NOTE]
>
>As amostras de código fornecidas aqui são apenas para fins ilustrativos. Consulte a [Documentação de conceitos da SonarQube](https://docs.sonarqube.org/latest/) para conhecer seus conceitos e regras de qualidade.

>[!NOTE]
>
>As regras completas do SonarQube não estão disponíveis para download devido às informações proprietárias do Adobe. Você pode baixar a lista completa de regras [usando este link.](/help/assets/CodeQuality-rules-latest-AMS.xlsx) Continue a ler este documento para obter descrições e exemplos das regras.

## Regras do SonarQube {#sonarqube-rules}

A seção a seguir especifica as regras do SonarQube executadas pelo Cloud Manager.

### Não usar funções potencialmente perigosas {#do-not-use-potentially-dangerous-functions}

* **Chave**: CQRules:CWE-676
* **Tipo**: Vulnerabilidade
* **Severidade**: Alta
* **Desde**: Versão 2018.4.0

Os métodos `Thread.stop()` e `Thread.interrupt()` podem gerar problemas difíceis de reproduzir e, em alguns casos, vulnerabilidades de segurança. A utilização deve ser rigorosamente monitorizada e validada. Em geral, a transmissão de mensagens é uma forma mais segura de atingir objetivos semelhantes.

#### Código não compatível {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Código compatível {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### Não use strings de formato que possam ser controladas externamente {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Chave**: CQRules:CWE-134
* **Tipo**: Vulnerabilidade
* **Severidade**: Alta
* **Desde**: Versão 2018.4.0

Usar uma string de formato de uma fonte externa (como um parâmetro de solicitação ou conteúdo gerado pelo usuário) pode expor um aplicativo a ataques de negação de serviço. Há circunstâncias em que uma string de formato pode ser controlada externamente, mas isso só é permitido a partir de fontes confiáveis.

#### Código não compatível {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### As solicitações HTTP sempre devem ter soquete e tempo limite de conexão {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Chave**: CQRules:ConnectionTimeoutMechanism
* **Tipo**: Erro
* **Severidade**: Crítica
* **Desde**: Versão 2018.6.0

Ao executar solicitações HTTP de dentro de um aplicativo do AEM, é importante garantir que os tempos limite adequados sejam configurados para evitar o consumo desnecessário de thread. Infelizmente, o comportamento tradicional do cliente HTTP padrão do Java™ (`java.net.HttpUrlConnection`) e do cliente de componentes HTTP do Apache geralmente usado é o de nunca atingir o tempo limite, portanto, estes devem ser definidos de forma explícita. Como prática recomendada, essas ocorrências de tempo limite não devem exceder 60 segundos.

#### Código não compatível {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Código compatível {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### Os objetos ResourceResolver sempre devem ser fechados {#resourceresolver-objects-should-always-be-closed}

* **Chave**: CQRules:CQBP-72
* **Tipo**: Code Smell
* **Severidade**: Alta
* **Desde**: Versão 2018.4.0

`ResourceResolver` objetos obtidos do `ResourceResolverFactory` consomem recursos do sistema. Embora existam medidas em vigor para recuperar esses recursos quando um `ResourceResolver` não estiver mais em uso, é mais eficiente fechar explicitamente todos os objetos `ResourceResolver` abertos chamando o método `close()`.

Um equívoco relativamente comum é que os objetos `ResourceResolver` criados usando uma sessão existente do JCR não devem ser fechados explicitamente ou que fazer isso encerrará a sessão subjacente do JCR. Não é isso o que ocorre. Independentemente de como um `ResourceResolver` foi aberto, ele deve ser fechado quando não estiver mais em uso. Como `ResourceResolver` implementa a interface `Closeable`, também é possível usar a sintaxe `try-with-resources` em vez de chamar explicitamente `close()`.

#### Código não compatível {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Código compatível {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Não usar caminhos Sling Servlet para registrar servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Chave**: CQRules:CQBP-75
* **Tipo**: Code Smell
* **Severidade**: Alta
* **Desde**: Versão 2018.4.0

Conforme descrito na [Documentação do Sling](https://sling.apache.org/documentation/the-sling-engine/servlets.html), não é recomendado vincular servlets por caminhos. Os servlets vinculados a caminhos não podem usar os controles de acesso JCR padrão e, como resultado disso, exigem maior rigor de segurança. Em vez de usar servlets vinculados a caminhos, é recomendado criar nós no repositório e registrar os servlets por tipo de recurso.

#### Código não compatível {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### As exceções capturadas devem ser registradas ou lançadas, não ambos {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Chave**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Em geral, uma exceção deve ser registrada exatamente uma vez. O múltiplo registro de exceções pode causar confusão, pois não deixa claro quantas vezes uma exceção ocorreu. O padrão mais comum que leva a isso é o registro e o descarte de uma exceção capturada.

#### Código não compatível {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Código compatível {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Evite declarações de log imediatamente seguidas por instruções de lançamento {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Chave**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Outro padrão comum a ser evitado é registrar uma mensagem e imediatamente depois lançar uma exceção. Isso geralmente indica que a mensagem de exceção acabará duplicada nos arquivos de log.

#### Código não compatível {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Código compatível {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Evitar fazer registro em INFO ao manipular solicitações GET ou HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Chave**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Tipo**: Code Smell
* **Severidade**: Baixa

Em geral, o nível de log INFO deve ser usado para demarcar ações importantes e, por padrão, o AEM é configurado para fazer logon no nível INFO ou superior. Os métodos GET e HEAD devem ser operações somente leitura e, portanto, não constituem ações importantes. Registrar no nível INFO em resposta a solicitações GET ou HEAD provavelmente criará um ruído significativo de log, dificultando a identificação de informações úteis em arquivos de log. Ao manipular solicitações GET ou HEAD, o registro deverá estar nos níveis AVISO ou ERRO quando algo der errado ou nos níveis DEPURAÇÃO ou RASTREAMENTO, se informações mais detalhadas de solução de problemas forem necessárias.

>[!NOTE]
>
>Isso não se aplica ao log access.log-type para cada solicitação.

#### Código não compatível {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Código compatível {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Não usar Exception.getMessage() como o primeiro parâmetro de uma instrução de registro {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Chave**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Como prática recomendada, as mensagens de log devem fornecer informações contextuais sobre onde ocorreu uma exceção no aplicativo. Embora o contexto também possa ser determinado pelo uso de rastros de pilha, em geral, a mensagem de log será mais fácil de ler e entender. Como resultado disso, ao registrar uma exceção, não é uma prática recomendada usar a mensagem da exceção como a mensagem de registro. A mensagem de exceção contém o que deu errado, enquanto a mensagem de log deve ser usada para informar a um leitor de logs o que o aplicativo estava fazendo quando a exceção aconteceu. A mensagem de exceção ainda é registrada. Ao especificar sua própria mensagem, será mais fácil entender os logs.

#### Código não compatível {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Código compatível {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### O registro em blocos de captura deve estar no nível AVISO ou ERRO {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Chave**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Como o nome sugere, as exceções do Java™ sempre devem ser usadas em casos excepcionais. Como resultado, quando uma exceção é capturada, é importante garantir que as mensagens de log sejam registradas no nível apropriado: AVISO ou ERRO. Isso garante que essas mensagens sejam exibidas corretamente nos logs.

#### Código não compatível {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Código compatível {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Não imprimir rastreamentos de pilha no console {#do-not-print-stack-traces-to-the-console}

* **Chave**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

O contexto é essencial ao entender as mensagens de log. Usar `Exception.printStackTrace()` faz com que somente o rastro de pilha seja enviado para o fluxo de erro padrão, perdendo todo o contexto. Além disso, em um aplicativo multithread como o AEM, se várias exceções forem impressas usando esse método em paralelo, seus rastreamentos de pilha podem se sobrepor, gerando bastante confusão. As exceções devem ser registradas somente por meio da estrutura de registro.

#### Código não compatível {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Código compatível {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Não gerar saída para saída padrão ou erro padrão {#do-not-output-to-standard-output-or-standard-error}

* **Chave**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

O logon no AEM sempre deve ser feito por meio da estrutura de log, SLF4J. Ao enviar diretamente para a saída padrão ou para fluxos de erro padrão, as informações estruturais e contextuais fornecidas pela estrutura de registro são perdidas e podem, em alguns casos, causar problemas de desempenho.

#### Código não compatível {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Código compatível {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Evitar caminhos /apps e /libs codificados {#avoid-hardcoded-apps-and-libs-paths}

* **Chave**: CQRules:CQBP-71
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Em geral, caminhos que começam com `/libs` e `/apps` não devem ser codificados, pois os caminhos a que se referem são armazenados com mais frequência como caminhos relativos ao caminho de pesquisa do Sling (que está definido como `/libs,/apps` por padrão). O uso do caminho absoluto pode apresentar defeitos sutis que só apareceriam posteriormente no ciclo de vida do projeto.

#### Código não compatível {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Código compatível {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### O Sling Scheduler não deve ser usado {#sonarqube-sling-scheduler}

* **Chave**: CQRules:AMSCORE-554
* **Tipo**: Compatibilidade entre Smell/Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

Não use o Sling Scheduler para tarefas que exigem uma execução garantida. Os processos agendados no Sling têm execução garantida e são mais adequados para ambientes clusterizados e não clusterizados.

Consulte a [Documentação de eventos e manuseio de processos do Apache Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) para saber mais sobre como os processos do Sling são tratados em ambientes clusterizados.

### APIs do AEM obsoletas não devem ser usadas {#sonarqube-aem-deprecated}

* **Chave**: AMSCORE-553
* **Tipo**: Compatibilidade entre Smell/Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

As APIs do AEM estão em constante revisão para identificar quais não devem mais ser usadas e, portanto, consideradas descontinuadas.

Muitas vezes, essas APIs são obsoletas usando a anotação padrão Java™ *@Deprecated* e, sendo assim, são identificadas por `squid:CallToDeprecatedMethod`.

No entanto, há casos em que uma API é obsoleta no contexto do AEM, mas pode não ser obsoleta em outros contextos. Esta regra identifica essa segunda classe.

## Regras de conteúdo OakPAL {#oakpal-rules}

A seção a seguir especifica as verificações do OakPAL executadas pelo Cloud Manager.

>[!NOTE]
>
>O OakPAL é uma estrutura que valida pacotes de conteúdo usando um repositório Oak autônomo. Ele foi desenvolvido por um parceiro do AEM e vencedor do prêmio AEM Rockstar North America 2019.

### As APIs de produto anotadas com @ProviderType não devem ser implementadas ou estendidas pelos clientes {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Chave**: CQBP-84
* **Tipo**: Erro
* **Severidade**: Crítica
* **Desde**: Versão 2018.7.0

A API do AEM contém interfaces e classes do Java™ que devem apenas ser usadas, mas não implementadas, por código personalizado. Por exemplo, a interface `com.day.cq.wcm.api.Page` é implementada somente pelo AEM.

Quando novos métodos são adicionados a essas interfaces, esses métodos adicionais não afetam o código existente que usa essas interfaces e, como resultado, a adição de novos métodos a essas interfaces é considerada compatível com versões anteriores. No entanto, se o código personalizado implementa uma dessas interfaces, ele apresenta um risco de compatibilidade com versões anteriores para o cliente.

As interfaces e classes que devem ser implementadas apenas pelo AEM são anotadas com `org.osgi.annotation.versioning.ProviderType` ou, em alguns casos, com a anotação herdada semelhante `aQute.bnd.annotation.ProviderType`. Esta regra identifica os casos em que essa interface é implementada ou em que uma classe é estendida por código personalizado.

#### Código não compatível {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Os pacotes de clientes não devem criar ou modificar nós em /libs {#oakpal-customer-package}

* **Chave**: BannedPath
* **Tipo**: Erro
* **Gravidade**: Bloqueador
* **Desde**: Versão 2019.6.0

Uma prática recomendada já consolidada é que a árvore de conteúdo `/libs` no repositório de conteúdo do AEM deve ser considerada somente leitura pelos clientes. A modificação dos nós e propriedades em `/libs` cria riscos significativos para atualizações importantes e secundárias. Modificações no `/libs` são feitas pela Adobe apenas através de canais oficiais.

### Pacotes não devem conter configurações OSGi duplicadas {#oakpal-package-osgi}

* **Chave**: DuplicateOsgiConfigurations
* **Tipo**: Erro
* **Severidade**: Alta
* **Desde**: Versão 2019.6.0

Um problema comum que ocorre em projetos complexos é quando um mesmo componente OSGi é configurado várias vezes. Isso cria uma ambiguidade sobre qual configuração é operável. Essa regra age de acordo com o modo de execução, no sentido de que ela apenas identifica problemas em que o mesmo componente é configurado várias vezes no mesmo modo de execução ou combinação de modos de execução.

#### Código não compatível {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Código compatível {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### As pastas de configuração e instalação devem conter apenas nós OSGi {#oakpal-config-install}

* **Chave**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Tipo**: Erro
* **Severidade**: Alta
* **Desde**: Versão 2019.6.0

Por motivos de segurança, caminhos que contêm `/config/` e `/install/` somente podem ser lidos por usuários administrativos no AEM e devem ser usados apenas para a configuração do OSGi e os pacotes do OSGi. Colocar outros tipos de conteúdo em caminhos que contêm esses segmentos resultará em uma variação incontrolável e não intencional do comportamento do aplicativo entre usuários administrativos e não administrativos.

Um problema comum é o uso de nós chamados `config` nas caixas de diálogo de componente ou ao especificar a configuração do editor rich text para edição em linha. Para resolver isso, o nó incorreto deve ser renomeado com um nome que esteja em conformidade. Para configurar o editor de rich text, use a propriedade `configPath` do nó `cq:inplaceEditing` para especificar o novo local.

#### Código não compatível {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Código compatível {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Os pacotes não devem se sobrepor {#oakpal-no-overlap}

* **Chave**: PackageOverlaps
* **Tipo**: Erro
* **Severidade**: Alta
* **Desde**: Versão 2019.6.0

Semelhante à regra [Os pacotes não devem conter configurações OSGi duplicadas](#oakpal-package-osgi), esse é um problema comum em projetos complexos, onde o mesmo caminho de nó é gravado por vários pacotes de conteúdo separados. Embora seja possível usar as dependências do pacote de conteúdo para garantir um resultado consistente, é melhor evitar as sobreposições completamente.

### O modo de autoria padrão não deve ser a interface do usuário clássica {#oakpal-default-authoring}

* **Chave**: ClassicUIAuthoringMode
* **Tipo**: Compatibilidade entre Smell/Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

A configuração do OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` define o modo de autoria padrão no AEM. Como a interface clássica foi descontinuada no AEM 6.4, um problema será gerado quando o modo de criação padrão estiver configurado para usá-la.

### Os componentes com caixas de diálogo devem ter caixas de diálogo da interface do usuário sensíveis ao toque {#oakpal-components-dialogs}

* **Chave**: ComponentWithOnlyClassicUIDialog
* **Tipo**: Compatibilidade entre Smell/Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

Os componentes do AEM que têm uma caixa de diálogo com interface clássica devem sempre ter uma caixa de diálogo com interface de toque correspondente, para fornecer uma experiência de criação ideal e para serem compatíveis com o modelo de implantação do Cloud Service, que não é compatível com a interface clássica. Essa regra verifica os seguintes cenários:

* Um componente com uma caixa de diálogo da interface do usuário clássica (ou seja, um nó secundário `dialog`) deve ter uma caixa de diálogo da interface do usuário de toque correspondente (ou seja, um nó secundário `cq:dialog`).
* Um componente com uma caixa de diálogo de design da interface do usuário clássica (ou seja, um nó `design_dialog`) deve ter uma caixa de diálogo de design da interface do usuário de toque correspondente (ou seja, um nó secundário `cq:design_dialog`).
* Um componente que tem uma caixa de diálogo e uma caixa de diálogo de design com interfaces clássicas também deve ter duas caixas com interfaces de toque correspondentes.

A documentação das Ferramentas de modernização do AEM fornece detalhes e ferramentas para converter componentes da interface clássica para a interface de toque. Consulte [a documentação das Ferramentas de modernização do AEM](https://opensource.adobe.com/aem-modernize-tools/) para obter mais detalhes.

### Os pacotes não devem misturar conteúdo mutável e imutável {#oakpal-packages-immutable}

* **Chave**: ImmutableMutableMixedPackage
* **Tipo**: Compatibilidade entre Smell/Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

Para serem compatíveis com o modelo de implantação do Cloud Service, os pacotes de conteúdo individuais devem incluir conteúdo para as áreas imutáveis do repositório (ou seja, `/apps` e `/libs`) ou para a área mutável (ou seja, tudo que não está em `/apps` ou em `/libs`), mas não ambas. Por exemplo, um pacote que inclui `/apps/myco/components/text and /etc/clientlibs/myco` não é compatível com a Cloud Service e causará a criação de um relatório de problemas.

Consulte a [Documentação da Estrutura de projetos do AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=pt-BR) para obter mais detalhes.

>[!NOTE]
>
>A regra [Os pacotes de clientes não devem criar ou modificar nós em /libs](#oakpal-customer-package) sempre se aplica.

### Os agentes de replicação reversa não devem ser usados {#oakpal-reverse-replication}

* **Chave**: ReverseReplication
* **Tipo**: Compatibilidade entre Smell/Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

A compatibilidade com replicação reversa não está disponível em implantações de Cloud Service, conforme descrito nas [Notas de versão: remoção de agentes de replicação.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=pt-BR#replication-agents)

Os clientes que usam replicação inversa devem entrar em contato com a Adobe para obter soluções alternativas.

### Os recursos contidos nas bibliotecas de clientes ativadas por proxy devem estar em uma pasta denominada “Recursos” {#oakpal-resources-proxy}

* **Chave**: ClientlibProxyResource
* **Tipo**: Erro
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Bibliotecas de clientes do AEM podem conter recursos estáticos, como imagens e fontes. Conforme descrito na [documentação Usar bibliotecas do lado do cliente,](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=pt-BR#using-preprocessors) ao usar bibliotecas de cliente com proxy, esses recursos estáticos devem estar contidos em uma pasta filho chamada `resources` para ser efetivamente referenciado nas instâncias de publicação.

#### Código não compatível {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Código compatível {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Uso de processos de fluxo de trabalho incompatíveis com o Cloud Service {#oakpal-usage-cloud-service}

* **Chave**: CloudServiceIncompatibleWorkflowProcess
* **Tipo**: Code Smell
* **Gravidade**: Bloqueador
* **Desde**: Versão 2021.2.0

Com a mudança para os microsserviços de ativos no processamento de ativos no AEM Cloud Service, vários processos de fluxo de trabalho que foram usados nas versões local e AMS do AEM se tornaram incompatíveis ou desnecessários.

A ferramenta de migração no [repositório GitHub do AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) pode ser usada para atualizar modelos de fluxo de trabalho durante a migração para o AEM as a Cloud Service.

### O uso de modelos estáticos não é recomendado em prol dos modelos editáveis {#oakpal-static-template}

* **Chave**: StaticTemplateUsage
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Embora o uso de modelos estáticos tenha sido historicamente comum em projetos AEM, os modelos editáveis são altamente recomendados, pois fornecem maior flexibilidade e são compatíveis com recursos adicionais que não estão presentes nos modelos estáticos. Mais informações podem ser encontradas na [documentação Modelos de página - Editáveis.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-editable.html?lang=pt-BR)

A migração de modelos estáticos para editáveis pode ser amplamente automatizada usando as [Ferramentas de modernização do AEM.](https://opensource.adobe.com/aem-modernize-tools/)

### O uso de componentes básicos herdados não é recomendado {#oakpal-usage-legacy}

* **Chave**: LegacyFoundationComponentUsage
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Os componentes fundamentais herdados (ou seja, os componentes em `/libs/foundation`) foram descontinuados para várias versões do AEM em favor dos [Componentes principais.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=pt-BR) O uso dos componentes fundamentais herdados como a base para componentes personalizados, seja por sobreposição ou herança, não é recomendado e deve ser convertido no componente principal correspondente.

Essa conversão pode ser facilitada pelas [Ferramentas de modernização do AEM.](https://opensource.adobe.com/aem-modernize-tools/)

### Somente nomes e ordenações de modos de execução compatíveis devem ser usados {#oakpal-supported-runmodes}

* **Chave**: SupportedRunmode
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service utiliza uma política de nomeação rigorosa para nomes de modo de execução e uma ordenação estrita para eles. A lista de modos de execução compatíveis pode ser encontrada na [Documentação de implantação no AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=pt-BR#runmodes), e qualquer desvio em relação a isso será identificado como um problema.

### Os nós de definição do índice de pesquisa personalizado devem ser nós secundários diretos de /oak:index {#oakpal-custom-search}

* **Chave**: OakIndexLocation
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service exige que as definições de índice de pesquisa personalizada (ou seja, nós do tipo `oak:QueryIndexDefinition`) sejam nós secundários diretos de `/oak:index`. Os índices em outros locais devem ser movidos para serem compatíveis com o AEM Cloud Service. Mais informações sobre índices de pesquisa podem ser encontradas na [documentação de Pesquisa e indexação de conteúdo.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=pt-BR)

### Os nós de definição do índice de pesquisa personalizada devem ter uma compatVersion de 2 {#oakpal-custom-search-compatVersion}

* **Chave**: IndexCompatVersion
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service exige que as definições de índice de pesquisa personalizada (ou seja, nós do tipo `oak:QueryIndexDefinition`) devem ter a propriedade `compatVersion` definida como `2`. Nenhum outro valor é compatível com o AEM Cloud Service. Mais informações sobre índices de pesquisa podem ser encontradas na [documentação de Pesquisa e indexação de conteúdo.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=pt-BR)

### Os nós descendentes dos nós de definição de índice de pesquisa personalizada devem ser do tipo nt:unstructured {#oakpal-descendent-nodes}

* **Chave**: IndexDescendantNodeType
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Problemas difíceis de solucionar podem ocorrer quando um nó de definição de índice de pesquisa personalizada tem nós secundários desordenados. Para evitar isso, é recomendável que todos os nós descendentes de um nó `oak:QueryIndexDefinition` sejam do tipo `nt:unstructured`.

### Os nós de definição do índice de pesquisa personalizada devem conter um nó secundário denominado indexRules que tenha tarefas derivadas {#oakpal-custom-search-index}

* **Chave**: IndexRulesNode
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Um nó de definição de índice de pesquisa personalizada corretamente definido deve conter um nó secundário chamado `indexRules` que, por sua vez, deve ter pelo menos um secundário. Mais informações podem ser encontradas na [documentação do Oak.](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

### Os nós de definição do índice de pesquisa personalizado devem seguir as convenções de nomenclatura {#oakpal-custom-search-definitions}

* **Chave**: IndexName
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service exige que definições de índice de pesquisa personalizada (ou seja, nós do tipo `oak:QueryIndexDefinition`) sejam nomeadas de acordo com um padrão específico descrito em [Pesquisa e indexação de conteúdo.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=pt-BR#how-to-use)

### Os nós de definição de índice de pesquisa personalizada devem usar o tipo de índice lucene  {#oakpal-index-type-lucene}

* **Chave**: IndexType
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service exige que as definições de índice de pesquisa personalizada (ou seja, nós do tipo `oak:QueryIndexDefinition`) tenham uma propriedade `type` com o valor definido como `lucene`. A indexação usando tipos de índice herdados deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [documentação de Pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=pt-BR#how-to-use) para obter mais informações.

### Os nós de definição de índice de pesquisa personalizada não devem conter uma propriedade denominada seed {#oakpal-property-name-seed}

* **Chave**: IndexSeedProperty
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service proíbe definições de índice de pesquisa personalizada (ou seja, nós do tipo `oak:QueryIndexDefinition`) de conter uma propriedade chamada `seed`. A indexação usando essa propriedade deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [documentação de Pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=pt-BR#how-to-use) para obter mais informações.

### Os nós de definição de índice de pesquisa personalizada não devem conter uma propriedade denominada reindex {#oakpal-reindex-property}

* **Chave**: IndexReindexProperty
* **Tipo**: Code Smell
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service proíbe definições de índice de pesquisa personalizada (ou seja, nós do tipo `oak:QueryIndexDefinition`) de conter uma propriedade chamada `reindex`. A indexação usando essa propriedade deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [Documentação de pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=pt-BR#how-to-use) para obter mais informações.

## Ferramenta de otimização do Dispatcher {#dispatcher-optimization-tool-rules}

A seção a seguir lista as verificações da Ferramenta de Otimização do Dispatcher (DOT) executadas pelo Cloud Manager. Siga os links para cada verificação para obter sua definição e detalhes do GitHub.

* [Tokens inesperados da configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Cotação sem correspondência da configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Chave ausente da configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Chave extra de configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Propriedade obrigatória ausente na Configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Propriedade obsoleta de configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Configuração do Dispatcher não encontrada](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Arquivo de inclusão de configuração httpd não encontrado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Configuração geral do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [O cache do farm de publicação do Dispatcher deve ter o serveStaleOnError ativado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Os filtros farm de publicação do Dispatcher devem conter as regras de negação padrão da versão 6.x.x do arquétipo do AEM](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [A propriedade statfileslevel do cache do farm de publicação do Dispatcher deve ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [A propriedade gracePeriod do farm de publicação do Dispatcher deve ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Cada farm do Dispatcher deve ter um nome exclusivo](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [O cache do farm de publicação do Dispatcher deve ter suas regras ignoreUrlParams configuradas de maneira semelhante a uma lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Os filtros farm de publicação do Dispatcher devem especificar os seletores Sling permitidos de maneira semelhante a uma lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Os filtros de farm de publicação do Dispatcher devem especificar os padrões de sufixo do Sling permitidos de maneira semelhante a uma lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [Não use a diretiva “Require all granted” em uma seção do VirtualHost Diretory com um caminho de diretório raiz](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
