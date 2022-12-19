# REPORT

This document contains a brief of how the following activities have been accomplished:

- The two services `accounts (2222)` and `web` are running and registered (two terminals, logs screenshots).
- The service registration service has these two services registered (a third terminal, dashboard screenshots)
- A second `accounts` service instance is started and will use the port 4444. This second `accounts (4444)` is also
  registered (a fourth terminal, log screenshots).
- What happens when you kill the service `accounts (2222)` and do requests to `web`?  
  Can the web service provide information about the accounts again? Why?

## Steps

The registration server is exposed in `http://localhost:1111`.

![Captura1.PNG](Captura1.PNG)

The account service is exposed in `http://localhost:2222`.

![Captura2.PNG](Captura2.PNG)

We can see that the account service is registered in the registration server:

![Captura3.PNG](Captura3.PNG)

Next, we launch launch the third application, the web one, at port 3333.

![Captura4.PNG](Captura4.PNG)

We can see that these two services are registered in the registration server:

![Captura5.PNG](Captura5.PNG)

Now we change the port of the account service to 4444 for example:

```yaml
spring:
  application:
    name: accounts-service  # Identify this application
# HTTP Server
server:
  port: 4444   # HTTP (Tomcat) port
```

Then we launch the new account service:

![Captura6.PNG](Captura6.PNG)

There are three services registered in the registration server now:

![Captura7.PNG](Captura7.PNG)

Now we shutdown the account service at port 2222:

![Captura8.PNG](Captura8.PNG)

When we try to fetch an account, sometimes it fails and sometimes it succeeds:

![Captura9.PNG](Captura9.PNG)