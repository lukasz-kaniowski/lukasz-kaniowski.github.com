---
layout: post
title: "Chef solo repo seed"
date: 2013-01-06 18:13
comments: true
categories: [chef]
published: true
---

If you need to create new repository for chef-solo simply execute commands below and you are good to go:

        $ git clone https://github.com/lukasz-kaniowski/chef-solo-seed.git your-repo
        $ cd your-repo
        $ bundle
        $ librarian-chef install

Now you should be able to create new roles and apply them using command below:

        $ chef-solo -c solo.rb -r "role[sample]"

Chef rocks!