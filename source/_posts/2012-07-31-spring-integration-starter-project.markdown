---
layout: post
title: "Spring Integration Starter"
date: 2012-07-31 02:50
comments: true
categories: [spring]
published: false

---

This is intrudoction to [spring integration][1]. 

Before you start, first you should read [Enterprise Integration Patterns][2] for reference. 

Another worth checking source of information is springsource
examples github [repository][3].


### Create a project

Spring integration is devided into ``spring-integration-core`` and additional modules such as ``spring-integration-jmx`` or ``spring-integration-twitter``.

Springsource shares [information][4] how to configure your pom.

I will be creating project using gradle plugin. You need to follow [instructions][5] to install plugin locally. 

	mkdir register-parse-user
	gradle create-project-war
	gradle jettyRun
	open http://localhost:8080/register-parse-user/
	
You should see twitter example provided by springsource guys. 

### Http inbound gateway  

First endpoint of this application is a place where your other application can make a http request after user register with them. 

	<int-http:inbound-gateway request-channel="receiveChannel" name="/register" supported-methods="GET"/>
	
    <int:channel id="receiveChannel"/>

    <int:service-activator input-channel="receiveChannel" expression="'Retrieved: ' + payload" />
    






[1]: http://www.springsource.org/spring-integration/            "Spring Integration Project"
[2]: http://www.eaipatterns.com/toc.html                        "Enterprise Integration Patterns - TOC"
[3]: https://github.com/SpringSource/spring-integration-samples "Spring Integration Examples"
[4]: http://www.springsource.org/node/2962                      "List of spring integration modules"
[5]: https://github.com/SpringSource/spring-integration-templates/tree/master/si-gradle-plugin "Gradle plugin for spring integration"