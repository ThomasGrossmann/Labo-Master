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
curl --request GET ^
--url http://localhost:8080/actuator/health ^
--header 'content-type: application/json'

[OUTPUT]
curl: (7) Failed to connect to localhost port 8080 after 5 ms: Couldn't connect to server
```

* [ ] List all Dockers currently running on your local environment. Observe the port forwarding for your "petclinic" docker.

```
[INPUT]
//TODO

[OUTPUT]
//TODO

```

* [ ] Stop your "petclinic" docker

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

* [ ] Rename your docker as "petclinic-app"

<!---->

* [Official doc](https://docs.docker.com/engine/reference/commandline/rename/)

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

* [ ] Restart your docker using the new name

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

* [ ] Display all running dockers with this output format

<!---->

* [Official doc](https://docs.docker.com/config/formatting/)

Result expected:

```
IMAGE                              PORTS.                  NAMES
eclipse-petclinic:version1.0.dev   0.0.0.0:80->8080/tcp.   petclinic-server
```

```
[INPUT]
//TODO

[OUTPUT]
//TODO
```

