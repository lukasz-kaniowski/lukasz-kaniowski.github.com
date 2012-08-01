---
layout: post
title: "Creating Cli Gem Quickly"
date: 2012-08-02 01:18
comments: true
categories: [ruby]
---

So you have some small, repetitive task to do. You create a script (bash, rake, thor) and you store it locally. After some time you forget where
it is and how to use it.

You could create a gem  and then add thor to it (described in this [article][1]). It's good but we can do better.

Here is a quick tutorial how.

## Install ore and thor template

[Ore][2] is a ruby project generator.

`$ gem install ore`

Ore generetes project based on templates. It has some templates built in, but you can also create your own.
There wasn't any template for thor so I created [one][3]. Install it:

`$ ore install https://github.com/lukasz-kaniowski/ore-thor`

## Generate thor project

Now you are ready to create your thor gem.

1. Create project 'helloworld' `$ mine helloworld --ore-thor --bundler`
2. Bundle project `$ cd helloworld; bundle`
3. Fill all todo's from `helloworld.gemspec`
4. Commit to git `$ git commit -am 'init' `
5. Install to your local gems `$ rake install`
6. Test it `$ helloworld` and `$ helloworld sample`

Thats all, now you can create cli gems in seconds.


[1]: http://chrisparai.so/creating-a-gem-from-a-thor-applicaton/ "Creating a Gem From a Thor Applicaton"
[2]: https://github.com/ruby-ore/ore
[3]: https://github.com/lukasz-kaniowski/ore-thor


