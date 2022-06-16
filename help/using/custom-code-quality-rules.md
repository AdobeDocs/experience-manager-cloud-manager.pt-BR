---
title: Regras de qualidade do código personalizado
description: Esta página descreve as regras de qualidade de código personalizadas executadas pelo Cloud Manager como parte do teste de qualidade de código. Eles são baseados nas práticas recomendadas da engenharia de AEM.
uuid: a7feb465-1982-46be-9e57-e67b59849579
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: d2338c74-3278-49e6-a186-6ef62362509f
feature: Code Quality Rules
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: d4c92a36ca3af123730d68fedf1dbf7ee819c66b
workflow-type: tm+mt
source-wordcount: '3609'
ht-degree: 3%

---


# Regras de qualidade do código personalizado {#custom-code-quality-rules}

Esta página descreve as regras de qualidade do código personalizado executadas pelo Cloud Manager como parte de [teste de qualidade do código.](understand-your-test-results.md) Eles são baseados nas práticas recomendadas da engenharia de AEM.

>[!NOTE]
>
>Para saber mais sobre as regras de qualidade do código personalizado do Cloud Manager em AEM as a Cloud Service, consulte [para esta documentação](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/custom-code-quality-rules.html#using-cloud-manager).

>[!NOTE]
>
>As amostras de código fornecidas aqui são apenas para fins ilustrativos. Consulte [Documentação de Conceitos da SonarQube](https://docs.sonarqube.org/7.4/user-guide/concepts/) para aprender sobre seus conceitos e regras de qualidade.

## Regras SonarQube {#sonarqube-rules}

A seção a seguir detalha as regras do SonarQube executadas pelo Cloud Manager.

### Não Utilize Funções Potencialmente Perigosas {#do-not-use-potentially-dangerous-functions}

* **Chave**: CQRules:CWE-676
* **Tipo**: Vulnerabilidade
* **Gravidade**: Major
* **Since**: Versão 2018.4.0

Os métodos `Thread.stop()` e `Thread.interrupt()` pode gerar problemas de difícil reprodução e, em alguns casos, vulnerabilidades de segurança. A utilização deve ser rigorosamente monitorizada e validada. Em geral, a transmissão de mensagens é uma forma mais segura de atingir objetivos semelhantes.

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
* **Gravidade**: Major
* **Since**: Versão 2018.4.0

Usar uma string de formato de uma fonte externa (como um parâmetro de solicitação ou conteúdo gerado pelo usuário) pode expor um aplicativo a ataques de negação de serviço. Há circunstâncias em que uma string de formato pode ser controlada externamente, mas só é permitida a partir de fontes confiáveis.

#### Código não compatível {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### As solicitações HTTP devem sempre ter soquete e tempo limite de conexão {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Chave**: CQRules:ConnectionTimeoutEngine
* **Tipo**: Bug
* **Gravidade**: Crítico
* **Since**: Versão 2018.6.0

Ao executar solicitações HTTP de dentro de um aplicativo AEM, é importante garantir que os tempos limite adequados sejam configurados para evitar o consumo desnecessário de encadeamento. Infelizmente, o comportamento padrão do cliente HTTP padrão do Java, `java.net.HttpUrlConnection`e o cliente Apache HTTP Components usado com frequência é o de nunca expirar o tempo limite, portanto, os tempos limite devem ser definidos explicitamente. Como prática recomendada, essas ocorrências de tempo limite não devem exceder 60 segundos.

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

### Os objetos ResourceResolver devem ser sempre fechados {#resourceresolver-objects-should-always-be-closed}

* **Chave**: CQRules:CQBP-72
* **Tipo**: Cheiro do código
* **Gravidade**: Major
* **Since**: Versão 2018.4.0

`ResourceResolver` objetos obtidos do `ResourceResolverFactory` consumir recursos do sistema. Embora existam medidas em vigor para recuperar esses recursos quando uma `ResourceResolver` não estiver mais em uso, é mais eficiente fechar explicitamente qualquer aberto `ResourceResolver` chamando a `close()` método .

Um equívoco relativamente comum é que `ResourceResolver` os objetos criados usando uma Sessão JCR existente não devem ser explicitamente fechados, ou isso fechará a Sessão JCR subjacente. Não é esse o caso. Independentemente de como uma `ResourceResolver` for aberto, deve ser fechado quando não for mais usado. Since `ResourceResolver` implementa o `Closeable` , também é possível usar a variável `try-with-resources` sintaxe em vez de chamar explicitamente `close()`.

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

### Não use os caminhos do Sling Servlet para registrar servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Chave**: CQRules:CQBP-75
* **Tipo**: Cheiro do código
* **Gravidade**: Major
* **Since**: Versão 2018.4.0

Conforme descrito na [Documentação do Sling](http://sling.apache.org/documentation/the-sling-engine/servlets.html), os servlets de vinculação por caminhos não são incentivados. Os servlets vinculados ao caminho não podem usar controles de acesso JCR padrão e, como resultado, exigem rigor de segurança adicional. Em vez de usar servlets vinculados a caminhos, é recomendável criar nós no repositório e registrar servlets por tipo de recurso.

#### Código não compatível {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### As exceções capturadas devem ser registradas ou lançadas, não {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Chave**: CQRules:CQBP-44—CatchAndLogOrThrow
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2018.4.0

Em geral, uma exceção deve ser registrada exatamente uma vez. O registro de exceções várias vezes pode causar confusão, pois não está claro quantas vezes uma exceção ocorreu. O padrão mais comum que leva a isso é o registro e o lançamento de uma exceção capturada.

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

* **Chave**: CQRules:CQBP-44 — ConsecutivelyLogAndThrow
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2018.4.0

Outro padrão comum a ser evitado é registrar uma mensagem e imediatamente lançar uma exceção. Isso geralmente indica que a mensagem de exceção acabará duplicada nos arquivos de log.

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

### Evite fazer logon em INFO ao manipular solicitações de GET ou HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Chave**: CQRules:CQBP-44—LogInfoInGetOrHeadRequests
* **Tipo**: Cheiro do código
* **Gravidade**: Menor

Em geral, o nível de log INFO deve ser usado para demarcar ações importantes e, por padrão, AEM é configurado para fazer logon no nível INFO ou superior. Os métodos GET e HEAD só devem ser operações somente leitura e, portanto, não constituem ações importantes. Fazer logon no nível da INFO em resposta a solicitações de GET ou HEAD provavelmente gera um ruído significativo de log, dificultando a identificação de informações úteis em arquivos de log. O registro ao manipular solicitações de GET ou HEAD deve estar nos níveis de AVISO ou ERRO quando algo deu errado ou nos níveis de DEBUG ou TRACE, se informações mais detalhadas de solução de problemas forem úteis.

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

### Não use Exception.getMessage() como o primeiro parâmetro de uma instrução de log {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Chave**: CQRules:CQBP-44—ExceptionGetMessageIsFirstLogParam
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2018.4.0

Como prática recomendada, as mensagens de log devem fornecer informações contextuais sobre onde ocorreu uma exceção no aplicativo. Embora o contexto também possa ser determinado por meio do uso de rastreamentos de pilha, em geral a mensagem de log será mais fácil de ler e entender. Como resultado, ao registrar uma exceção, é uma prática ruim usar a mensagem da exceção como a mensagem de log. A mensagem de exceção conterá o que deu errado, enquanto a mensagem de log deve ser usada para informar a um leitor de log o que o aplicativo estava fazendo quando a exceção aconteceu. A mensagem de exceção ainda será registrada. Ao especificar sua própria mensagem, os registros serão mais fáceis de entender.

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

### O logon em blocos de capturas deve estar no nível AVISO ou ERRO {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Chave**: CQRules:CQBP-44—WrongLogLevelInCatchBlock
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2018.4.0

Como o nome sugere, as exceções de Java devem sempre ser usadas em circunstâncias excepcionais. Como resultado, quando uma exceção é capturada, é importante garantir que as mensagens de log sejam registradas no nível apropriado: AVISO ou ERRO. Isso garante que essas mensagens sejam exibidas corretamente nos logs.

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

* **Chave**: CQRules:CQBP-44—ExceptionPrintStackTrace
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2018.4.0

O contexto é essencial ao entender as mensagens de log. Usando `Exception.printStackTrace()` faz com que somente o rastreamento de pilha seja enviado para o fluxo de erro padrão, perdendo todo o contexto. Além disso, em um aplicativo de vários segmentos, como AEM se várias exceções forem impressas em paralelo usando esse método, seus rastreamentos de pilha podem se sobrepor, o que gera uma confusão significativa. As exceções devem ser registradas somente por meio da estrutura de registro.

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
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2018.4.0

O AEM de logon deve ser sempre feito por meio da estrutura de registro, SLF4J. A saída diretamente para a saída padrão ou fluxos de erro padrão perde as informações estruturais e contextuais fornecidas pela estrutura de registro e pode, em alguns casos, causar problemas de desempenho.

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

### Evite caminhos /apps e /libs codificados {#avoid-hardcoded-apps-and-libs-paths}

* **Chave**: CQRules:CQBP-71
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2018.4.0

Em geral, caminhos que começam com `/libs` e `/apps` não deve ser codificado, pois os caminhos a que se referem são mais comumente armazenados como caminhos relativos ao caminho de pesquisa do Sling (que está definido como `/libs,/apps` por padrão). O uso do caminho absoluto pode apresentar defeitos sutis que só apareceriam posteriormente no ciclo de vida do projeto.

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

### O Sling Scheduler Não Deve Ser Usado {#sonarqube-sling-scheduler}

* **Chave**: CQRules:AMSCORE-554
* **Tipo**: Compatibilidade de Cheiro de Código/Cloud Service
* **Gravidade**: Menor
* **Since**: Versão 2020.5.0

O Sling Scheduler não deve ser usado para tarefas que exigem uma execução garantida. Os trabalhos agendados do Sling garantem a execução e são mais adequados para ambientes em cluster e não em cluster.

Consulte [Documentação de Evento e Manuseio de Trabalho do Apache Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) para saber mais sobre como os Sling Jobs são tratados em ambientes em cluster.

### AEM APIs obsoletas não devem ser usadas {#sonarqube-aem-deprecated}

* **Chave**: AMSCORE-553
* **Tipo**: Compatibilidade de Cheiro de Código/Cloud Service
* **Gravidade**: Menor
* **Since**: Versão 2020.5.0

A superfície da API de AEM está sob revisão constante para identificar APIs para as quais o uso é desencorajado e, portanto, considerado obsoleto.

Em muitos casos, essas APIs são descontinuadas usando o Java padrão *@Deprecated* anotação e, como tal, como identificada por `squid:CallToDeprecatedMethod`.

No entanto, há casos em que uma API é preterida no contexto de AEM, mas pode não ser preterida em outros contextos. Essa regra identifica essa segunda classe.

## Regras de conteúdo OakPAL {#oakpal-rules}

A seção a seguir detalha as verificações do OakPAL executadas pelo Cloud Manager.

>[!NOTE]
>
>OakPAL é uma estrutura, que valida pacotes de conteúdo usando um repositório Oak independente. Ele foi desenvolvido por um Parceiro AEM e vencedor do prêmio AEM Rockstar North America 2019.

### As APIs de produto anotadas com @ProviderType não devem ser implementadas ou estendidas por clientes {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Chave**: CQBP-84
* **Tipo**: Bug
* **Gravidade**: Crítico
* **Since**: Versão 2018.7.0

A API do AEM contém interfaces e classes do Java que devem ser usadas, mas não implementadas, apenas pelo código personalizado. Por exemplo, a interface `com.day.cq.wcm.api.Page` foi projetada para ser implementada somente pelo AEM.

Quando novos métodos são adicionados a essas interfaces, esses métodos adicionais não afetam o código existente que usa essas interfaces e, como resultado, a adição de novos métodos a essas interfaces é considerada compatível com versões anteriores. No entanto, se o código personalizado implementa uma dessas interfaces, ele apresenta um risco de compatibilidade com versões anteriores para o cliente.

Interfaces e classes que só devem ser implementadas por AEM são anotadas com `org.osgi.annotation.versioning.ProviderType` ou, em alguns casos, uma anotação herdada semelhante `aQute.bnd.annotation.ProviderType`. Esta regra identifica os casos em que essa interface é implementada ou em que uma classe é estendida por um código personalizado.

#### Código não compatível {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Os pacotes de clientes não devem criar ou modificar nós em /libs {#oakpal-customer-package}

* **Chave**: Caminho Banido
* **Tipo**: Bug
* **Gravidade**: Bloqueador
* **Since**: Versão 2019.6.0

Há muito que a melhor prática é que `/libs` a árvore de conteúdo no repositório de conteúdo AEM deve ser considerada somente leitura pelos clientes. Modificação de nós e propriedades em `/libs` cria riscos significativos para atualizações importantes e secundárias. Modificações em `/libs` só devem ser efetuadas pelo Adobe através de canais oficiais.

### Os pacotes não devem conter configurações OSGi duplicadas {#oakpal-package-osgi}

* **Chave**: DuplicateOsgiConfigurations
* **Tipo**: Bug
* **Gravidade**: Major
* **Since**: Versão 2019.6.0

Um problema comum que ocorre em projetos complexos é onde o mesmo componente OSGi é configurado várias vezes. Isso cria uma ambiguidade sobre qual configuração será operável. Essa regra é &quot;sensível ao modo de execução&quot; na medida em que só identificará problemas em que o mesmo componente é configurado várias vezes no mesmo modo de execução ou combinação de modos de execução.

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

* **Chave**: ConfigAndInstallshouldOnlyContainOsgiNodes
* **Tipo**: Bug
* **Gravidade**: Major
* **Since**: Versão 2019.6.0

Por motivos de segurança, caminhos que contêm `/config/` e `/install/` só podem ser lidos por usuários administrativos no AEM e devem ser usados apenas para configuração do OSGi e pacotes OSGi. Colocar outros tipos de conteúdo em caminhos que contêm esses segmentos resulta no comportamento do aplicativo, que varia de forma não intencional entre usuários administrativos e não administrativos.

Um problema comum é o uso de nós nomeados `config` nas caixas de diálogo do componente ou ao especificar a configuração do editor de rich text para edição em linha. Para resolver isso, o nó incorreto deve ser renomeado para um nome compatível. Para a configuração do editor de rich text, use o `configPath` na `cq:inplaceEditing` para especificar o novo local.

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

### Os Pacotes Não Devem Sobrepor {#oakpal-no-overlap}

* **Chave**: PackageOverlaps
* **Tipo**: Bug
* **Gravidade**: Major
* **Since**: Versão 2019.6.0

Semelhante ao [Os pacotes não devem conter a regra de configurações OSGi duplicadas,](#oakpal-package-osgi)  esse é um problema comum em projetos complexos, onde o mesmo caminho de nó é gravado por vários pacotes de conteúdo separados. Embora seja possível usar as dependências do pacote de conteúdo para garantir um resultado consistente, é melhor evitar sobreposições completamente.

### O Modo de Criação Padrão Não Deve Ser A Interface Clássica {#oakpal-default-authoring}

* **Chave**: ClassicUIAuthoringMode
* **Tipo**: Compatibilidade de Cheiro de Código/Cloud Service
* **Gravidade**: Menor
* **Since**: Versão 2020.5.0

A configuração do OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` define o modo de criação padrão no AEM. Porque [a interface do usuário clássica está obsoleta desde o AEM 6.4,](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html) um problema será gerado quando o modo de criação padrão estiver configurado para a interface do usuário clássica.

### Os Componentes Com Caixas De Diálogo Devem Ter Caixas De Diálogo Da Interface Do Usuário De Toque {#oakpal-components-dialogs}

* **Chave**: ComponentWithOnlyClassicUIDalog
* **Tipo**: Compatibilidade de Cheiro de Código/Cloud Service
* **Gravidade**: Menor
* **Since**: Versão 2020.5.0

AEM Os componentes que têm uma caixa de diálogo da interface clássica devem sempre ter uma caixa de diálogo da interface do usuário de toque correspondente, para fornecer uma experiência de criação ideal e para serem compatíveis com o modelo de implantação do Cloud Service, onde a interface do usuário clássica não é compatível. Essa regra verifica os seguintes cenários:

* Um componente com uma caixa de diálogo da interface clássica (ou seja, um `dialog` nó filho) deve ter uma caixa de diálogo da interface do usuário de toque correspondente (ou seja, um `cq:dialog` nó filho).
* Um componente com uma caixa de diálogo de design da interface clássica (ou seja, um `design_dialog` nó ) deve ter uma caixa de diálogo de design da interface do usuário de toque correspondente (ou seja, um `cq:design_dialog` nó filho).
* Um componente com uma caixa de diálogo da interface clássica e uma caixa de diálogo de design da interface clássica deve ter uma caixa de diálogo da interface do usuário de toque correspondente e uma caixa de diálogo de design da interface de toque correspondente.

A documentação das Ferramentas de Modernização do AEM fornece detalhes e ferramentas para converter componentes da interface clássica para a interface do usuário de toque. Consulte [A documentação das Ferramentas de Modernização do AEM ](https://opensource.adobe.com/aem-modernize-tools/) para obter mais detalhes.

### Os pacotes não devem misturar conteúdo mutável e imutável {#oakpal-packages-immutable}

* **Chave**: ImmutableMutableMixedPackage
* **Tipo**: Compatibilidade de Cheiro de Código/Cloud Service
* **Gravidade**: Menor
* **Since**: Versão 2020.5.0

Para serem compatíveis com o modelo de implantação do Cloud Service, os pacotes de conteúdo individuais devem conter conteúdo para as áreas imutáveis do repositório (ou seja, `/apps` e `/libs`) ou a área mutável (isto é, tudo não está em `/apps` ou `/libs`), mas não ambos. Por exemplo, um pacote que inclui ambos `/apps/myco/components/text and /etc/clientlibs/myco` O não é compatível com o Cloud Service e causará a criação de um relatório de problemas.

Consulte [Documentação AEM Estrutura do projeto](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html) para obter mais detalhes.

>[!NOTE]
>
>A regra [Os pacotes de clientes não devem criar ou modificar nós em /libs](#oakpal-customer-package) sempre se aplica.

### Os Agentes De Replicação Reversa Não Devem Ser Usados {#oakpal-reverse-replication}

* **Chave**: ReverseReplication
* **Tipo**: Compatibilidade de Cheiro de Código/Cloud Service
* **Gravidade**: Menor
* **Since**: Versão 2020.5.0

O suporte para replicação reversa não está disponível em implantações de Cloud Service, conforme descrito em [Notas de versão: Remoção dos agentes de replicação.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html#replication-agents)

Os clientes que usam replicação inversa devem entrar em contato com o Adobe para obter soluções alternativas.

### Os recursos contidos nas bibliotecas de clientes ativadas por proxy devem estar em uma pasta denominada recursos {#oakpal-resources-proxy}

* **Chave**: ClientlibProxyResource
* **Tipo**: Bug
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

AEM bibliotecas de clientes podem conter recursos estáticos, como imagens e fontes. Conforme descrito na [Usar a documentação de bibliotecas do lado do cliente,](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html#using-preprocessors) ao usar bibliotecas de cliente proxy, esses recursos estáticos devem estar contidos em uma pasta filho chamada `resources` para ser efetivamente referenciado nas instâncias de publicação.

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

* **Chave**: CloudServiceIncompatívelWorkflowProcess
* **Tipo**: Cheiro do código
* **Gravidade**: Bloqueador
* **Since**: Versão 2021.2.0

Com a mudança para os microsserviços de ativos para processamento de ativos no AEM Cloud Service, vários processos de fluxo de trabalho que foram usados nas versões local e AMS do AEM se tornaram incompatíveis ou desnecessários.

A ferramenta de migração no [Repositório GitHub as a Cloud Service da AEM Assets](https://github.com/adobe/aem-cloud-migration) O pode ser usado para atualizar modelos de fluxo de trabalho durante a migração para AEM as a Cloud Service.

### O uso de modelos estáticos é desincentivado em favor de modelos editáveis {#oakpal-static-template}

* **Chave**: StaticTemplateUsage
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

Embora o uso de modelos estáticos tenha sido historicamente muito comum em projetos AEM, os modelos editáveis são altamente recomendados, pois fornecem mais flexibilidade e suporte a recursos adicionais não presentes em modelos estáticos. Mais informações podem ser encontradas no [Modelos de página - Documentação editável.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-editable.html)

A migração de modelos estáticos para editáveis pode ser amplamente automatizada usando o [AEM Ferramentas de Modernização.](https://opensource.adobe.com/aem-modernize-tools/)

### O uso de componentes básicos herdados está desencorajado {#oakpal-usage-legacy}

* **Chave**: LegacyFoundationComponentUsage
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

Os componentes básicos herdados (ou seja, os componentes em `/libs/foundation`) foram descontinuadas para várias versões de AEM em favor do [Componentes principais.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=pt-BR) O uso dos componentes de base herdados como a base para componentes personalizados, seja por sobreposição ou herança, não é recomendado e deve ser convertido no componente principal correspondente.

Essa conversão pode ser facilitada pela [AEM Ferramentas de Modernização.](https://opensource.adobe.com/aem-modernize-tools/)

### Somente Nomes e Pedidos de Modo de Execução Suportados Devem Ser Usados {#oakpal-supported-runmodes}

* **Chave**: SupportedRunmode
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

O AEM Cloud Service impõe uma política de nomenclatura estrita para nomes de modo de execução e uma ordem estrita para esses modos de execução. A lista de modos de execução compatíveis pode ser encontrada no [Implantação em AEM documentação as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html#runmodes) e qualquer desvio em relação a isso será identificado como um problema.

### Os nós de definição do índice de pesquisa personalizado devem ser filhos diretos de /oak:index {#oakpal-custom-search}

* **Chave**: OakIndexLocation
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

O AEM Cloud Service exige que as definições de índice de pesquisa personalizadas (ou seja, nós do tipo `oak:QueryIndexDefinition`) ser nós filhos diretos de `/oak:index`. Os índices em outros locais devem ser movidos para serem compatíveis com o AEM Cloud Service. Mais informações sobre índices de pesquisa podem ser encontradas no [Documentação de pesquisa e indexação de conteúdo.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)

### Os nós de definição de índice de pesquisa personalizada devem ter uma compatVersion de 2 {#oakpal-custom-search-compatVersion}

* **Chave**: IndexCompatVersion
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

O AEM Cloud Service exige que as definições de índice de pesquisa personalizadas (ou seja, nós do tipo `oak:QueryIndexDefinition`) deve ter o `compatVersion` propriedade definida como `2`. Nenhum outro valor é suportado pela AEM Cloud Service. Mais informações sobre índices de pesquisa podem ser encontradas no [Documentação de pesquisa e indexação de conteúdo.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)

### Os Nós Descendentes dos Nós de Definição de Índice de Pesquisa Personalizado Devem Ser Do Tipo nt:unstructured {#oakpal-descendent-nodes}

* **Chave**: IndexDescendantNodeType
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

Problemas difíceis de solucionar podem ocorrer quando um nó de definição de índice de pesquisa personalizado tem nós filhos desordenados. Para evitar isso, é recomendável que todos os nós descendentes de um `oak:QueryIndexDefinition` nó ser do tipo `nt:unstructured`.

### Os nós de definição do índice de pesquisa personalizado devem conter um nó filho denominado indexRules que tenha filhos {#oakpal-custom-search-index}

* **Chave**: IndexRulesNode
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

Um nó de definição de índice de pesquisa personalizado corretamente definido deve conter um nó filho chamado `indexRules` que, por sua vez, deve ter pelo menos um filho. Mais informações podem ser encontradas no [Documentação do Oak.](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

### Os Nós De Definição De Índice De Pesquisa Personalizada Devem Seguir As Convenções De Nomenclatura {#oakpal-custom-search-definitions}

* **Chave**: IndexName
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

O AEM Cloud Service requer definições de índice de pesquisa personalizadas (ou seja, nós do tipo `oak:QueryIndexDefinition`) deve ser nomeado de acordo com um padrão específico descrito em [Pesquisa e indexação de conteúdo.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use)

### Os nós de definição de índice de pesquisa personalizada devem usar o lucene de tipo de índice  {#oakpal-index-type-lucene}

* **Chave**: IndexType
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

O AEM Cloud Service exige que as definições de índice de pesquisa personalizadas (ou seja, nós do tipo `oak:QueryIndexDefinition`) têm um `type` com o valor definido como `lucene`. A indexação usando tipos de índice herdados deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [Documentação de pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) para obter mais informações.

### Os nós de definição de índice de pesquisa personalizada não devem conter uma propriedade denominada seed {#oakpal-property-name-seed}

* **Chave**: IndexSeedProperty
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

O AEM Cloud Service proíbe definições de índice de pesquisa personalizadas (ou seja, nós do tipo `oak:QueryIndexDefinition`) de conter uma propriedade chamada `seed`. A indexação usando essa propriedade deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [Documentação de pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) para obter mais informações.

### Os nós de definição de índice de pesquisa personalizada não devem conter uma propriedade denominada reindex {#oakpal-reindex-property}

* **Chave**: IndexReindexProperty
* **Tipo**: Cheiro do código
* **Gravidade**: Menor
* **Since**: Versão 2021.2.0

O AEM Cloud Service proíbe definições de índice de pesquisa personalizadas (ou seja, nós do tipo `oak:QueryIndexDefinition`) de conter uma propriedade chamada `reindex`. A indexação usando essa propriedade deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [Documentação de pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) para obter mais informações.

## Ferramenta de otimização do Dispatcher {#dispatcher-optimization-tool-rules}

A seção a seguir lista as verificações da Ferramenta de Otimização do Dispatcher (DOT) executadas pelo Cloud Manager. Siga os links para cada verificação para obter sua definição e detalhes do GitHub.

* [Tokens inesperados da configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Cotação Sem Correspondência da Configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Chave ausente da configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Chave extra de configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Propriedade Obrigatória Ausente na Configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Propriedade Obsoleta de Configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Configuração do Dispatcher Não Encontrada](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Arquivo de Inclusão de Configuração Httpd não encontrado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Configuração Geral do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [O cache do farm de publicação do Dispatcher deve ter o serveStaleOnError ativado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Os filtros farm de publicação do Dispatcher devem conter as regras de negação padrão da versão 6.x.x do arquétipo de AEM](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [A propriedade statfileslevel do cache do farm de publicação do Dispatcher deve ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [A propriedade Publish farm GracePeriod do Dispatcher deve ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Cada farm do Dispatcher deve ter um nome exclusivo](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [O cache do farm de publicação do Dispatcher deve ter suas regras ignoreUrlParams configuradas de maneira lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Os filtros farm de publicação do Dispatcher devem especificar os seletores Sling permitidos de maneira lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Os filtros de farm de publicação do Dispatcher devem especificar os padrões de sufixo do Sling permitidos de maneira lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [A diretiva &quot;Require all given&quot; não deve ser usada em uma seção VirtualHost Diretory com um caminho de diretório raiz](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
