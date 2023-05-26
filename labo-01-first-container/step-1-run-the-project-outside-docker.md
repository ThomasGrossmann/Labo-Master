# Step 1 - Run the project outside Docker

* [Official Source](https://docs.docker.com/language/java/build-images/)

## Get the project source code

* Clone the repo

```
git clone https://github.com/spring-projects/spring-petclinic.git
```

* Read the readme file carefully

<!---->

* [ ] What type of application is it?
* [ ] Which database engine is used?
* [ ] Do we need to install the package manager _MAVEN_ before building the project?

<!---->

* Inspect the dependencies (pom.xml)

<!---->

* [ ] Which version of Java should be compatible with the code provided?

## Setup Java components

### Check your current Java installation

* [ ] Where is Java installed?

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

* [ ] Which current compiler is installed (JDK)?

<pre><code><strong>[INPUT]
</strong>//TODO

[OUTPUT]
//TODO
</code></pre>

* [ ] Which current runtime is installed (JRE)?

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

* [ ] Do we need to install the Java virtual machine (JVM)?

```
//TODO
```

### Install the Open JDK

* [Oracle Download WebSite](https://jdk.java.net/20/)

{% hint style="info" %}
* Accept the end user license before trying, then
* Then get the target URL (cookies).
{% endhint %}

```powershell
[INPUT]
//TODO

[OUTPUT]
//TODO
```

#### Check the archive integrity before installing the JDK

* [Get the hash provided by Oracle](https://download.java.net/java/GA/jdk20.0.1/b4887098932d415489976708ad6d1a4b/9/GPL/openjdk-20.0.1\_windows-x64\_bin.zip.sha256)
* Generate your local hash based on the archive downloaded ([help](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.3))
* Compare both hashes...

```powershell
[INPUT]
//TODO

[OUTPUT]
//TODO
```

#### Unzip jdk archive

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

#### Move the unzip folder to Programs Folder

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

#### Set environment variables

* [Java official documentation](https://dev.java/learn/getting-started/)

<!---->

* [ ] Set JAVA\_HOME variable

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

* [ ] Update PATH environment variable

{% hint style="info" %}
Back up your current path before updating it.

echo %PATH% > path.back
{% endhint %}

```
[INPUT]
//TODO

[OUTPUT]
//TODO

```

* [ ] Check the variables

```
[INPUT]
//TODO

[OUTPUT]
//TODO

```

## Build and test the project

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

### Result expected 

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
