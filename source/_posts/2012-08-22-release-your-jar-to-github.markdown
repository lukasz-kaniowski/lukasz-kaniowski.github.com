---
layout: post
title: "Release your jar to github"
date: 2012-08-22 23:45
comments: true
categories: java

---

If you ever need to quickly publish any of your jars to the public, quickest way is to use github. 

    
### Create maven repo on github
You need to create repository on github, in my case i called it maven-repository. 

You need to clone this repo locally as this is where you will be releasing your jars. 

### Pom configuration and settings.xml
To your project's pom you need to add this lines

	<scm>
        <url>https://github.com/lukasz-kaniowski/android_utils</url>
        <connection>scm:git:https://github.com/lukasz-kaniowski/android_utils</connection>
        <developerConnection>scm:git:https://github.com/lukasz-kaniowski/android_utils</developerConnection>
    </scm>
    <distributionManagement>
        <repository>
            <id>github-repo</id>
            <url>https://github.com/lukasz-kaniowski/maven-repository/raw/master</url>
        </repository>
    </distributionManagement>

Actually you will not be publishing your jars directly to github but to your local clone of github repository. To do so you need to override `distributionManagement` variable. Best is to do this in `~/.m2/settings.xml`
	
	<profile>
		<id>deploy-github</id>
		<properties>
			<altDeploymentRepository>release-repo::default::file:/path/to/local/github/repo</altDeploymentRepository>
		</properties>
	</profile>

Now you are good to go.

### Release your jar

Process of releasing jar is straightforward:

	cd /path/to/your/mvn/project
	mvn release:prepare
	mvn release:perform -Pdeploy-github
	
Next you need to push changes from your local clone of github repo

	cd /path/to/local/github/repo
	git add .
	git commit -m "new jar release"
	git push origin master
	
### Configure maven project to use your new github repository

To use your released jars you will need to add this line into your project's pom 

	<repositories>
        <repository>
            <id>Repo on Github</id>
            <url>https://github.com/lukasz-kaniowski/maven-repository/raw/master</url>
        </repository>
    </repositories>
    
Nothing else left to say than just that **Github is awesome!!!**


	
