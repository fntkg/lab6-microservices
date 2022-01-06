# microservices report

Germán Garcés 757024

## Launching and registering services

### Service discovery

Launch Eureka server:

```
./gradlew :registration:bootRun
```

![](https://i.imgur.com/bTiNiKv.jpg)

### Account service

Launch account service:

```
./gradlew :accounts:bootRun
```

![](https://i.imgur.com/PdJ74TY.png)

### Web service

Launch web service:

```
./gradlew :web:bootRun
```

![](https://i.imgur.com/8dalhCJ.png)

### Checking services registration

Access http://localhost:1111/ and check if new services are there:

![](https://i.imgur.com/p6wNQTk.png)

## Second `accounts` service

Change `accounts` service default port in `accounts/src/main/resources/application.yml` to `4444` so there won't be problems with the `account` service currently running.

![](https://i.imgur.com/5ouypxm.png)

Now, launch new `accounts` service:

```
./gradlew :accounts:bootRun
```

Check dashboard, a new account should have appeared.

![](https://i.imgur.com/ZM8l5qr.png)


## Killing a service

When the first `accounts` service is killed, the first noticeable thing is one instance of `ACCOUNTS-SERVICE` has dissapeared from Eureka dashboard.

Next, when a request is made to  successful`web`, it shows a web. This happens because `web` service asks Eureka server the real location of the logical URL `https://ACCOUNTS-SERVICE` and Eureka answers with the location of the second `accounts` service.

![](https://i.imgur.com/KzBQiO8.png)
