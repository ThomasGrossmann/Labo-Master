# Step 2 - Create a Dockerfile for Java

* [Official Source](https://docs.docker.com/language/java/build-images/#create-a-dockerfile-for-java)

## Create your docker file

* [ ] Change the directory to the app directory (we will use the same project [as for the previous step](step-1-run-the-project-outside-docker.md)).
* [ ] Create an empty file named "Dockerfile"

```
[INPUT]
cd $HOME/Documents/Github/VIR1/spring-petclinic/
touch Dockerfile

[OUTPUT]
No specific output
```

* Using your IDE, add the following contents to the Dockerfile:

```
# synthax=docker/dockerfile:1

FROM eclipse-temurin:17-jdk-jammy
```

* [x] What is the purpose of the directive starting with "# synthax=docker..."

<!---->

* [Official documentation - Synthax directive](https://docs.docker.com/build/dockerfile/frontend/)

```
It overrides the default Docker frontend.
```

* [ ] Is the docker image suitable for a production environment?

```
//TODO
```

### Dependencies resolution and first app build

* [x] Set the image's working directory by adding this command line:

```
WORKDIR /app
```

* [x] Before we can resolve dependencies with _MAVEN,_ we need to get the _MAVEN_ wrapper and your pom.xml file into your image.

```
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
```

* [x] Let's use _MAVEN_ to resolve the dependencies.

```
RUN ./mvnw dependency:resolve
```

* [x] How is it possible to resolve the dependencies when the source code is not available at this point in the process?

```
The dependencies are resolved from the pom.xml file so it is not necessary to have the source code for now.
```

* Add the command able to provide (copy) your source code to the image.

```
COPY ./src /app
```

* Add the command responsible to run your application inside the Docker.

```
CMD ["./mvnw", "spring-boot:run"]
```

## Create a .dockerignore file

* [Official documentation - dockerignore](https://docs.docker.com/language/java/build-images/#create-a-dockerignore-file)

{% hint style="info" %}
To meet the good practice provided by Docker, we have to reduce the amount of data in the Docker build context. For this first lab, we will simply remove the directory containing the eventual outputs of MAVEN.
{% endhint %}

* [x] Create a .dockerignore file in the same directory as the Dockerfile.
* [x] Add the folder containing the MAVEN output.

## Build an image

{% hint style="info" %}
Best practices - docker tag naming convention:\
Read carefully [this doc](https://docs.docker.com/develop/dev-best-practices/) and deduce the right tag for your image.\
This [doc may also help you with tag samples](https://docs.docker.com/engine/reference/commandline/tag/).
{% endhint %}

* [x] Find the best tag for your image (this image is not intended for publication.)

```
docker tag vir:1
```

* [x] Build your first Docker image

Result Expected:

```
docker build --tag vir:1
Sending build context to Docker daemon   9.92MB
Step 1/7 : FROM eclipse-temurin:17-jdk-jammy
 ---> 56c7bc12ee6d
 ---> Using cache
 ---> b4854585fa31
Step 3/7 : COPY .mvn/ .mvn
 ---> Using cache
 ---> b72a055eb5f8
Step 4/7 : COPY mvnw pom.xml ./
 ---> Using cache
 ---> ae3709e4bfb7
Step 5/7 : RUN ./mvnw dependency:resolve
 ---> Using cache
 ---> e62d33f55785
Step 6/7 : COPY src ./src
 ---> Using cache
 ---> b926a101aec1
Step 7/7 : CMD ["./mvnw", "spring-boot:run"]
 ---> Using cache
 ---> 910e5f0c8b1f
Successfully built 910e5f0c8b1f
Successfully tagged java-docker:dev
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to dou
ble check and reset permissions for sensitive files and directories.

```

```
[INPUT]
docker build --tag vir:1 .

[OUTPUT]
[+] Building 400.3s (11/11) FINISHED
=> [internal] load build definition from Dockerfile
=> => transferring dockerfile: 232B
=> [internal] load .dockerignore
=> [internal] load metadata for docker.io/library/eclipse-temurin:17-jdk-jammy
=> [1/6] FROM docker.io/library/eclipse-temurin:17-jdk-jammy@sha256:13ff0fa4f9232f69b9f6e8a4cf86b7cb3a3783dbee06818aa5aee447159c1bc3
=> => resolve docker.io/library/eclipse-temurin:17-jdk-jammy@sha256:13ff0fa4f9232f69b9f6e8a4cf86b7cb3a3783dbee06818aa5aee447159c1bc3
=> => sha256:f7e2ea804cf3eb99ede72c4190dd3df195e93e5efa059ac56b5ba6170423f227 191.40MB / 191.40MB
=> => sha256:13ff0fa4f9232f69b9f6e8a4cf86b7cb3a3783dbee06818aa5aee447159c1bc3 1.21kB / 1.21kB
=> => sha256:9b636b8f207f4ccf70ff69c13229dea8077788cf6b968307582eb3b2c9fb665c 1.16kB / 1.16kB
=> => sha256:c83e061ebfc9fac164e3b16dbaedb1d718c88a6e86fc3e23465a4071296502b3 6.32kB / 6.32kB
=> => sha256:f3f60f415e9a03eed88bd5dd5268c841cde08dacf16911a3ef1e4e0fcdd76568 28.39MB / 28.39MB
=> => sha256:2da9c27f8f486373408efc6e2d12bdb650ff3041dc480e2fcd2dd0c7e9be9777 18.47MB / 18.47MB
=> => sha256:7ad5170cfb57d48d8209d266deda3bd50024fea3a47edc24a73bdbd64ca9f9b2 171B / 171B
=> => extracting sha256:f3f60f415e9a03eed88bd5dd5268c841cde08dacf16911a3ef1e4e0fcdd76568
=> => extracting sha256:2da9c27f8f486373408efc6e2d12bdb650ff3041dc480e2fcd2dd0c7e9be9777
=> => extracting sha256:f7e2ea804cf3eb99ede72c4190dd3df195e93e5efa059ac56b5ba6170423f227
=> => extracting sha256:7ad5170cfb57d48d8209d266deda3bd50024fea3a47edc24a73bdbd64ca9f9b2
=> [internal] load build context
=> => transferring context: 9.57kB
=> [2/6] WORKDIR /app
=> [3/6] COPY .mvn/ .mvn
=> [4/6] COPY mvnw pom.xml ./
=> [5/6] RUN ./mvnw dependency:resolve
=> [6/6] COPY ./src src
=> exporting to image
=> => exporting layers
=> => writing image sha256:a340bc2a086c5047a9b48fc5cd0bfea003dc6680b179f171facd7883bb1f8636
=> => naming to docker.io/library/vir:1
```

### View local images

* [x] Using the "docker images" command, observe your images, and the associates tag.

Result expected:\


```
docker images
REPOSITORY        TAG            IMAGE ID       CREATED          SIZE
java-docker       <yourTag>      910e5f0c8b1f   11 minutes ago   606MB
eclipse-temurin   17-jdk-jammy   56c7bc12ee6d   3 days ago       456MB
```

```
[INPUT]
docker images

[OUTPUT]
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
vir          1         a340bc2a086c   6 minutes ago   602MB
```
