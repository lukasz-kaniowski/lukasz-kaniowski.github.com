---
layout: post
title: "Git Dropbox Sync Tool"
date: 2012-08-05 15:01
comments: true
categories: ['ruby']
---

I often use dropbox folder as a remote for my local git repositories. 

Lately I found this great shell [script][1], that makes work with your dropbox very easy. 

It is really great but I wanted more functionality, so on top of that I created gem: [git-dropbox on rubygems][2]

## Git Dropbox Gem

This gem lets you syncs your repository by executing command `git dropbox sync`. 

If you have multiple git repositorys and you want to be sure that all of them are sync to drobpox you can execute
`git dropbox sync --all`. It will sync all of the known repositories. 

For installation instruction and more details please check git-dropbox [github page][3]. 

[1]: https://github.com/agnoster/git-dropbox 
[2]: https://rubygems.org/gems/git-dropbox
[3]: https://github.com/lukasz-kaniowski/git-dropbox
