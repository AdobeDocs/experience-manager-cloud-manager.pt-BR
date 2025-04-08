---
title: Regras de qualidade do código personalizado
description: Descubra as especificidades das regras de qualidade de código personalizado executadas pelo Cloud Manager durante os testes de qualidade. Essas regras são baseadas nas práticas recomendadas pela engenharia do AEM.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 8388edb5510ed4583a7bc703f3781af03d976948
workflow-type: tm+mt
source-wordcount: '3644'
ht-degree: 96%

---


# Regras de qualidade do código personalizado {#custom-code-quality-rules}

Saiba mais sobre as regras de qualidade de código personalizado executadas pelo Cloud Manager como parte dos [testes de qualidade de código](/help/using/code-quality-testing.md), com base nas práticas recomendadas pela equipe de engenharia do AEM.

>[!NOTE]
>
>As amostras de código fornecidas aqui são apenas para fins ilustrativos. Consulte a [Documentação de conceitos da SonarQube](https://docs.sonarsource.com/sonarqube-server/latest/) para conhecer seus conceitos e regras de qualidade.

As regras completas do SonarQube não estão disponíveis para download devido às informações proprietárias da Adobe. Você pode baixar a lista completa de regras [usando este link](/help/assets/CodeQuality-rules-latest-AMS.xlsx). Continue a ler este documento para obter descrições e exemplos das regras.

>[!IMPORTANT]
>
>A partir de quinta-feira, 13 de fevereiro de 2025 (Cloud Manager 2025.2.0), a qualidade de código do Cloud Manager usará uma versão atualizada do SonarQube 9.9 e uma lista atualizada de regras que você pode [baixar aqui](/help/assets/CodeQuality-rules-latest-AMS-2024-12-0.xlsx).

## Regras do SonarQube {#sonarqube-rules}

A seção a seguir especifica as regras do SonarQube executadas pelo Cloud Manager.

### Não usar funções potencialmente perigosas {#do-not-use-potentially-dangerous-functions}

* **Chave**: CQRules:CWE-676
* **Tipo**: Vulnerabilidade
* **Severidade**: Alta
* **Desde**: Versão 2018.4.0

Os métodos `Thread.stop()` e `Thread.interrupt()` podem gerar problemas difíceis de reproduzir e, em alguns casos, vulnerabilidades de segurança. A utilização deve ser rigorosamente monitorizada e validada. Em geral, a transmissão de mensagens é uma forma mais segura de atingir objetivos semelhantes.

#### Código não compatível  {#non-compliant-code}

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

#### Código compatível  {#compliant-code}

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

### Não use strings de formatação que possam ser controladas externamente  {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Chave**: CQRules:CWE-134
* **Tipo**: Vulnerabilidade
* **Severidade**: Alta
* **Desde**: Versão 2018.4.0

Usar uma string de formatação de uma fonte externa (como um parâmetro de solicitação ou conteúdo gerado pelo usuário) pode expor um aplicativo a ataques de negação de serviço. Há casos em que uma string de formatação pode ser controlada externamente, mas isso somente é permitido de fontes confiáveis.

#### Código não compatível  {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### As solicitações HTTP devem sempre ter um tempo limite de soquete e conexão {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Chave**: CQRules:ConnectionTimeoutMechanism
* **Tipo**: Erro
* **Severidade**: Crítica
* **Desde**: Versão 2018.6.0

Ao executar solicitações HTTP de dentro de um aplicativo do AEM, é essencial garantir que os tempos limite sejam configurados adequadamente para evitar um consumo desnecessário de threads. Infelizmente, o cliente HTTP padrão do Java™, `java.net.HttpUrlConnection`, e o cliente Apache HTTP Components amplamente usado não têm um tempo limite padrão. Portanto, é necessário configurar os tempos limite explicitamente. Como prática recomendada, essas ocorrências de tempo limite não devem exceder 60 segundos.

#### Código não compatível  {#non-compliant-code-2}

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

#### Código compatível  {#compliant-code-1}

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

### Sempre feche os objetos `ResourceResolver` {#resourceresolver-objects-should-always-be-closed}

* **Chave**: CQRules:CQBP-72
* **Tipo**: `Code Smell`
* **Severidade**: Alta
* **Desde**: Versão 2018.4.0

Objetos `ResourceResolver` obtidos do `ResourceResolverFactory` consumem recursos do sistema. Embora existam medidas em vigor para recuperar esses recursos quando um `ResourceResolver` não é mais utilizado, é mais eficiente fechar explicitamente todos os objetos `ResourceResolver` abertos chamando o método `close()`.

Um equívoco comum é achar que não se deve fechar explicitamente os objetos `ResourceResolver` criados em uma sessão JCR existente. Outro equívoco é pensar que fechar esses objetos fechará a sessão JCR subjacente. Não é isso o que ocorre. Independentemente de como um `ResourceResolver` foi aberto, deve-se fechá-lo quando não estiver mais em uso. Como o `ResourceResolver` implementa a interface `Closeable`, também é possível usar a sintaxe `try-with-resources` em vez de chamar explicitamente `close()`.

#### Código não compatível  {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Código compatível  {#compliant-code-2}

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

### Não use caminhos de servlet do Sling para registrar servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Chave**: CQRules:CQBP-75
* **Tipo**: `Code Smell`
* **Severidade**: Alta
* **Desde**: Versão 2018.4.0

Conforme descrito na [documentação do Sling](https://sling.apache.org/documentation/the-sling-engine/servlets.html), vincular os servlets por caminhos não é recomendado. Os servlets vinculados a caminhos não podem usar os controles de acesso JCR padrão e, como resultado disso, exigem maior rigor de segurança. Em vez de usar servlets vinculados a caminhos, é recomendado criar nós no repositório e registrar os servlets por tipo de recurso.

#### Código não compatível  {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### As exceções capturadas devem ser registradas ou descartadas, mas não ambos {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Chave**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Em geral, uma exceção deve ser registrada exatamente uma vez. O registro múltiplo de exceções pode causar confusão porque não deixa claro quantas vezes uma exceção ocorreu. O hábito mais comum que resulta nisso é registrar e emitir uma exceção de captura.

#### Código não compatível  {#non-compliant-code-6}

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

#### Código compatível  {#compliant-code-3}

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

### Evite declarações de log imediatamente seguidas por instruções de emissão {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Chave**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Outro padrão comum a ser evitado é registrar uma mensagem e imediatamente depois lançar uma exceção. Isso geralmente indica que a mensagem de exceção acabará duplicada nos arquivos de log. 

#### Código não compatível  {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Código compatível  {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Evite registrar no nível INFO ao manipular solicitações GET ou HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Chave**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Tipo**: `Code Smell`
* **Severidade**: Baixa

Em geral, o nível de log INFO deve ser usado para demarcar ações importantes e, por padrão, o AEM é configurado para fazer logon no nível INFO ou superior. Os métodos GET e HEAD devem ser operações somente leitura e, portanto, não constituem ações importantes. Registrar no nível INFO em resposta a solicitações GET ou HEAD provavelmente criará um ruído significativo de log, dificultando a identificação de informações úteis em arquivos de log. Ao manipular solicitações GET ou HEAD, o registro deve estar na camada de AVISO ou ERRO, se algo tiver dado errado. Para informações mais detalhadas sobre resolução de problemas, o registro deve estar na camada DEBUG ou TRACE.

>[!NOTE]
>
>Esse fluxo de trabalho não se aplica ao registro de access.log-type para cada solicitação.

#### Código não compatível  {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Código compatível  {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Não use `Exception.getMessage()` como o primeiro parâmetro de uma instrução de registro  {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Chave**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Como prática recomendada, as mensagens de log devem fornecer informações contextuais sobre onde ocorreu uma exceção no aplicativo. Embora o contexto também possa ser determinado pelo uso de rastros de pilha, em geral, a mensagem de log será mais fácil de ler e entender. Como resultado disso, ao registrar uma exceção, não é uma prática recomendada usar a mensagem da exceção como a mensagem de registro. A mensagem de exceção deve detalhar o que deu errado. Por outro lado, a mensagem de log deve informar quem está lendo sobre o que o aplicativo estava fazendo quando a exceção ocorreu. A mensagem de exceção ainda é registrada. Ao especificar sua própria mensagem, será mais fácil entender os logs. 

#### Código não compatível  {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Código compatível  {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Os logs em blocos de catch devem estar no nível AVISO ou ERRO {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Chave**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Como o nome sugere, as exceções do Java™ sempre devem ser usadas em casos excepcionais. Como resultado, quando uma exceção é capturada, é importante garantir que as mensagens de log sejam registradas no nível apropriado: AVISO ou ERRO. Isso garante a exibição correta dessas mensagens nos logs.

#### Código não compatível  {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Código compatível  {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Não imprimir rastros de pilha no console {#do-not-print-stack-traces-to-the-console}

* **Chave**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

O contexto é essencial ao entender as mensagens de log. Usar `Exception.printStackTrace()` faz com que somente o rastro de pilha seja enviado para o fluxo de erro padrão, perdendo todo o contexto. Além disso, em um aplicativo com várias threads como o AEM, se várias exceções forem impressas com esse método em paralelo, seus rastros de pilha podem se sobrepor, gerando bastante confusão. As exceções devem ser registradas somente por meio da estrutura de registro.

#### Código não compatível  {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Código compatível  {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Não envie para a saída padrão ou fluxo de erro padrão {#do-not-output-to-standard-output-or-standard-error}

* **Chave**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

O logon no AEM sempre deve ser feito por meio da estrutura de log, SLF4J. Ao enviar diretamente para a saída padrão ou para fluxos de erro padrão, as informações estruturais e contextuais fornecidas pela estrutura de registro são perdidas e podem, em alguns casos, causar problemas de desempenho.

#### Código não compatível  {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Código compatível  {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Evite caminhos `/apps` e `/libs` codificados {#avoid-hardcoded-apps-and-libs-paths}

* **Chave**: CQRules:CQBP-71
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2018.4.0

Caminhos que começam com `/libs` e `/apps` geralmente não devem ser codificados. Normalmente, esses caminhos são armazenados em relação ao caminho de pesquisa do Sling, que tem como padrão `/libs,/apps`. O uso do caminho absoluto pode gerar defeitos sutis que só aparecerão posteriormente no ciclo de vida do projeto.

#### Código não compatível  {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Código compatível  {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Não use o scheduler do Sling {#sonarqube-sling-scheduler}

* **Chave**: CQRules:AMSCORE-554
* **Tipo**: compatibilidade entre `Code Smell` e o Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

Não use o Sling Scheduler para tarefas que exigem uma execução garantida. Os processos agendados no Sling têm execução garantida e são mais adequados para ambientes clusterizados e não clusterizados.

Consulte a [documentação sobre manuseio de processos e eventos do Apache Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) para saber mais sobre como os processos do Sling são tratados em ambientes clusterizados.

### Não utilize APIs obsoletas do AEM {#sonarqube-aem-deprecated}

* **Chave**: AMSCORE-553
* **Tipo**: compatibilidade entre `Code Smell` e o Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

As APIs do AEM estão em constante revisão para identificar quais não devem mais ser usadas e, portanto, consideradas descontinuadas.

Muitas vezes, essas APIs são obsoletas usando a anotação padrão Java™ *@Deprecated* e, sendo assim, são identificadas por `squid:CallToDeprecatedMethod`.

No entanto, há casos em que uma API é obsoleta no contexto do AEM, mas pode não ser obsoleta em outros contextos. Esta regra identifica essa segunda classe.

## Regras de conteúdo OakPAL {#oakpal-rules}

A seção a seguir especifica as verificações do OakPAL executadas pelo Cloud Manager.

>[!NOTE]
>
>O OakPAL é uma estrutura que valida pacotes de conteúdo usando um repositório Oak autônomo. Ela foi desenvolvida por um parceiro do AEM, vencedor do prêmio AEM Rock Star North America 2019.

### Clientes não devem implementar nem estender APIs de produto anotadas com @ProviderType {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Chave**: CQBP-84
* **Tipo**: Erro
* **Severidade**: Crítica
* **Desde**: Versão 2018.7.0

A API do AEM contém interfaces e classes Java™ que devem apenas ser usadas (não implementadas) por meio de um código personalizado. Por exemplo, somente o AEM implementa a interface `com.day.cq.wcm.api.Page`.

Adicionar novos métodos a essas interfaces não afeta o código existente, tornando a adição de novos métodos compatível com versões anteriores. No entanto, se o código personalizado implementa uma dessas interfaces, ele apresenta um risco de compatibilidade com versões anteriores para o cliente.

O AEM anota interfaces e classes destinadas exclusivamente à sua implementação com `org.osgi.annotation.versioning.ProviderType` ou, ocasionalmente, a anotação herdada, `aQute.bnd.annotation.ProviderType`. Esta regra detecta instâncias em que o código personalizado implementa essa interface ou estende uma classe.

#### Código não compatível {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Os pacotes de clientes não devem criar nem editar nós em `/libs` {#oakpal-customer-package}

* **Chave**: BannedPath
* **Tipo**: Erro
* **Gravidade**: Bloqueador
* **Desde**: Versão 2019.6.0

Uma prática recomendada já consolidada é que a árvore de conteúdo `/libs` no repositório de conteúdo do AEM deve ser considerada somente leitura pelos clientes. A modificação dos nós e propriedades em `/libs` cria riscos significativos para atualizações importantes e secundárias. As edições de `/libs` são feitas pela Adobe apenas por meio de canais oficiais.

### Os pacotes não devem conter configurações de OSGi duplicadas {#oakpal-package-osgi}

* **Chave**: DuplicateOsgiConfigurations
* **Tipo**: Erro
* **Severidade**: Alta
* **Desde**: Versão 2019.6.0

Um problema comum que ocorre em projetos complexos é quando o mesmo componente OSGi é configurado várias vezes. Isso cria uma ambiguidade sobre qual configuração é operável. Essa regra age de acordo com o modo de execução, no sentido de que ela apenas identifica problemas em que o mesmo componente é configurado várias vezes no mesmo modo de execução ou combinação de modos de execução.

#### Código não compatível  {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Código compatível  {#compliant-code-osgi}

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

Por motivos de segurança, caminhos que contêm `/config/` e `/install/` somente podem ser lidos por usuários administrativos no AEM e devem ser usados apenas para a configuração do OSGi e os pacotes do OSGi. Colocar outros tipos de conteúdo em caminhos que contêm esses segmentos faz com que o aplicativo varie de forma não intencional entre usuários administrativos e não administrativos.

Um problema comum é o uso de nós nomeados como `config` nas caixas de diálogo de componente ou ao especificar a configuração do editor de rich text para edição em linha. Para solucionar esse problema, o nó incorreto deve ser renomeado para um nome que esteja em conformidade. Para configurar o editor de rich text, use a propriedade `configPath` do nó `cq:inplaceEditing` para especificar o novo local.

#### Código não compatível  {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Código compatível  {#compliant-code-config-install}

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

Semelhante à regra [Pacotes não devem conter configurações OSGi duplicadas](#oakpal-package-osgi), esse é um problema comum em projetos complexos nos quais o mesmo caminho de nó é gravado por vários pacotes de conteúdo separados. Embora seja possível usar as dependências do pacote de conteúdo para garantir um resultado consistente, é melhor evitar qualquer sobreposição.

### O modo de criação padrão não deve ser a interface clássica {#oakpal-default-authoring}

* **Chave**: ClassicUIAuthoringMode
* **Tipo**: compatibilidade entre `Code Smell` e o Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

A configuração do OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` define o modo de autoria padrão no AEM. Como a interface clássica foi descontinuada no AEM 6.4, um problema será gerado quando o modo de criação padrão estiver configurado para usá-la.

### Componentes com caixas de diálogo devem ter caixas de diálogo de interface sensível ao toque {#oakpal-components-dialogs}

* **Chave**: ComponentWithOnlyClassicUIDialog
* **Tipo**: compatibilidade entre `Code Smell` e o Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

Componentes do AEM com uma caixa de diálogo com interface clássica também devem ter uma caixa de diálogo com interface sensível ao toque para um processo de criação ideal e compatível com o modelo de implantação do Cloud Service, que não é compatível com a interface clássica. Essa regra verifica os seguintes cenários:

* Um componente com uma caixa de diálogo da interface do usuário clássica (ou seja, um nó secundário `dialog`) deve ter uma caixa de diálogo da interface do usuário de toque correspondente (ou seja, um nó secundário `cq:dialog`).
* Um componente com uma caixa de diálogo de design com interface clássica (ou seja, um nó `design_dialog`) deve ter uma caixa de diálogo de design com interface de toque correspondente (ou seja, um nó secundário `cq:design_dialog`).
* Um componente com uma caixa de diálogo com interface clássica e uma caixa de diálogo de design com interface clássica deve ter uma caixa de diálogo com interface de toque e uma caixa de diálogo de design com interface de toque correspondentes.

A documentação das Ferramentas de modernização do AEM fornece detalhes e ferramentas para converter componentes da interface clássica para a interface de toque. Consulte [a documentação das ferramentas de modernização do AEM](https://opensource.adobe.com/aem-modernize-tools/) para mais detalhes.

### Não use agentes de replicação reversa {#oakpal-reverse-replication}

* **Chave**: ReverseReplication
* **Tipo**: compatibilidade entre `Code Smell` e o Cloud Service
* **Severidade**: Baixa
* **Desde**: Versão 2020.5.0

A compatibilidade com a replicação reversa não está disponível em implantações do Cloud Service, conforme descrito nas [Notas de versão: remoção de agentes de replicação](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents).

Os clientes que usam replicação reversa devem entrar em contato com a Adobe para obter soluções alternativas.

### Os recursos contidos nas bibliotecas de clientes ativadas por proxy devem estar em uma pasta chamada “resources” {#oakpal-resources-proxy}

* **Chave**: ClientlibProxyResource
* **Tipo**: Erro
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

As bibliotecas de clientes do AEM podem conter recursos estáticos, como imagens e fontes. Conforme descrito na [documentação sobre o uso de bibliotecas do lado do cliente](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors), ao usar bibliotecas de clientes com proxy, esses recursos estáticos devem estar contidos em uma pasta secundária chamada de `resources` para serem referenciados corretamente nas instâncias de publicação.

#### Código não compatível  {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Código compatível  {#compliant-proxy-enabled}

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
* **Tipo**: `Code Smell`
* **Gravidade**: Bloqueador
* **Desde**: Versão 2021.2.0

Com a mudança para os microsserviços de ativos no processamento de ativos do AEM Cloud Service, vários processos de fluxo de trabalho usados nas versões local e AMS do AEM tornaram-se incompatíveis ou desnecessários.

É possível usar a ferramenta de migração no [repositório GitHub do AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) para atualizar modelos de fluxo de trabalho durante a migração para o AEM as a Cloud Service.

### Recomendamos o uso de modelos editáveis em vez de modelos estáticos {#oakpal-static-template}

* **Chave**: StaticTemplateUsage
* **Tipo**: `Code Smell` 
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Embora o uso de modelos estáticos tenha sido historicamente comum em projetos AEM, os modelos editáveis são altamente recomendados, pois fornecem maior flexibilidade e são compatíveis com recursos adicionais que não estão presentes nos modelos estáticos. Para mais informações, consulte a [documentação Modelos de página - Editáveis](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable).

A migração de modelos estáticos para editáveis pode ser amplamente automatizada usando as [Ferramentas de modernização do AEM](https://opensource.adobe.com/aem-modernize-tools/).

### O uso de componentes básicos herdados não é recomendado {#oakpal-usage-legacy}

* **Chave**: LegacyFoundationComponentUsage
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Os componentes fundamentais legados (ou seja, os componentes em `/libs/foundation`) foram descontinuados em várias versões do AEM a fim de priorizar o uso dos [componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction). Não é recomendado utilizar componentes fundamentais legados como base para componentes personalizados, seja por sobreposição ou herança; em vez disso, use o componente principal correspondente.

[As ferramentas de modernização do AEM](https://opensource.adobe.com/aem-modernize-tools/) podem facilitar essa conversão.

### Os nós de definição do índice de pesquisa personalizado devem ser nós secundários diretos de `/oak:index` {#oakpal-custom-search}

* **Chave**: OakIndexLocation
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service exige que as definições de índice de pesquisa personalizado (ou seja, nós do tipo `oak:QueryIndexDefinition`) sejam nós secundários diretos de `/oak:index`. Os índices em outros locais devem ser movidos para serem compatíveis com o AEM Cloud Service. Para mais informações sobre índices de pesquisa, consulte a [documentação de Pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/operations/indexing).

### Os nós de definição do índice de pesquisa personalizada devem ter uma compatVersion de 2 {#oakpal-custom-search-compatVersion}

* **Chave**: IndexCompatVersion
* **Tipo**: `Code Smell` 
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service exige que as definições de índice de pesquisa personalizado (ou seja, nós do tipo `oak:QueryIndexDefinition`) tenham a propriedade `compatVersion` definida como `2`. O AEM Cloud Service não é compatível com nenhum outro valor. Para mais informações sobre índices de pesquisa, consulte a [documentação de Pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/operations/indexing).

### Os nós descendentes dos nós de definição do índice de pesquisa personalizado devem ser do tipo `nt:unstructured` {#oakpal-descendent-nodes}

* **Chave**: IndexDescendantNodeType
* **Tipo**: `Code Smell` 
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Problemas difíceis de solucionar podem ocorrer quando um nó de definição de índice de pesquisa personalizada tem nós secundários desordenados. Para evitar esses nós, a Adobe recomenda que todos os nós descendentes de um nó `oak:QueryIndexDefinition` sejam do tipo `nt:unstructured`.

### Os nós de definição do índice de pesquisa personalizado devem conter um nó secundário denominado `indexRules`, o qual possua nós secundários {#oakpal-custom-search-index}

* **Chave**: IndexRulesNode
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

Um nó de definição do índice de pesquisa personalizado definido corretamente deve conter um nó secundário chamado de `indexRules`, o qual deve ter pelo menos um nó secundário. Para mais informações, consulte a [documentação do Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Os nós de definição do índice de pesquisa personalizado devem seguir as convenções de nomeação {#oakpal-custom-search-definitions}

* **Chave**: IndexName
* **Tipo**: `Code Smell` 
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service exige que as definições do índice de pesquisa personalizado (ou seja, nós do tipo `oak:QueryIndexDefinition`) sejam nomeadas de acordo com um padrão específico descrito em [Pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use).

### Os nós de definição do índice de pesquisa personalizado devem usar o tipo de índice Lucene {#oakpal-index-type-lucene}

* **Chave**: IndexType
* **Tipo**: `Code Smell` 
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service exige que as definições do índice de pesquisa personalizado (ou seja, nós do tipo `oak:QueryIndexDefinition`) tenham uma propriedade `type` com o valor definido como `lucene`. A indexação usando tipos de índice herdados deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [documentação de Pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) para obter mais informações.

### Os nós de definição do índice de pesquisa personalizado não devem conter uma propriedade denominada `seed` {#oakpal-property-name-seed}

* **Chave**: IndexSeedProperty
* **Tipo**: `Code Smell`
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service proíbe definições de índice de pesquisa personalizada (ou seja, nós do tipo `oak:QueryIndexDefinition`) de conter uma propriedade chamada `seed`. A indexação usando essa propriedade deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [documentação de Pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) para obter mais informações.

### Os nós de definição do índice de pesquisa personalizado não devem conter uma propriedade denominada `reindex` {#oakpal-reindex-property}

* **Chave**: IndexReindexProperty
* **Tipo**: `Code Smell` 
* **Severidade**: Baixa
* **Desde**: Versão 2021.2.0

O AEM Cloud Service proíbe definições de índice de pesquisa personalizada (ou seja, nós do tipo `oak:QueryIndexDefinition`) de conter uma propriedade chamada `reindex`. A indexação usando essa propriedade deve ser atualizada antes da migração para o AEM Cloud Service. Consulte a [documentação de Pesquisa e indexação de conteúdo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) para obter mais informações.

### Não implante nós de definição de índice no pacote de conteúdo da interface {#oakpal-ui-content-package}

* **Chave**: IndexNotUnderUIContent
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2024.6.0

O AEM Cloud Service proíbe que definições de índice de pesquisa personalizadas (nós do tipo `oak:QueryIndexDefinition`) sejam implantadas no pacote de conteúdo da interface.

>[!WARNING]
>
>Recomendamos que você resolva esse problema o mais rápido possível, pois ele poderá causar falhas nos pipelines a partir da [versão de agosto de 2024 do Cloud Manager](/help/release-notes/current.md).

### Uma definição de índice de texto completo personalizado do tipo `damAssetLucene` deve receber o prefixo correto de `damAssetLucene` {#oakpal-dam-asset-lucene}

* **Chave**: CustomFulltextIndexesOfTheDamAssetCheck
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2024.6.0

O AEM Cloud Service proíbe que definições de índice de texto completo personalizadas do tipo `damAssetLucene` sejam prefixadas com qualquer item diferente de `damAssetLucene`.

>[!WARNING]
>
>Recomendamos que você resolva esse problema o mais rápido possível, pois ele poderá causar falhas nos pipelines a partir da [versão de agosto de 2024 do Cloud Manager](/help/release-notes/current.md).

### Nós de definição de índice não devem conter propriedades com o mesmo nome {#oakpal-index-property-name}

* **Chave**: DuplicateNameProperty
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2024.6.0

O AEM Cloud Service proíbe que definições de índice de pesquisa personalizadas (ou seja, nós do tipo `oak:QueryIndexDefinition`) contenham propriedades com o mesmo nome

>[!WARNING]
>
>Recomendamos que você resolva esse problema o mais rápido possível, pois ele poderá causar falhas nos pipelines a partir da [versão de agosto de 2024 do Cloud Manager](/help/release-notes/current.md).

### A personalização de determinadas definições de índice prontas para uso é proibida {#oakpal-customizing-ootb-index}

* **Chave**: RestrictIndexCustomization
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2024.6.0

O AEM Cloud Service proíbe modificações não autorizadas nos seguintes índices protos para uso:

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>Recomendamos que você resolva esse problema o mais rápido possível, pois ele poderá causar falhas nos pipelines a partir da [versão de agosto de 2024 do Cloud Manager](/help/release-notes/current.md).

### A configuração de tokenizadores nos analisadores deve utilizar o nome `tokenizer` {#oakpal-tokenizer}

* **Chave**: AnalyzerTokenizerConfigCheck
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2024.6.0

O AEM Cloud Service proíbe a criação de tokenizadores com nomes incorretos em analisadores. Os tokenizadores devem ser sempre definidos como `tokenizer`.

### A configuração das definições de indexação não deve conter espaços {#oakpal-indexing-definitions-spaces}

* **Chave**: PathSpacesCheck
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2024.7.0

O AEM Cloud Service proíbe a criação de definições de indexação que contenham propriedades com espaços.

### A configuração das definições de indexação não deve conter a propriedade haystack0 {#oakpal-indexing-haystack0-property}

* **Chave**: HayStackPropertyCheck
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2024.12.0

O AEM Cloud Service proíbe a criação de definições de indexação que contenham propriedades haystack.

### As definições de indexação não devem conter a propriedade: async-previous {#oakpal-indexing-unsupported-async-properties}

* **Chave**: IndexUnsupportedAsyncPropertiesCheck
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2025.3.0

O AEM Cloud Service proíbe a criação de definições de indexação com propriedades assíncronas não compatíveis.

### A configuração das definições de indexação não deve ter a mesma tag em vários índices {#oakpal-indexing-same-tag-multiple-indexes}

* **Chave**: SameTagInMultipleIndexes
* **Tipo**: melhoria
* **Severidade**: baixa
* **Desde**: versão 2025.3.0

O AEM Cloud Service proíbe a criação de definições de indexação que contenham a mesma tag em vários índices.

### A configuração das definições de indexação não deve conter substituição de modo para caminhos proibidos {#oakpal-xml-mode-analysis}

* **Chave**: FilterXmlModeAnalysis
* **Tipo**: melhoria
* **Severidade**: Alta
* **Desde**: versão 2025.4.0

O uso do modo &quot;substituição&quot; no file vault não é permitido para caminhos abaixo de /content; ele não deve ser usado para caminhos abaixo de /etc e /var.
O modo &quot;substituir&quot; substituirá todo o conteúdo já existente no repositório pelo fornecido no pacote de conteúdo, e os pacotes que acionam essa ação não devem fazer parte dos pacotes implantados pelo Cloud Manager.

## Ferramenta de otimização do Dispatcher {#dispatcher-optimization-tool-rules}

A seção a seguir lista as verificações da Ferramenta de Otimização do Dispatcher (DOT) executadas pelo Cloud Manager. Siga os links para cada verificação para obter sua definição e detalhes do GitHub.

* [Tokens inesperados da configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Aspas sem correspondência na configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Chave ausente na configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Chave extra na configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Propriedade obrigatória ausente na configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Propriedade obsoleta na configuração do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Configuração do Dispatcher não encontrada](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [A configuração httpd inclui um arquivo não encontrado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Configuração geral do Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [O cache da farm de publicação do Dispatcher deve estar com `serveStaleOnError` habilitado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Os filtros farm de publicação do Dispatcher devem conter as regras de negação padrão da versão 6.x.x do arquétipo do AEM](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [A propriedade `statfileslevel` do cache da farm de publicação do Dispatcher deve ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [A propriedade `gracePeriod` da farm de publicação do Dispatcher deve ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Cada farm do Dispatcher deve ter um nome exclusivo](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [O cache da farm de publicação do Dispatcher deve estar com as regras `ignoreUrlParams` configuradas de maneira semelhante a uma lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Os filtros farm de publicação do Dispatcher devem especificar os seletores Sling permitidos de maneira semelhante a uma lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Os filtros de farm de publicação do Dispatcher devem especificar os padrões de sufixo do Sling permitidos de maneira semelhante a uma lista de permissões](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [Não use a diretiva “Require all granted” em uma seção do VirtualHost Diretory com um caminho de diretório raiz](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
