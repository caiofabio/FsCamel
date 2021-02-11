# Camel

Neste repositório estarão disponíveis nosso *Workshop* de implementação fazendo uso da tecnologia [Apache Camel](https://camel.apache.org/)

## Pré Requisitos

- [JDK/Open JDK 11 (no mínimo)](https://openjdk.java.net/install/)
- [Apache Maven 3.6.x](https://maven.apache.org/download.cgi)
- [IntelliJ Community](https://www.jetbrains.com/idea/download/#section=mac)

## Workshop

0. [Spring Boot - Hello World](#workshop-springboot-helloworld)
1. [Quarkus - Hello World](#workshop-quarkus-helloworld)
2. [Spring Boot - File](#workshop-springboot-file)
3. [Quarkus - File](#workshop-quarkus-file)
4. [Spring Boot - ConvertBody](#workshop-springboot-convertbody)
5. [Quarkus - ConvertBody](#workshop-quarkus-convertbody)
6. [Spring Boot - Split](#workshop-springboot-split)
7. [Quarkus - Split](#workshop-quarkus-split)
8. [Spring Boot - Content Based Routing](#workshop-springboot-cbr)
9. [Quarkus - Content Based Routing](#workshop-quarkus-cbr)
10. [Spring Boot - Filter](#workshop-springboot-filter)
11. [Quarkus - Filter](#workshop-quarkus-filter)
12. [Spring Boot - Customer API](#workshop-springboot-customer-api)

## Implementação

### 0 - Spring Boot - Hello World <a name="workshop-springboot-helloworld">

* Acesse o [Spring Boot Initializer](https://start.spring.io/) e gere um projeto com as seguintes informações:

  ```
  Project: Maven
  Language: Java
  Spring Boot: 2.4.2
  Project Metadata
    Group: br.com.impacta.camel.springboot
    artifact: helloworld
    name: helloworld
    Package Name: br.com.impacta.camel.springboot.helloworld
    Packaging: jar
    Java: 11
  Dependencies:
    Apache Camel
  ```

* Importe o projeto no *IntelliJ* e verifique se o mesmo está sendo executado com sucesso através do comando *mvn spring-boot:run*:

  ```
  mvn spring-boot:run
  [INFO] Scanning for projects...
  [INFO]
  [INFO] -------------< br.com.impacta.camel.springboot:helloworld >-------------
  [INFO] Building helloworld 0.0.1-SNAPSHOT
  [INFO] --------------------------------[ jar ]---------------------------------
  [INFO]
  [INFO] >>> spring-boot-maven-plugin:2.4.2:run (default-cli) > test-compile @ helloworld >>>
  [INFO]
  [INFO] --- maven-resources-plugin:3.2.0:resources (default-resources) @ helloworld ---
  [INFO] Using 'UTF-8' encoding to copy filtered resources.
  [INFO] Using 'UTF-8' encoding to copy filtered properties files.
  [INFO] Copying 1 resource
  [INFO] Copying 0 resource
  [INFO]
  [INFO] --- maven-compiler-plugin:3.8.1:compile (default-compile) @ helloworld ---
  [INFO] Changes detected - recompiling the module!
  [INFO] Compiling 1 source file to /Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/springboot/helloworld/target/classes
  [INFO]
  [INFO] --- maven-resources-plugin:3.2.0:testResources (default-testResources) @ helloworld ---
  [INFO] Using 'UTF-8' encoding to copy filtered resources.
  [INFO] Using 'UTF-8' encoding to copy filtered properties files.
  [INFO] skip non existing resourceDirectory /Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/springboot/helloworld/src/test/resources
  [INFO]
  [INFO] --- maven-compiler-plugin:3.8.1:testCompile (default-testCompile) @ helloworld ---
  [INFO] Changes detected - recompiling the module!
  [INFO] Compiling 1 source file to /Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/springboot/helloworld/target/test-classes
  [INFO]
  [INFO] <<< spring-boot-maven-plugin:2.4.2:run (default-cli) < test-compile @ helloworld <<<
  [INFO]
  [INFO]
  [INFO] --- spring-boot-maven-plugin:2.4.2:run (default-cli) @ helloworld ---
  [INFO] Attaching agents: []
  OpenJDK 64-Bit Server VM warning: forcing TieredStopAtLevel to full optimization because JVMCI is enabled

    .   ____          _            __ _ _
   /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
  ( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
   \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
    '  |____| .__|_| |_|_| |_\__, | / / / /
   =========|_|==============|___/=/_/_/_/
   :: Spring Boot ::                (v2.4.2)

  2021-02-09 22:31:46.619  INFO 2670 --- [           main] b.c.i.c.s.h.HelloworldApplication        : Starting HelloworldApplication using Java 11.0.7 on marcfleury with PID 2670 (/Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/springboot/helloworld/target/classes started by vinny in /Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/springboot/helloworld)
  2021-02-09 22:31:46.621  INFO 2670 --- [           main] b.c.i.c.s.h.HelloworldApplication        : No active profile set, falling back to default profiles: default
  2021-02-09 22:31:47.356  INFO 2670 --- [           main] o.apache.camel.support.LRUCacheFactory   : Detected and using LRUCacheFactory: camel-caffeine-lrucache
  2021-02-09 22:31:47.615  INFO 2670 --- [           main] o.a.c.s.boot.SpringBootRoutesCollector   : Loading additional Camel XML routes from: classpath:camel/*.xml
  2021-02-09 22:31:47.616  INFO 2670 --- [           main] o.a.c.s.boot.SpringBootRoutesCollector   : Loading additional Camel XML route templates from: classpath:camel-template/*.xml
  2021-02-09 22:31:47.616  INFO 2670 --- [           main] o.a.c.s.boot.SpringBootRoutesCollector   : Loading additional Camel XML rests from: classpath:camel-rest/*.xml
  2021-02-09 22:31:47.662  INFO 2670 --- [           main] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) is starting
  2021-02-09 22:31:47.663  INFO 2670 --- [           main] o.a.c.impl.engine.AbstractCamelContext   : StreamCaching is not in use. If using streams then it's recommended to enable stream caching. See more details at http://camel.apache.org/stream-caching.html
  2021-02-09 22:31:47.673  INFO 2670 --- [           main] o.a.c.impl.engine.AbstractCamelContext   : Total 0 routes, of which 0 are started
  2021-02-09 22:31:47.673  INFO 2670 --- [           main] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) started in 11ms
  2021-02-09 22:31:47.683  INFO 2670 --- [           main] b.c.i.c.s.h.HelloworldApplication        : Started HelloworldApplication in 1.467 seconds (JVM running for 1.831)
  2021-02-09 22:31:47.694  WARN 2670 --- [extShutdownHook] o.a.c.s.boot.SpringBootCamelContext      : CamelContext has only been running for less than a second. If you intend to run Camel for a longer time then you can set the property camel.springboot.main-run-controller=true in application.properties or add spring-boot-starter-web JAR to the classpath.
  2021-02-09 22:31:47.694  INFO 2670 --- [extShutdownHook] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) is shutting down
  2021-02-09 22:31:47.703  INFO 2670 --- [extShutdownHook] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) uptime 41ms
  2021-02-09 22:31:47.703  INFO 2670 --- [extShutdownHook] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) is shutdown in 9ms
  [INFO] ------------------------------------------------------------------------
  [INFO] BUILD SUCCESS
  [INFO] ------------------------------------------------------------------------
  [INFO] Total time:  4.897 s
  [INFO] Finished at: 2021-02-09T22:31:47-03:00
  [INFO] ------------------------------------------------------------------------
  ```

* Crie a classe **HelloWorldRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.builder.RouteBuilder;
  import org.springframework.stereotype.Component;

  @Component
  public class HelloWorldRoute extends RouteBuilder {

      @Override
      public void configure() throws Exception {
          from("timer:example?period=1000")
              .log("Hello World");
      }

  }
  ```

* Altere o arquivo **application.properties** com o seguite conteúdo:

  ```
  camel.springboot.main-run-controller=true
  ```

* Execute a aplicação novamente através do comando *mvn spring-boot:run*:

  ```
  2021-02-09 22:39:25.093  INFO 2867 --- [           main] b.c.i.c.s.h.HelloworldApplication        : Starting HelloworldApplication using Java 11.0.7 on marcfleury with PID 2867 (/Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/springboot/helloworld/target/classes started by vinny in /Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/springboot/helloworld)
  2021-02-09 22:39:25.095  INFO 2867 --- [           main] b.c.i.c.s.h.HelloworldApplication        : No active profile set, falling back to default profiles: default
  2021-02-09 22:39:25.881  INFO 2867 --- [           main] o.apache.camel.support.LRUCacheFactory   : Detected and using LRUCacheFactory: camel-caffeine-lrucache
  2021-02-09 22:39:26.235  INFO 2867 --- [           main] o.a.c.s.boot.SpringBootRoutesCollector   : Loading additional Camel XML routes from: classpath:camel/*.xml
  2021-02-09 22:39:26.236  INFO 2867 --- [           main] o.a.c.s.boot.SpringBootRoutesCollector   : Loading additional Camel XML route templates from: classpath:camel-template/*.xml
  2021-02-09 22:39:26.236  INFO 2867 --- [           main] o.a.c.s.boot.SpringBootRoutesCollector   : Loading additional Camel XML rests from: classpath:camel-rest/*.xml
  2021-02-09 22:39:26.355  INFO 2867 --- [           main] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) is starting
  2021-02-09 22:39:26.357  INFO 2867 --- [           main] o.a.c.impl.engine.AbstractCamelContext   : StreamCaching is not in use. If using streams then it's recommended to enable stream caching. See more details at http://camel.apache.org/stream-caching.html
  2021-02-09 22:39:26.358  INFO 2867 --- [           main] c.s.b.CamelSpringBootApplicationListener : Starting CamelMainRunController to ensure the main thread keeps running
  2021-02-09 22:39:26.369  INFO 2867 --- [           main] o.a.c.i.e.InternalRouteStartupManager    : Route: route1 started and consuming from: timer://example
  2021-02-09 22:39:26.378  INFO 2867 --- [           main] o.a.c.impl.engine.AbstractCamelContext   : Total 1 routes, of which 1 are started
  2021-02-09 22:39:26.379  INFO 2867 --- [           main] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) started in 24ms
  2021-02-09 22:39:26.387  INFO 2867 --- [           main] b.c.i.c.s.h.HelloworldApplication        : Started HelloworldApplication in 1.703 seconds (JVM running for 2.117)
  2021-02-09 22:39:27.379  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:28.373  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:29.372  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:30.373  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:31.373  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:32.373  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:33.374  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:34.374  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:35.374  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:36.374  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:37.374  INFO 2867 --- [timer://example] route1                                   : Hello World
  2021-02-09 22:39:38.375  INFO 2867 --- [timer://example] route1                                   : Hello World
  ^C2021-02-09 22:39:38.641  INFO 2867 --- [extShutdownHook] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) is shutting down
  2021-02-09 22:39:38.642  INFO 2867 --- [extShutdownHook] o.a.c.i.engine.DefaultShutdownStrategy   : Starting to graceful shutdown 1 routes (timeout 45 seconds)
  2021-02-09 22:39:38.648  INFO 2867 --- [ - ShutdownTask] o.a.c.i.engine.DefaultShutdownStrategy   : Route: route1 shutdown complete, was consuming from: timer://example
  2021-02-09 22:39:38.648  INFO 2867 --- [extShutdownHook] o.a.c.i.engine.DefaultShutdownStrategy   : Graceful shutdown of 1 routes completed in 7ms
  2021-02-09 22:39:38.654  INFO 2867 --- [extShutdownHook] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) uptime 12s299ms
  2021-02-09 22:39:38.654  INFO 2867 --- [extShutdownHook] o.a.c.impl.engine.AbstractCamelContext   : Apache Camel 3.7.2 (camel-1) is shutdown in 13ms
  ```

### 1 - Quarkus - Hello World <a name="workshop-quarkus-helloworld">

* Acesse o [Quarkus Initializer](https://code.quarkus.io/) e gere um projeto com as seguintes informações:

  ```
  Group: br.com.impacta.camel.quarkus
  artifact: helloworld
  name: helloworld
  Extensions
  Camel Core
  Camel Endpoint DSL
  Camel Component DSL
  Camel Timer
  ```

* Importe o projeto no *IntelliJ* e verifique se o mesmo está sendo executado com sucesso através do comando *mvn quarkus:dev*:

  ```
  [INFO] Scanning for projects...
  [INFO]
  [INFO] --------------< br.com.impacta.camel.quarkus:helloworld >---------------
  [INFO] Building helloworld 1.0.0-SNAPSHOT
  [INFO] --------------------------------[ jar ]---------------------------------
  [INFO]
  [INFO] --- quarkus-maven-plugin:1.11.2.Final:dev (default-cli) @ helloworld ---
  [INFO] Using 'UTF-8' encoding to copy filtered resources.
  [INFO] Copying 2 resources
  [INFO] Changes detected - recompiling the module!
  [INFO] Compiling 1 source file to /Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/quarkus/helloworld/target/classes
  OpenJDK 64-Bit Server VM warning: forcing TieredStopAtLevel to full optimization because JVMCI is enabled
  Listening for transport dt_socket at address: 5005
  __  ____  __  _____   ___  __ ____  ______
   --/ __ \/ / / / _ | / _ \/ //_/ / / / __/
   -/ /_/ / /_/ / __ |/ , _/ ,< / /_/ /\ \
  --\___\_\____/_/ |_/_/|_/_/|_|\____/___/
  2021-02-09 23:12:18,146 INFO  [org.apa.cam.qua.cor.CamelBootstrapRecorder] (Quarkus Main Thread) bootstrap runtime: org.apache.camel.quarkus.core.CamelContextRuntime
  2021-02-09 23:12:18,189 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (Quarkus Main Thread) Apache Camel 3.7.0 (camel-1) is starting
  2021-02-09 23:12:18,190 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (Quarkus Main Thread) StreamCaching is not in use. If using streams then it's recommended to enable stream caching. See more details at http://camel.apache.org/stream-caching.html
  2021-02-09 23:12:18,192 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (Quarkus Main Thread) Total 0 routes, of which 0 are started
  2021-02-09 23:12:18,192 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (Quarkus Main Thread) Apache Camel 3.7.0 (camel-1) started in 3ms
  2021-02-09 23:12:18,318 INFO  [io.quarkus] (Quarkus Main Thread) helloworld 1.0.0-SNAPSHOT on JVM (powered by Quarkus 1.11.2.Final) started in 2.399s. Listening on: http://localhost:8080
  2021-02-09 23:12:18,318 INFO  [io.quarkus] (Quarkus Main Thread) Profile dev activated. Live Coding activated.
  2021-02-09 23:12:18,318 INFO  [io.quarkus] (Quarkus Main Thread) Installed features: [camel-core, camel-endpointdsl, camel-support-common, camel-timer, cdi, resteasy]
  ```

* Crie a classe **HelloWorldRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.quarkus;

  import org.apache.camel.builder.RouteBuilder;

  public class HelloWorldRoute extends RouteBuilder {

      @Override
      public void configure() throws Exception {
          from("timer:example?period=1000")
              .log("Hello World");
      }
  }
  ```

* Execute a aplicação novamente através do comando *mvn quarkus:dev*

  ```
  [INFO] Scanning for projects...
  [INFO]
  [INFO] --------------< br.com.impacta.camel.quarkus:helloworld >---------------
  [INFO] Building helloworld 1.0.0-SNAPSHOT
  [INFO] --------------------------------[ jar ]---------------------------------
  [INFO]
  [INFO] --- quarkus-maven-plugin:1.11.2.Final:dev (default-cli) @ helloworld ---
  [INFO] Using 'UTF-8' encoding to copy filtered resources.
  [INFO] Copying 2 resources
  [INFO] Changes detected - recompiling the module!
  [INFO] Compiling 2 source files to /Users/vinny/Documents/IMPACTA/2021/FullStack/ApiGatewayIntegracao/FsCamel/source/quarkus/helloworld/target/classes
  OpenJDK 64-Bit Server VM warning: forcing TieredStopAtLevel to full optimization because JVMCI is enabled
  Listening for transport dt_socket at address: 5005
  __  ____  __  _____   ___  __ ____  ______
   --/ __ \/ / / / _ | / _ \/ //_/ / / / __/
   -/ /_/ / /_/ / __ |/ , _/ ,< / /_/ /\ \
  --\___\_\____/_/ |_/_/|_/_/|_|\____/___/
  2021-02-09 23:30:58,214 INFO  [org.apa.cam.qua.cor.CamelBootstrapRecorder] (Quarkus Main Thread) bootstrap runtime: org.apache.camel.quarkus.core.CamelContextRuntime
  2021-02-09 23:30:58,293 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (Quarkus Main Thread) Apache Camel 3.7.0 (camel-1) is starting
  2021-02-09 23:30:58,295 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (Quarkus Main Thread) StreamCaching is not in use. If using streams then it's recommended to enable stream caching. See more details at http://camel.apache.org/stream-caching.html
  2021-02-09 23:30:58,300 INFO  [org.apa.cam.imp.eng.InternalRouteStartupManager] (Quarkus Main Thread) Route: route1 started and consuming from: timer://example
  2021-02-09 23:30:58,302 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (Quarkus Main Thread) Total 1 routes, of which 1 are started
  2021-02-09 23:30:58,302 INFO  [org.apa.cam.imp.eng.AbstractCamelContext] (Quarkus Main Thread) Apache Camel 3.7.0 (camel-1) started in 9ms
  2021-02-09 23:30:58,537 INFO  [io.quarkus] (Quarkus Main Thread) helloworld 1.0.0-SNAPSHOT on JVM (powered by Quarkus 1.11.2.Final) started in 2.505s. Listening on: http://localhost:8080
  2021-02-09 23:30:58,538 INFO  [io.quarkus] (Quarkus Main Thread) Profile dev activated. Live Coding activated.
  2021-02-09 23:30:58,538 INFO  [io.quarkus] (Quarkus Main Thread) Installed features: [camel-core, camel-endpointdsl, camel-support-common, camel-timer, cdi, resteasy]
  2021-02-09 23:30:59,310 INFO  [route1] (Camel (camel-1) thread #0 - timer://example) Hello World
  ```

### 2 - Spring - File <a name="workshop-springboot-file">

* Crie a classe **FileRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.builder.RouteBuilder;
  import org.springframework.stereotype.Component;

  @Component
  public class FileRoute extends RouteBuilder {

      @Override
      public void configure() throws Exception {
          from("file:/tmp/input")
              .log("FileName: ${in.header.CamelFileName} Content: ${body}")
              .to("file:/tmp/output");
      }
  }
  ```

* Execute o projeto através do comando: `mvn spring-boot:run`

* Crie um arquivo no diretório */tpm/input* e perceba que o mesmo é movido para o diretório */tmp/output*:

  ```
  touch /tmp/input/test1.txt
  touch /tmp/input/test2.txt
  ls /tmp/output
  -rw-r--r--   1 vinny  wheel     0B Feb  9 23:35 test1.txt
  -rw-r--r--   1 vinny  wheel     0B Feb  9 23:35 test2.txt
  ```

* Altere o método **Configure** da classe **FileRoute** com o seguinte conteúdo:

  ```
  @Override
  public void configure() throws Exception {
      from("file:/tmp/input")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .to("file:/tmp/output?fileName=${date:now:yyyyMMddhhmmss}.txt.done");
  }
  ```

* Crie um arquivo no diretório */tpm/input* e perceba que o mesmo é movido para o diretório */tmp/output* porém com nome no formato *yyyyMMddhhmmss* e com a extensão *.done*:

  ```
  ls /tmp/output
  20210209114424.txt.done
  ```

### 3 - Quarkus - File <a name="workshop-quarkus-file">

* Altere o arquivo *pom.xml* do projeto adicionando a seguinte extensão:

  ```
  <dependency>
    <groupId>org.apache.camel.quarkus</groupId>
    <artifactId>camel-quarkus-file</artifactId>
  </dependency>
  ```

* Crie a classe **FileRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.builder.RouteBuilder;
  import org.springframework.stereotype.Component;

  @Component
  public class FileRoute extends RouteBuilder {

      @Override
      public void configure() throws Exception {
          from("file:/tmp/input-quarkus")
              .log("FileName: ${in.header.CamelFileName} Content: ${body}")
              .to("file:/tmp/output-quarkus");
      }
  }
  ```

* Execute o projeto através do comando: `mvn quarkus:dev`

* Crie um arquivo no diretório */tpm/input-quarkus* e perceba que o mesmo é movido para o diretório */tmp/output-quarkus*:

* Altere o método **Configure** da classe **FileRoute** com o seguinte conteúdo:

  ```
  @Override
  public void configure() throws Exception {
      from("file:/tmp/input-quarkus")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .to("file:/tmp/output-quarkus?fileName=${date:now:yyyyMMddhhmmss}.txt.done");
  }
  ```

* Crie um arquivo no diretório */tpm/input-quarkus* e perceba que o mesmo é movido para o diretório */tmp/output-quarkus* porém com nome no formato *yyyyMMddhhmmss* e com a extensão *.done*:

  ```
  ls /tmp/output
  20210209114424.txt.done
  ```

### 4 - Spring - ConvertBody <a name="workshop-springboot-convertbody">

* Altere o método **Configure** da classe **FileRoute** com o seguinte conteúdo:

  ```
  @Override
  public void configure() throws Exception {
      from("file:/tmp/input")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .convertBodyTo(java.lang.String.class)
          .bean(UpperBean.class, "upperCase")
          .to("file:/tmp/output?fileName=${date:now:yyyyMMddhhmmss}.txt.done");
  }
  ```

* Crie a classe **UpperBean** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.Exchange;
  import org.springframework.stereotype.Component;

  @Component
  public class UpperBean {

      public void upperCase(Exchange exchange) {
          String messageBody = (String)exchange.getIn().getBody();
          if (messageBody != null && !messageBody.isEmpty()) {
              System.out.println("Current MessageBody content BEFORE Transformation: " + messageBody);
              exchange.getIn().setBody(messageBody.toUpperCase());
              System.out.println("Current MessageBody content AFTER Transformation: " + (String)exchange.getIn().getBody());
          }
      }
  }
  ```

* Crie um arquivo no diretório */tpm/input* com o seguinte conteúdo: `echo "this is my lower case message" > /tmp/input/lower.txt`

* Verifique que no diretório */tmp/output* o arquivo está presente e o conteúdo do mesmo está em LETRA MAIÚSCULA:

  ```
  cat /tmp/output/20210210121317.txt.done
  THIS IS MY LOWER CASE MESSAGE
  ```

### 5 - Quarkus - ConvertBody <a name="workshop-quarkus-convertbody">

* Altere o arquivo *pom.xml* do projeto adicionando a seguinte extensão:

  ```
  <dependency>
    <groupId>org.apache.camel.quarkus</groupId>
    <artifactId>camel-quarkus-bean</artifactId>
  </dependency>
  ```

* Altere o método **Configure** da classe **FileRoute** com o seguinte conteúdo:

  ```
  @Override
  public void configure() throws Exception {
      from("file:/tmp/input-quarkus")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .convertBodyTo(java.lang.String.class)
          .bean(UpperBean.class, "upperCase")
          .to("file:/tmp/output-quarkus?fileName=${date:now:yyyyMMddhhmmss}.txt.done");
  }
  ```

* Crie a classe **UpperBean** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.quarkus;

  import org.apache.camel.Exchange;

  import javax.enterprise.context.ApplicationScoped;

  @ApplicationScoped
  public class UpperBean {

      public void upperCase(Exchange exchange) {
          String messageBody = (String)exchange.getIn().getBody();
          if (messageBody != null && !messageBody.isEmpty()) {
              System.out.println("Current MessageBody content BEFORE Transformation: " + messageBody);
              exchange.getIn().setBody(messageBody.toUpperCase());
              System.out.println("Current MessageBody content AFTER Transformation: " + (String)exchange.getIn().getBody());
          }
      }
  }
  ```

* Crie um arquivo no diretório */tpm/input-quarkus* com o seguinte conteúdo: `echo "this is my lower case message" > /tmp/input-quarkus/lower.txt`

* Verifique que no diretório */tmp/output-quarkus* o arquivo está presente e o conteúdo do mesmo está em LETRA MAIÚSCULA:

  ```
  cat /tmp/output-quarkus/20210210121317.txt.done
  THIS IS MY LOWER CASE MESSAGE
  ```

### 6 - Spring - Split <a name="workshop-springboot-split">

* Altere o arquivo *pom.xml* do projeto adicionando a seguinte extensão:
  ```
  <dependency>
    <groupId>org.apache.camel.springboot</groupId>
    <artifactId>camel-bindy-starter</artifactId>
    <version>3.7.2</version>
  </dependency>
  ```

* Crie a classe **Customer** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.dataformat.bindy.annotation.CsvRecord;
  import org.apache.camel.dataformat.bindy.annotation.DataField;

  @CsvRecord(separator = ",")
  public class Customer {

      @DataField(pos = 1)
      private long customerId;
      @DataField(pos = 2)
      private String firstName;
      @DataField(pos = 3)
      private String lastName;

      @Override
      public String toString() {
          return "Customer [customerId=" + customerId + ", firstName=" + firstName + ", lastName=" + lastName + "]";
      }

      @Override
      public int hashCode() {
          final int prime = 31;
          int result = 1;
          result = prime * result + (int) (customerId ^ (customerId >>> 32));
          return result;
      }
      @Override
      public boolean equals(Object obj) {
          if (this == obj)
              return true;
          if (obj == null)
              return false;
          if (getClass() != obj.getClass())
              return false;
          Customer other = (Customer) obj;
          if (customerId != other.customerId)
              return false;
          return true;
      }

      public long getCustomerId() {
          return customerId;
      }
      public void setCustomerId(long customerId) {
          this.customerId = customerId;
      }
      public String getFirstName() {
          return firstName;
      }
      public void setFirstName(String firstName) {
          this.firstName = firstName;
      }
      public String getLastName() {
          return lastName;
      }
      public void setLastName(String lastName) {
          this.lastName = lastName;
      }

  }
  ```

* Crie a classe **CustomerBean** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.Exchange;
  import org.springframework.stereotype.Component;

  import java.util.List;

  @Component
  public class CustomerBean {

      public void printClass(Exchange exchange) {
          List<Customer> customerList = (List<Customer>)exchange.getIn().getBody(List.class);
          customerList.stream().forEach(customer ->
                  System.out.println(
                      " Customer ID: " + customer.getCustomerId() +
                      " Customer First Name: " + customer.getFirstName() +
                      " Customer Last Name: " + customer.getLastName()
                  )
          );
      }
  }
  ```

* Altere o método **Configure** da classe **FileRoute** com o seguinte conteúdo:

  ```
  @Override
  public void configure() throws Exception {
      BindyCsvDataFormat csvDataFormat = new BindyCsvDataFormat(Customer.class);

      from("file:/tmp/input")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .split(body().tokenize("/n")).unmarshal(csvDataFormat)
          .log("Reading File Line >> ${body}")
          .convertBodyTo(Customer[].class)
          .bean(CustomerBean.class, "printClass");
  }
  ```

* Crie um arquivo (e.g players.txt) com o conteúdo abaixo e mova o mesmo para o diretório */tmp/input*:

  ```
  1,Kobe,Bryant
  2,Michael,Jordan
  3,Vinicius,Martinez
  ```

### 7 - Quarkus - Split <a name="workshop-quarkus-convertbody">

* Altere o arquivo *pom.xml* do projeto adicionando a seguinte extensão:
  ```
  <dependency>
    <groupId>org.apache.camel.quarkus</groupId>
    <artifactId>camel-quarkus-bindy</artifactId>
  </dependency>
  ```

* Crie a classe **Customer** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.quarkus.helloworld;

  import org.apache.camel.dataformat.bindy.annotation.CsvRecord;
  import org.apache.camel.dataformat.bindy.annotation.DataField;

  @CsvRecord(separator = ",")
  public class Customer {

      @DataField(pos = 1)
      private long customerId;
      @DataField(pos = 2)
      private String firstName;
      @DataField(pos = 3)
      private String lastName;

      @Override
      public String toString() {
          return "Customer [customerId=" + customerId + ", firstName=" + firstName + ", lastName=" + lastName + "]";
      }

      @Override
      public int hashCode() {
          final int prime = 31;
          int result = 1;
          result = prime * result + (int) (customerId ^ (customerId >>> 32));
          return result;
      }
      @Override
      public boolean equals(Object obj) {
          if (this == obj)
              return true;
          if (obj == null)
              return false;
          if (getClass() != obj.getClass())
              return false;
          Customer other = (Customer) obj;
          if (customerId != other.customerId)
              return false;
          return true;
      }

      public long getCustomerId() {
          return customerId;
      }
      public void setCustomerId(long customerId) {
          this.customerId = customerId;
      }
      public String getFirstName() {
          return firstName;
      }
      public void setFirstName(String firstName) {
          this.firstName = firstName;
      }
      public String getLastName() {
          return lastName;
      }
      public void setLastName(String lastName) {
          this.lastName = lastName;
      }

  }
  ```

* Crie a classe **CustomerBean** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.quarkus.helloworld;

  import org.apache.camel.Exchange;

  import java.util.List;

  public class CustomerBean {

      public void printClass(Exchange exchange) {
          List<Customer> customerList = (List<Customer>)exchange.getIn().getBody(List.class);
          customerList.stream().forEach(customer ->
                  System.out.println(
                      " Customer ID: " + customer.getCustomerId() +
                      " Customer First Name: " + customer.getFirstName() +
                      " Customer Last Name: " + customer.getLastName()
                  )
          );
      }
  }
  ```

* Altere o método **Configure** da classe **FileRoute** com o seguinte conteúdo:

  ```
  @Override
  public void configure() throws Exception {
      BindyCsvDataFormat csvDataFormat = new BindyCsvDataFormat(Customer.class);

      from("file:/tmp/input-quarkus")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .split(body().tokenize("/n")).unmarshal(csvDataFormat)
          .log("Reading File Line >> ${body}")
          .convertBodyTo(Customer[].class)
          .bean(CustomerBean.class, "printClass");
  }
  ```

* Crie um arquivo (e.g players.txt) com o conteúdo abaixo e mova o mesmo para o diretório */tmp/input*:

  ```
  1,Kobe,Bryant
  2,Michael,Jordan
  3,Vinicius,Martinez
  ```

### 8 - Spring - Content Based Routing <a name="workshop-springboot-cbr">

* Crie uma classe **CBRRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.builder.RouteBuilder;
  import org.springframework.stereotype.Component;

  @Component
  public class CBRRoute extends RouteBuilder {
      @Override
      public void configure() throws Exception {
          from("file:/tmp/input/pedidos")
              .choice()
                  .when(xpath("/Order/Country='USA'"))
                      .log("Pedido USA Found")
                      .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                      .to("file:/tmp/output/pedidos/usa")
                  .when(xpath("/Order/Country='UK'"))
                      .log("Pedido UK Found")
                      .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                      .to("file:/tmp/output/pedidos/uk")
                  .otherwise()
                      .log("Pedido Default")
                      .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                      .to("file:/tmp/output/pedidos/default")
              .end();
      }
  }
  ```

* Crie três arquivos no diretório *src/main/resources/pedidos* com o seguinte conteúdo:

  ```
  -- arquivo 1
  <Order>
      <Number>22222</Number>
      <Country>UK</Country>
      <Amount>22222</Amount>
      <Items>
          <ItemID>22222</ItemID>
          <ItemCost>22.00</ItemCost>
      </Items>
  </Order>

  -- arquivo 2
  <Order>
      <Number>123456</Number>
      <Country>USA</Country>
      <Amount>676332</Amount>
      <Items>
          <ItemID>12345</ItemID>
          <ItemCost>44.00</ItemCost>
          <ItemQty>1</ItemQty>
      </Items>
  </Order>

  -- arquivo 3
  <Order>
      <Number>3333</Number>
      <Country>BRASIL</Country>
      <Amount>3333</Amount>
      <Items>
          <ItemID>3333</ItemID>
          <ItemQty>3</ItemQty>
      </Items>
  </Order>
  ```

* Copie os arquivos presentes no diretório **resources/pedidos** para o diretório **/tmp/input/pedidos**: `cp source/springboot/helloworld/src/main/resources/pedidos/pedido* /tmp/input/pedidos`


* Verifique que os arquivos foram processados e direcionados para o diretório adequado:
  ```
  2021-02-10 10:10:01.843  INFO 12662 --- [           main] b.c.i.c.s.h.HelloworldApplication        : Started HelloworldApplication in 1.807 seconds (JVM running for 2.39)
  2021-02-10 10:10:02.841  INFO 12662 --- [timer://example] route3                                   : Hello World
  2021-02-10 10:10:29.941  INFO 12662 --- [p/input/pedidos] route1                                   : Pedido UK Found
  2021-02-10 10:10:29.942  INFO 12662 --- [p/input/pedidos] route1                                   : FileName: pedido-uk.xml Content: <Order>
      <Number>22222</Number>
      <Country>UK</Country>
      <Amount>22222</Amount>
      <Items>
          <ItemID>22222</ItemID>
          <ItemCost>22.00</ItemCost>
      </Items>
  </Order>
  2021-02-10 10:10:29.953  INFO 12662 --- [p/input/pedidos] route1                                   : Pedido USA Found
  2021-02-10 10:10:29.953  INFO 12662 --- [p/input/pedidos] route1                                   : FileName: pedido-usa.xml Content: <Order>
      <Number>123456</Number>
      <Country>USA</Country>
      <Amount>676332</Amount>
      <Items>
          <ItemID>12345</ItemID>
          <ItemCost>44.00</ItemCost>
          <ItemQty>1</ItemQty>
      </Items>
  </Order>
  2021-02-10 10:10:29.959  INFO 12662 --- [p/input/pedidos] route1                                   : Pedido Default
  2021-02-10 10:10:29.959  INFO 12662 --- [p/input/pedidos] route1                                   : FileName: pedido.xml Content: <Order>
      <Number>3333</Number>
      <Country>BRASIL</Country>
      <Amount>3333</Amount>
      <Items>
          <ItemID>3333</ItemID>
          <ItemQty>3</ItemQty>
      </Items>
  </Order>

  tree /tmp/output/pedidos
  /tmp/output/pedidos
  ├── default
  │   └── pedido.xml
  ├── uk
  │   └── pedido-uk.xml
  └── usa
      └── pedido-usa.xml

  3 directories, 3 files
  ```

* Altere **CBRRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.builder.RouteBuilder;

  public class CBRRoute extends RouteBuilder {
      @Override
      public void configure() throws Exception {
          from("file:/tmp/input/pedidos")
              .choice()
                .when(xpath("/Order/Country='USA'"))
                  .log("Pedido USA Found")
                  .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                  .to("rabbitmq://localhost:5672/quarkus-orders-us.exchange?queue=quarkus-orders-us")
              .when(xpath("/Order/Country='UK'"))
                  .log("Pedido UK Found")
                  .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                  .to("rabbitmq://localhost:5672/quarkus-orders-uk.exchange?queue=quarkus-orders-uk")
              .otherwise()
                  .log("Pedido Default")
                  .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                  .to("rabbitmq://localhost:5672/quarkus-orders.exchange?queue=quarkus-orders")
              .end();
      }
  }
  ```

* Altere o **pom.xml** adicionando a dependência do RabbitMQ:

  ```
  <dependency>
  	<groupId>org.apache.camel.springboot</groupId>
  	<artifactId>camel-rabbitmq-starter</artifactId>
  	<version>3.7.2</version>
	</dependency>
  ```

* Inicie o serviço de mensageria: `docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management`

* Repita o processo anterior de envio de mensagens: `cp source/springboot/helloworld/src/main/resources/pedidos/pedido* /tmp/input/pedidos`

* Acesse a interface do *RabbitMQ* e valide o envio de mensagens:

  ```
  http://localhost:15672/#/queues
  guest guest
  ```

### 9 - Quarkus - Content Based Routing <a name="workshop-quarkus-cbr">

* Adicione a seguinte dependência no arquivo **pom.xml**:

  ```
  <dependency>
    <groupId>org.apache.camel.quarkus</groupId>
    <artifactId>camel-quarkus-xpath</artifactId>
  </dependency>
  ```

* Crie uma classe **CBRRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.quarkus.helloworld;

  import org.apache.camel.builder.RouteBuilder;

  public class CBRRoute extends RouteBuilder {
      @Override
      public void configure() throws Exception {
          from("file:/tmp/input/pedidos")
              .choice()
                  .when(xpath("/Order/Country='USA'"))
                      .log("Pedido USA Found")
                      .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                      .to("file:/tmp/output/pedidos/usa")
                  .when(xpath("/Order/Country='UK'"))
                      .log("Pedido UK Found")
                      .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                      .to("file:/tmp/output/pedidos/uk")
                  .otherwise()
                      .log("Pedido Default")
                      .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                      .to("file:/tmp/output/pedidos/default")
              .end();
      }
  }
  ```

* Crie três arquivos no diretório *src/main/resources/pedidos* com o seguinte conteúdo:

  ```
  -- arquivo 1
  <Order>
      <Number>22222</Number>
      <Country>UK</Country>
      <Amount>22222</Amount>
      <Items>
          <ItemID>22222</ItemID>
          <ItemCost>22.00</ItemCost>
      </Items>
  </Order>

  -- arquivo 2
  <Order>
      <Number>123456</Number>
      <Country>USA</Country>
      <Amount>676332</Amount>
      <Items>
          <ItemID>12345</ItemID>
          <ItemCost>44.00</ItemCost>
          <ItemQty>1</ItemQty>
      </Items>
  </Order>

  -- arquivo 3
  <Order>
      <Number>3333</Number>
      <Country>BRASIL</Country>
      <Amount>3333</Amount>
      <Items>
          <ItemID>3333</ItemID>
          <ItemQty>3</ItemQty>
      </Items>
  </Order>
  ```

* Copie os arquivos presentes no diretório **resources/pedidos** para o diretório **/tmp/input/pedidos**: `cp source/quarkus/helloworld/src/main/resources/pedidos/pedido* /tmp/input-quarkus/pedidos`


* Verifique que os arquivos foram processados e direcionados para o diretório adequado:

  ```
  2021-02-10 10:39:19,167 INFO  [route2] (Camel (camel-1) thread #0 - file:///tmp/input-quarkus/pedidos) Pedido UK Found
  2021-02-10 10:39:19,168 INFO  [route2] (Camel (camel-1) thread #0 - file:///tmp/input-quarkus/pedidos) FileName: pedido-uk.xml Content: <Order>
      <Number>22222</Number>
      <Country>UK</Country>
      <Amount>22222</Amount>
      <Items>
          <ItemID>22222</ItemID>
          <ItemCost>22.00</ItemCost>
      </Items>
  </Order>
  2021-02-10 10:39:19,179 INFO  [route2] (Camel (camel-1) thread #0 - file:///tmp/input-quarkus/pedidos) Pedido USA Found
  2021-02-10 10:39:19,179 INFO  [route2] (Camel (camel-1) thread #0 - file:///tmp/input-quarkus/pedidos) FileName: pedido-usa.xml Content: <Order>
      <Number>123456</Number>
      <Country>USA</Country>
      <Amount>676332</Amount>
      <Items>
          <ItemID>12345</ItemID>
          <ItemCost>44.00</ItemCost>
          <ItemQty>1</ItemQty>
      </Items>
  </Order>
  2021-02-10 10:39:19,187 INFO  [route2] (Camel (camel-1) thread #0 - file:///tmp/input-quarkus/pedidos) Pedido Default
  2021-02-10 10:39:19,187 INFO  [route2] (Camel (camel-1) thread #0 - file:///tmp/input-quarkus/pedidos) FileName: pedido.xml Content: <Order>
      <Number>3333</Number>
      <Country>BRASIL</Country>
      <Amount>3333</Amount>
      <Items>
          <ItemID>3333</ItemID>
          <ItemQty>3</ItemQty>
      </Items>
  </Order>

  tree /tmp/output-quarkus/pedidos
  /tmp/output/pedidos
  ├── default
  │   └── pedido.xml
  ├── uk
  │   └── pedido-uk.xml
  └── usa
      └── pedido-usa.xml

  3 directories, 3 files
  ```

* Altere **CBRRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.camel.helloworld;

  import org.apache.camel.builder.RouteBuilder;

  public class CBRRoute extends RouteBuilder {
      @Override
      public void configure() throws Exception {
          from("file:/tmp/input/pedidos")
              .choice()
                .when(xpath("/Order/Country='USA'"))
                  .log("Pedido USA Found")
                  .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                  .to("rabbitmq://localhost:5672/quarkus-orders-us.exchange?queue=quarkus-orders-us")
              .when(xpath("/Order/Country='UK'"))
                  .log("Pedido UK Found")
                  .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                  .to("rabbitmq://localhost:5672/quarkus-orders-uk.exchange?queue=quarkus-orders-uk")
              .otherwise()
                  .log("Pedido Default")
                  .log("FileName: ${in.header.CamelFileName} Content: ${body}")
                  .to("rabbitmq://localhost:5672/quarkus-orders.exchange?queue=quarkus-orders")
              .end();
      }
  }
  ```

* Altere o **pom.xml** adicionando a dependência do RabbitMQ:

  ```
  <dependency>
    <groupId>org.apache.camel.quarkus</groupId>
    <artifactId>camel-quarkus-rabbitmq</artifactId>
  </dependency>
  ```

* Inicie o serviço de mensageria: `docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management`

* Repita o processo anterior de envio de mensagens: `cp source/quarkus/helloworld/src/main/resources/pedidos/pedido* /tmp/input-quarkus/pedidos`

* Acesse a interface do *RabbitMQ* e valide o envio de mensagens:

  ```
  http://localhost:15672/#/queues
  guest
  ```

### 10 - Spring Boot - Filter <a name="workshop-springboot-filter">

* Altere o método **Configure** adicionando o seguinte conteúdo:

  ```
  from("file:/tmp/input/pedidos")
    .choice()
        .when(xpath("/Order/Country='USA'"))
          .log("Pedido USA Found")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .to("rabbitmq://localhost:5672/spring-orders-us.exchange?queue=spring-orders-us")
        .when(xpath("/Order/Country='UK'"))
          .log("Pedido UK Found")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .to("rabbitmq://localhost:5672/spring-orders-uk.exchange?queue=spring-orders-uk")
        .otherwise()
          .log("Pedido Default")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .filter().xpath("/Order/Amount>10000")
          .log("FileName: ${in.header.CamelFileName} Content: ${body} will be Dispatched to RabbitMQ")
          .to("rabbitmq://localhost:5672/spring-orders.exchange?queue=spring-orders")
    .end();
  ```

* Inicie o serviço de mensageria: `docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management`

* Repita o processo anterior de envio de mensagens: `cp source/springboot/helloworld/src/main/resources/pedidos/pedido* /tmp/input/pedidos`

* Acesse a interface do *RabbitMQ* e valide o envio de mensagens:

  ```
  http://localhost:15672/#/queues
  guest
  ```

### 11 - Quarkus - Filter <a name="workshop-quarkus-filter">

* Altere o método **Configure** adicionando o seguinte conteúdo:

  ```
  from("file:/tmp/input/pedidos")
    .choice()
        .when(xpath("/Order/Country='USA'"))
          .log("Pedido USA Found")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .to("rabbitmq://localhost:5672/spring-orders-us.exchange?queue=spring-orders-us")
        .when(xpath("/Order/Country='UK'"))
          .log("Pedido UK Found")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .to("rabbitmq://localhost:5672/spring-orders-uk.exchange?queue=spring-orders-uk")
        .otherwise()
          .log("Pedido Default")
          .log("FileName: ${in.header.CamelFileName} Content: ${body}")
          .filter().xpath("/Order/Amount>10000")
          .log("FileName: ${in.header.CamelFileName} Content: ${body} will be Dispatched to RabbitMQ")
          .to("rabbitmq://localhost:5672/spring-orders.exchange?queue=spring-orders")
    .end();
  ```

* Inicie o serviço de mensageria: `docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management`

* Repita o processo anterior de envio de mensagens: `cp source/quarkus/helloworld/src/main/resources/pedidos/pedido* /tmp/input-quarkus/pedidos`

* Acesse a interface do *RabbitMQ* e valide o envio de mensagens:

  ```
  http://localhost:15672/#/queues
  guest
  ```

### 12 - Spring Boot - Customer API <a name="workshop-springboot-customer-api">

* Incluir as seguintes dependências no **pom.xml**:

  ```
  <dependency>
  	<groupId>org.apache.camel.springboot</groupId>
  	<artifactId>camel-rest-starter</artifactId>
  	<version>3.7.2</version>
  </dependency>
  <dependency>
  	<groupId>org.apache.camel.springboot</groupId>
  	<artifactId>camel-undertow-starter</artifactId>
  	<version>3.7.2</version>
  </dependency>
  <dependency>
  	<groupId>org.apache.camel.springboot</groupId>
  	<artifactId>camel-jackson-starter</artifactId>
  	<version>3.7.2</version>
  </dependency>
  ```

* Criar a classe **CustomerService** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.springframework.stereotype.Component;

  import java.util.HashSet;
  import java.util.Set;

  @Component
  public class CustomerService {

      private static Set<Customer> customerSet = new HashSet<Customer>(0);

      public Customer addCustomer(Customer customer){
          if (customerSet.contains(customer)){
              for (Customer customerEntity : customerSet) {
                  if (customerEntity.equals(customer)){
                      return customerEntity;
                  }
              }
          }
          customerSet.add(customer);
          return customer;
      }

      public Customer getCustomer(Long customerid){
          Customer customer = new Customer();
          customer.setCustomerId(customerid);
          if (customerSet.contains(customer)){
              for (Customer customerEntity : customerSet) {
                  if (customerEntity.equals(customer)){
                      return customerEntity;
                  }
              }
          }
          return null;
      }
      public Set<Customer> listCustomer(){
          return customerSet;
      }

      public Customer deleteCustomer(Long customerid){
          Customer customer = new Customer();
          customer.setCustomerId(customerid);
          if (customerSet.contains(customer)){
              customerSet.remove(customer);
              return customer;
          }
          return null;
      }

      public Customer updateCustomer(Customer customer){
          if (customerSet.contains(customer)){
              for (Customer customerEntity : customerSet) {
                  if (customerEntity.equals(customer)){
                      customerEntity.setCustomerId(customer.getCustomerId());
                      customerEntity.setFirstName(customer.getFirstName());
                      customerEntity.setLastName(customer.getLastName());
                      customerSet.remove(customer);
                      customerSet.add(customerEntity);
                      return customerEntity;
                  }
              }
          }
          return null;
      }

  }
  ```

* Criar a classe **CustomerRoute** com o seguinte conteúdo:

  ```
  package br.com.impacta.camel.springboot.helloworld;

  import org.apache.camel.builder.RouteBuilder;
  import org.apache.camel.model.rest.RestBindingMode;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.stereotype.Component;

  @Component
  public class CustomerRoute extends RouteBuilder {

      @Autowired
      CustomerService customerService;

      @Override
      public void configure() throws Exception {
          restConfiguration().host("localhost").port(8080).bindingMode(RestBindingMode.json);
          rest("/customers")
              .post("/").consumes("application/json").type(Customer.class).route().bean(customerService, "addCustomer(${body})").endRest()
              .get("/").produces("application/json").route().bean(customerService, "listCustomer").endRest()
              .get("/{id}").route().bean(customerService, "getCustomer(${header.id})").endRest()
              .put("/").consumes("application/json").type(Customer.class).route().bean(customerService, "updateCustomer(${body})").endRest()
              .delete("/{id}").produces("application/json").route().bean(customerService, "deleteCustomer(${header.id})").endRest();
      }
  }
  ```

* Teste da API:

  ```
  http :8080/customers
  http POST :8080/customers customerId=1111 firstName=nome1 lastName=sobrenome1
  http PUT :8080/customers customerId=1111 firstName=nome1ALTERADO lastName=sobrenome1UPDATE
  http POST :8080/customers customerId=2222 firstName=nome2 lastName=sobrenome2
  http :8080/customers
  http DELETE :8080/customers/2222
  http :8080/customers
  ```
