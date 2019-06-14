---
title: Regras de qualidade de código personalizadas
seo-title: Regras de qualidade de código personalizadas
description: Siga esta página para saber mais sobre as regras de qualidade de código personalizadas executadas pelo Experience Cloud Manager.
seo-description: Siga esta página para saber mais sobre as regras de qualidade de código personalizadas executadas pelo Gerenciador do Adobe Experience Manager Cloud.
uuid: a 7 feb 465-1982-46 be -9 e 57-e 67 b 59849579
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: usando
discoiquuid: d 2338 c 74-3278-49 e 6-a 186-6 ef 62362509 f
translation-type: tm+mt
source-git-commit: f8cea9d52ebb01d7f5291d4dfcd82011da8dacc2

---


# Regras de qualidade de código personalizadas {#custom-code-quality-rules}

Esta página descreve as regras de qualidade de código personalizadas executadas pelo Experience Manager Manager criadas com base nas práticas recomendadas da engenharia do AEM.

>[!NOTE]
>
>As amostras de código fornecidas aqui são apenas para fins ilustrativos.

## Regras sonarqube {#sonarqube-rules}

A seção a seguir destaca as Regras sonarqube:

### Não use funções potencialmente perigosas {#do-not-use-potentially-dangerous-functions}

**Chave**: Cqrules: CWE -676

**Tipo**: Vulnerabilidade

**Gravidade**: Principal

**Desde**: Versão 2018.4.0

Os métodos ***Thread. stop ()*** e ***Thread. interrompt ()*** podem produzir problemas difíceis de gerar e, em alguns casos, vulnerabilidades de segurança. Seu uso deve ser totalmente monitorado e validado. Em geral, a transmissão de mensagens é uma maneira mais segura de alcançar metas semelhantes.

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

### Não usar strings de formato que podem ser controladas externamente {#do-not-use-format-strings-which-may-be-externally-controlled}

**Chave**: Cqrules: CWE -134

**Tipo**: Vulnerabilidade

**Gravidade**: Principal

**Desde**: Versão 2018.4.0

O uso de uma sequência de formato de uma fonte externa (como um parâmetro de solicitação ou conteúdo gerado pelo usuário) pode expor um aplicativo para ataques de negação de serviço. Há circunstâncias em que uma string de formato pode ser controlada externamente, mas só é permitida de fontes confiáveis.

#### Código não compatível {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text");
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### As solicitações HTTP devem ter sempre o soquete e os tempos limite do Connect {#http-requests-should-always-have-socket-and-connect-timeouts}

**Chave**: Cqrules: Connectiontimeoutengine

**Tipo**: Bug

**Gravidade**: Crítica

**Desde**: Versão 2018.6.0

Ao executar solicitações HTTP de dentro de um aplicativo AEM, é fundamental garantir que os tempos limite apropriados sejam configurados para evitar o consumo desnecessário de encadeamento. Infelizmente, o comportamento padrão do cliente HTTP padrão de Java (java.net.Ht tahlconnection) e o cliente de Componentes HTTP de comumente usado é nunca tempo limite, portanto os tempos limite devem ser definidos explicitamente. Além disso, como prática recomendada, esses tempos limite não devem exceder 60 segundos.

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

### As apis de produto anotadas com @ providertype não devem ser implementadas ou estendidas por clientes {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Chave**: CQBP -84, CQBP -84-dependências

**Tipo**: Bug

**Gravidade**: Crítica

**Desde**: Versão 2018.7.0

A API do AEM contém interfaces e classes Java que devem ser usadas somente, mas não implementadas, pelo código personalizado. Por exemplo, a interface *com.day.cq.wc m. api. Página* é projetada para ser implementada somente pelo ***AEM***.

Quando novos métodos são adicionados a essas interfaces, esses métodos adicionais não afetam o código existente que usa essas interfaces e, como resultado, a adição de novos métodos a essas interfaces é considerada compatível com versões anteriores. No entanto, se o código ***personalizado implementa*** uma dessas interfaces, esse código personalizado introduziu um risco de compatibilidade retroativa para o cliente.

As interfaces (e classes) que devem ser implementadas apenas pelo AEM são anotadas com *org. osgi. annotation. versioning. standertype* (ou, em alguns casos, uma anotação herdada similar *aqute. bnd. annotation. standertype*). Essa regra identifica os casos em que uma interface é implementada (ou uma classe é estendida) pelo código personalizado.

#### Código não compatível {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Os objetos resourceresolver devem sempre ser fechados {#resourceresolver-objects-should-always-be-closed}

**Chave**: Cqrules: CQBP -72

**Tipo**: Código Smell

**Gravidade**: Principal

**Desde**: Versão 2018.4.0

Os objetos resourceresolver obtidos de resourceresolverfactory consomem os recursos do sistema. Embora haja medidas em vigor para recuperar esses recursos quando um resourceresolver não estiver mais em uso, é mais eficiente fechar explicitamente quaisquer objetos resourceresolver abertos chamando o método close ().

Um equívoco relativamente comum é que os objetos resourceresolver criados usando uma Sessão JCR existente não devem ser fechados explicitamente ou que isso fechará a Sessão JCR subjacente. Esse não é o caso - independentemente de como um resourceresolver é aberto, ele deve ser fechado quando não for mais usado. Como o resourceresolver implementa a interface que pode ser fechada, também é possível usar a sintaxe try-with-resources em vez de chamar explicitamente fechar ().

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

### Não use caminhos de servlet Sling para registrar servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

**Chave**: Cqrules: CQBP -75

**Tipo**: Código Smell

**Gravidade**: Principal

**Desde**: Versão 2018.4.0

Conforme descrito na documentação [Sling](http://sling.apache.org/documentation/the-sling-engine/servlets.html), os servlets de vínculos por caminhos são desencorajados. Servlets vinculados a caminho não podem usar controles de acesso JCR padrão e, como resultado, exigir diferenciação adicional de segurança. Em vez de usar servlets vinculados a caminho, é recomendável criar nós no repositório e registrar servlets por tipo de recurso.

#### Código não compatível {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Capture Exceptions deve ser registrado ou lançado, mas não {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**Chave**: Cqrules: CQBP -44—Catchandeitherlogorthrow

**Tipo**: Código Smell

**Gravidade**: Menor

**Desde**: Versão 2018.4.0

Em geral, uma exceção deve ser registrada exatamente de uma vez. Fazer logon várias vezes pode causar confusão, pois não é claro quantas vezes uma exceção ocorreu. O padrão mais comum que leva a isso é registrar e lançar uma exceção capturada.

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

### Evitar ter uma declaração de log imediatamente seguida por uma instrução throw {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Chave**: Cqrules: CQBP -44—Pathightylogandthrow

**Tipo**: Código Smell

**Gravidade**: Menor

**Desde**: Versão 2018.4.0

Outro padrão comum a evitar é registrar uma mensagem e lançar imediatamente uma exceção. Isso geralmente indica que a mensagem de exceção será encerrada em arquivos de log.

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

### Evite o logon em INFO ao lidar com solicitações GET ou HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Chave**: Cqrules: CQBP -44—Loginfoingetorheadrequests

**Tipo**: Código Smell

**Gravidade**: Menor

Em geral, o nível de log INFO deve ser usado para demarcar ações importantes e, por padrão, o AEM está configurado para registrar no nível INFO ou acima. Os métodos GET e HEAD devem ser apenas operações somente leitura e, portanto, não constituem ações importantes. Fazer logon no nível INFO em resposta a solicitações GET ou HEAD provavelmente criará ruído de log significativo facilitando a identificação de informações úteis em arquivos de log. Fazer logon na manipulação de solicitações GET ou HEAD deve estar nos níveis WARN ou ERROR quando algo correu errado ou nos níveis DEBUG ou TRACE se informações de solução de problemas mais profundas forem úteis.

>[!CAUTION]
>
>Isso não se aplica ao registro de tipo access. log para cada solicitação.

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

### Não use Exceção. getmessage () como o primeiro parâmetro de uma declaração de registro {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**Chave**: Cqrules: CQBP -44—Exceptiongetmessageisfirstlogparam

**Tipo**: Código Smell

**Gravidade**: Menor

**Desde**: Versão 2018.4.0

Como prática recomendada, as mensagens de registro devem fornecer informações contextuais sobre onde no aplicativo uma exceção ocorreu. Embora o contexto também possa ser determinado por meio do uso de traçados de pilha, em geral, a mensagem de registro será mais fácil de ler e entender. Como resultado, ao registrar uma exceção, é uma prática incorreta usar a mensagem da exceção como mensagem de registro - a mensagem de exceção conterá o que foi errado, pois a mensagem de registro deve ser usada para informar ao leitor de log o que o aplicativo estava fazendo quando a exceção aconteceu. A mensagem de exceção ainda será registrada; ao especificar sua própria mensagem, os logs serão mais fáceis de entender.

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

### O logon em blocos catch deve estar no nível WARN ou ERROR {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**Chave**: Cqrules: CQBP -44—Wrongloglevelincatchblock

**Tipo**: Código Smell

**Gravidade**: Menor

**Desde**: Versão 2018.4.0

Como sugere o nome, as exceções do Java devem ser sempre usadas em *circunstâncias excepcionais* . Como resultado, quando uma exceção é detectada, é importante garantir que as mensagens de registro sejam registradas no nível apropriado - seja BOM ou ERROR. Isso garante que essas mensagens sejam exibidas corretamente nos logs.

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

### Não imprimir traçados de pilha no console {#do-not-print-stack-traces-to-the-console}

**Chave**: Cqrules: CQBP -44—Exceptionprintstacktrace

**Tipo**: Código Smell

**Gravidade**: Menor

**Desde**: Versão 2018.4.0

Como mencionado, o contexto é essencial ao entender as mensagens de log. Usar exceção. printstacktrace () faz com **que somente** o rastreamento de pilha seja produzido para o fluxo de erro padrão, perdendo assim todo o contexto. Além disso, em um aplicativo com vários segmentos como o AEM, se várias exceções forem impressas usando esse método simultaneamente, seus rastreadores de pilha poderão se sobrepor, o que produz uma confusão significativa. As exceções devem ser registradas apenas na estrutura de logon.

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

### Não coloque para Saída padrão ou Erro padrão {#do-not-output-to-standard-output-or-standard-error}

**Chave**: Cqrules: CQBP -44—loglevelconsoleprinters

**Tipo**: Código Smell

**Gravidade**: Menor

**Desde**: Versão 2018.4.0

O logon no AEM deve ser sempre executado na estrutura de logon (SLF 4 J). A saída diretamente na saída padrão ou fluxos de erros padrão perde as informações estruturais e contextuais fornecidas pela estrutura de logon e pode, em alguns casos, causar problemas de desempenho.

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

### Evite /apps e /libs Caminhos codificados {#avoid-hardcoded-apps-and-libs-paths}

**Chave**: Cqrules: CQBP -71

**Tipo**: Código Smell

**Gravidade**: Menor

**Desde**: Versão 2018.4.0

Em geral, os caminhos que começam com /libs e /apps não devem ser codificados como os caminhos que referem são mais armazenados como caminhos relativos ao caminho de pesquisa Sling (que é definido como /libs,/aplicativos por padrão). O uso do caminho absoluto pode apresentar defeitos sutil que só apareceriam posteriormente no ciclo de vida do projeto.

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
