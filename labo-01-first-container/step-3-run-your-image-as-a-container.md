# Step 3 - Run your image as a container

* [Official Source](https://docs.docker.com/language/java/run-containers/)

<!---->

* [ ] Run your "petclinic" docker based on the image created in the previous step.
  * [ ] We should access to your application using the http standard port.

Result expected:

{% hint style="info" %}
Linux user, change ^ by ' to execute multi lines commands.
{% endhint %}

```
[INPUT]
curl --request GET \
--url http://localhost:8080/actuator/health \
--header 'content-type: application/json'

[OUTPUT]
{"status":"UP"}
```

* [x] List all Dockers currently running on your local environment. Observe the port forwarding for your "petclinic" docker.

```
[INPUT]
docker container ls

[OUTPUT]
CONTAINER ID   IMAGE             COMMAND                  CREATED         STATUS         PORTS                    NAMES
33234f9c93cf   vir:1   "./mvnw spring-boot:…"   4 minutes ago   Up 4 minutes   0.0.0.0:8080->8080/tcp   thirsty_johnson
```

* [x] Stop your "petclinic" docker

```
[INPUT]
CTRL C in the terminal

[OUTPUT]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  06:09 min
[INFO] Finished at: 2023-06-02T08:54:42Z
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.springframework.boot:spring-boot-maven-plugin:3.0.4:run (default-cli) on project spring-petclinic: Process terminated with exit code: 143 -> [Help 1]
[ERROR]
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException
```

* [x] Rename your docker as "petclinic-app"

<!---->

* [Official doc](https://docs.docker.com/engine/reference/commandline/rename/)

```
[INPUT]
docker tag vir:1 petclinic-app:1

[OUTPUT]
No specific output
```

* [x] Restart your docker using the new name

```
[INPUT]
docker run petclinic-app:1

[OUTPUT]
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 24 source files to /app/target/classes
[INFO]
[INFO] --- maven-resources-plugin:3.3.0:testResources (default-testResources) @ spring-petclinic ---
[INFO] skip non existing resourceDirectory /app/src/test/resources
[INFO]
[INFO] --- maven-compiler-plugin:3.10.1:testCompile (default-testCompile) @ spring-petclinic ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 11 source files to /app/target/test-classes
[INFO] /app/src/test/java/org/springframework/samples/petclinic/vet/VetTests.java: /app/src/test/java/org/springframework/samples/petclinic/vet/VetTests.java uses or overrides a deprecated API.
[INFO] /app/src/test/java/org/springframework/samples/petclinic/vet/VetTests.java: Recompile with -Xlint:deprecation for details.
[INFO]
[INFO] <<< spring-boot-maven-plugin:3.0.4:run (default-cli) < test-compile @ spring-petclinic <<<
[INFO]
[INFO]
[INFO] --- spring-boot-maven-plugin:3.0.4:run (default-cli) @ spring-petclinic ---
[INFO] Attaching agents: []


              |\      _,,,--,,_
             /,`.-'`'   ._  \-;;,_
  _______ __|,4-  ) )_   .;.(__`'-'__     ___ __    _ ___ _______
 |       | '---''(_/._)-'(_\_)   |   |   |   |  |  | |   |       |
 |    _  |    ___|_     _|       |   |   |   |   |_| |   |       | __ _ _
 |   |_| |   |___  |   | |       |   |   |   |       |   |       | \ \ \ \
 |    ___|    ___| |   | |      _|   |___|   |  _    |   |      _|  \ \ \ \
 |   |   |   |___  |   | |     |_|       |   | | |   |   |     |_    ) ) ) )
 |___|   |_______| |___| |_______|_______|___|_|  |__|___|_______|  / / / /
 ==================================================================/_/_/_/

:: Built with Spring Boot :: 3.0.4


2023-06-02T08:59:37.938Z  INFO 162 --- [  restartedMain] o.s.s.petclinic.PetClinicApplication     : Starting PetClinicApplication using Java 17.0.7 with PID 162 (/app/target/classes started by root in /app)
2023-06-02T08:59:37.939Z  INFO 162 --- [  restartedMain] o.s.s.petclinic.PetClinicApplication     : No active profile set, falling back to 1 default profile: "default"
2023-06-02T08:59:37.970Z  INFO 162 --- [  restartedMain] .e.DevToolsPropertyDefaultsPostProcessor : Devtools property defaults active! Set 'spring.devtools.add-properties' to 'false' to disable
2023-06-02T08:59:37.970Z  INFO 162 --- [  restartedMain] .e.DevToolsPropertyDefaultsPostProcessor : For additional web related logging consider setting the 'logging.level.web' property to 'DEBUG'
2023-06-02T08:59:38.378Z  INFO 162 --- [  restartedMain] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2023-06-02T08:59:38.405Z  INFO 162 --- [  restartedMain] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 24 ms. Found 2 JPA repository interfaces.
2023-06-02T08:59:38.649Z  INFO 162 --- [  restartedMain] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8080 (http)
2023-06-02T08:59:38.653Z  INFO 162 --- [  restartedMain] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2023-06-02T08:59:38.654Z  INFO 162 --- [  restartedMain] o.apache.catalina.core.StandardEngine    : Starting Servlet engine: [Apache Tomcat/10.1.5]
2023-06-02T08:59:38.678Z  INFO 162 --- [  restartedMain] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2023-06-02T08:59:38.679Z  INFO 162 --- [  restartedMain] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 708 ms
2023-06-02T08:59:38.719Z  INFO 162 --- [  restartedMain] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2023-06-02T08:59:38.805Z  INFO 162 --- [  restartedMain] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Added connection conn0: url=jdbc:h2:mem:e32b3348-6190-418a-a2da-063507d919a7 user=SA
2023-06-02T08:59:38.806Z  INFO 162 --- [  restartedMain] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Start completed.
2023-06-02T08:59:38.811Z  INFO 162 --- [  restartedMain] o.s.b.a.h2.H2ConsoleAutoConfiguration    : H2 console available at '/h2-console'. Database available at 'jdbc:h2:mem:e32b3348-6190-418a-a2da-063507d919a7'
2023-06-02T08:59:38.906Z  INFO 162 --- [  restartedMain] o.hibernate.jpa.internal.util.LogHelper  : HHH000204: Processing PersistenceUnitInfo [name: default]
2023-06-02T08:59:38.927Z  INFO 162 --- [  restartedMain] org.hibernate.Version                    : HHH000412: Hibernate ORM core version 6.1.7.Final
2023-06-02T08:59:39.067Z  INFO 162 --- [  restartedMain] SQL dialect                              : HHH000400: Using dialect: org.hibernate.dialect.H2Dialect
2023-06-02T08:59:39.438Z  INFO 162 --- [  restartedMain] o.h.e.t.j.p.i.JtaPlatformInitiator       : HHH000490: Using JtaPlatform implementation: [org.hibernate.engine.transaction.jta.platform.internal.NoJtaPlatform]
2023-06-02T08:59:39.442Z  INFO 162 --- [  restartedMain] j.LocalContainerEntityManagerFactoryBean : Initialized JPA EntityManagerFactory for persistence unit 'default'
2023-06-02T08:59:39.915Z  INFO 162 --- [  restartedMain] o.s.b.d.a.OptionalLiveReloadServer       : LiveReload server is running on port 35729
2023-06-02T08:59:39.918Z  INFO 162 --- [  restartedMain] o.s.b.a.e.web.EndpointLinksResolver      : Exposing 13 endpoint(s) beneath base path '/actuator'
2023-06-02T08:59:39.961Z  INFO 162 --- [  restartedMain] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2023-06-02T08:59:39.970Z  INFO 162 --- [  restartedMain] o.s.s.petclinic.PetClinicApplication     : Started PetClinicApplication in 2.177 seconds (process running for 2.39)
```

* [x] Display all running dockers with this output format

<!---->

* [Official doc](https://docs.docker.com/config/formatting/)

Result expected:

```
IMAGE                              PORTS.                  NAMES
eclipse-petclinic:version1.0.dev   0.0.0.0:80->8080/tcp.   petclinic-server
```

```
[INPUT]
docker ps --format "table {{.Image}}\t{{.Ports}}\t{{.Names}}"

[OUTPUT]
IMAGE             PORTS                    NAMES
petclinic-app:1   0.0.0.0:8080->8080/tcp   thirsty_johnson
```

