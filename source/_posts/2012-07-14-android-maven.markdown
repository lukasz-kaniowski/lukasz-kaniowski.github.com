---
layout: post
title: "Maven and Android"
date: 2012-07-14 18:13
comments: true
categories: [android]
published: true
---

I recently started looking into android development. After some time spend consuming information from the web it seems like
a lot of android development is done only on eclipse, without help from maven build tool.

If you are like me, comming from java enterprise world, you probably want to use maven for setuping and building your projects.
Below i described a few tools that come in handy for the job.

### Android Archetypes
Archetypes for android will help bootstrap your android project. Setup instructions are [here](https://github.com/akquinet/android-archetypes)

``` bash generate maven structure
mvn archetype:generate -Dfilter=android
# choose => de.akquinet.android.archetypes:android-quickstart
```

### Git setup

It's good to ignore android specyfic directories.

``` bash git with .gitignore
cd <project>
git init

# ignore files specyfic to android
curl https://raw.github.com/github/gitignore/master/Android.gitignore >> .gitignore
curl https://raw.github.com/github/gitignore/master/Maven.gitignore >> .gitignore

# First commit
git add .
git commit -m "init"
```

### Host your own maven repository on github
From time to time you will bump onto situation where there is no maven artifact for
the library you want to use. Solution is simple: host this library on your github account. Check
[here](http://blog.marrowboy.co.uk/2011/11/08/how-to-host-a-maven-repo-on-github/)
for setup instructions.


