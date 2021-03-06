# Objective

This project is a prototype in order to materialize CSRF prevention concepts described in the following OWASP cheatsheet:

https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet

Precisely the following concepts:
* Verifying same origin with standard headers
* CSRF specific defense:
    * Double submit cookie (stateless)
    * Leverage *SameSite* cookie attribute

The POC will focus on stateless approach, i.e. no use of Session for CSRF token storage, because the following project, OWASP CSRFGuard, cover the stateful approach:

https://github.com/aramrami/OWASP-CSRFGuard

All classes are fully documented.

The project is developed with Maven under IntelliJ IDEA.

A web page propose to send manual request in parallel of automated requests sending in order to show all parallel exchanges and CSRF tokens parallel handling.

![Demo](demo1.png)

![Demo](demo2.png)

![Demo](demo3.png)

# Note about the SameSite cookie attribute

Source from *https://tools.ietf.org/html/draft-ietf-httpbis-cookie-same-site-00*:

"These attribute are intended to provide a solid layer of defense-in-depth against attacks which require embedding an authenticated request into an attacker-controlled context."

Unfortunately, for the moment, only **Chrome** based browser supports this attribute:

http://caniuse.com/#feat=same-site-cookie-attribute
 
There a very good description of this attribute here:

https://chloe.re/2016/04/13/goodbye-csrf-samesite-to-the-rescue/


# Build or Run

Add the following line to your **hosts** file:

```
# Local domain
127.0.0.1 local.net
```

Run the following command to create a WAR archive:
```
mvn clean package
```

Run the following command to run the prototype (it will exposed on **http://local.net:9090**):
```
mvn tomcat7:run-war
```

# TODO

- Auto deploy POC on cloud provider 

# Main references

* Origin HTTP header - https://wiki.mozilla.org/Security/Origin
* Description of the SameSite attribute - https://chloe.re/2016/04/13/goodbye-csrf-samesite-to-the-rescue/
* SameSite attribute specification - https://tools.ietf.org/html/draft-ietf-httpbis-cookie-same-site-00
* SameSite attribute supports - http://caniuse.com/#feat=same-site-cookie-attribute
