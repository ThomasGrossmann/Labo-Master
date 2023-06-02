# Step 1 - Run the project outside Docker

* [Official Source](https://docs.docker.com/language/java/build-images/)

## Get the project source code

* Clone the repo

```
git clone https://github.com/spring-projects/spring-petclinic.git
```

* Read the readme file carefully

<!---->

* [x] What type of application is it? : Application web
* [x] Which database engine is used? : H2, Postgres, MySQL
* [x] Do we need to install the package manager _MAVEN_ before building the project? : No, you can also build the project using Gradle.

<!---->

* Inspect the dependencies (pom.xml)

<!---->

* [x] Which version of Java should be compatible with the code provided? : 17 or newer

## Setup Java components

### Check your current Java installation

* [x] Where is Java installed?

```
[INPUT]
which java

[OUTPUT]
/usr/bin/java
```

* [x] Which current compiler is installed (JDK)?

```
[INPUT]
java --version

[OUTPUT]
openjdk 20.0.1 2023-04-18
```

* [x] Which current runtime is installed (JRE)?

```
[INPUT]
java --version

[OUTPUT]
OpenJDK Runtime Environment (build 20.0.1+9-29)
```

* [x] Do we need to install the Java virtual machine (JVM)? : No, it is included in the JDK.

### Install the Open JDK

* [Oracle Download WebSite](https://jdk.java.net/20/)

{% hint style="info" %}
* Accept the end user license before trying, then
* Then get the target URL (cookies).
{% endhint %}

```
[INPUT]
curl https://download.java.net/java/GA/jdk20.0.1/b4887098932d415489976708ad6d1a4b/9/GPL/openjdk-20.0.1_macos-aarch64_bin.tar.gz --output openjdk.tar.gz

[OUTPUT]
No specific output.
```

#### Check the archive integrity before installing the JDK

* [Get the hash provided by Oracle](https://download.java.net/java/GA/jdk20.0.1/b4887098932d415489976708ad6d1a4b/9/GPL/openjdk-20.0.1\_windows-x64\_bin.zip.sha256)
* Generate your local hash based on the archive downloaded ([help](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.3))
* Compare both hashes...

```
[INPUT]
shasum -a 256 openjdk.tar.gz

[OUTPUT]
78ae5bb4c96632df8d3f776919c95653d1afd3e715981c4d33be5b3c81d05420  openjdk.tar.gz
```

#### Unzip jdk archive

```
[INPUT]
tar -xf openjdk.tar.gz

[OUTPUT]
No specific output.
```

#### Move the unzip folder to Programs Folder

```
[INPUT]
sudo mv jdk-20.0.1.jdk /Library/Java/JavaVirtualMachines

[OUTPUT]
No specific output.
```

#### Set environment variables

* [Java official documentation](https://dev.java/learn/getting-started/)

<!---->

* [x] Set JAVA\_HOME variable

```
[INPUT]
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-20.0.1.jdk
echo $JAVA_HOME

[OUTPUT]
/Library/Java/JavaVirtualMachines/jdk-20.0.1.jdk
```

* [x] Update PATH environment variable

{% hint style="info" %}
Back up your current path before updating it.

echo %PATH% > path.back
{% endhint %}

```
[INPUT]
echo $PATH > path.back

[OUTPUT]
No specific output.
```

* [x] Check the variables

```
[INPUT]
export PATH=$JAVA_HOME/bin:$PATH
which java

[OUTPUT]
/usr/bin/java
```

## Build and test the project

```
[INPUT]
./mvnw package

[OUTPUT]
[INFO] Results:
[INFO]
[WARNING] Tests run: 41, Failures: 0, Errors: 0, Skipped: 1
[INFO]
[INFO]
[INFO] --- jacoco-maven-plugin:0.8.8:report (report) @ spring-petclinic ---
[INFO] Loading execution data file /Users/thomas/Documents/Github/VIR1/spring-petclinic/target/jacoco.exec
[INFO] Analyzed bundle 'petclinic' with 21 classes
[INFO]
[INFO] --- maven-jar-plugin:3.3.0:jar (default-jar) @ spring-petclinic ---
[INFO] Building jar: /Users/thomas/Documents/Github/VIR1/spring-petclinic/target/spring-petclinic-3.0.0-SNAPSHOT.jar
[INFO]
[INFO] --- spring-boot-maven-plugin:3.0.4:repackage (repackage) @ spring-petclinic ---
[INFO] Replacing main artifact with repackaged archive
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  10.417 s
[INFO] Finished at: 2023-06-02T10:38:42+02:00
[INFO] ------------------------------------------------------------------------
```

### Result expected 

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
