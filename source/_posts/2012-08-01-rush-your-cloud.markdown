---
layout: post
title: "Rush your cloud"
date: 2012-08-01 10:33
comments: true
categories: [ruby, cloud]
published: true
---

## Blitz on heroku and cloudfront

There is a great performance testing tool out there and it calls [blitz.io][1]. If you haven't already try it, just give it a shot.
It's free for basic usage.

I decided to check how  basic [sinatra app][4] behave on [heroku][2] and [cloudfoundry][3].

### Sinatra app

Creation of sinatra app is very trivial. Just create a file `hello.rb`

``` ruby hello.rb
require 'sinatra'

get '/' do
    "Hello World!"
end
```

Blitz needs to verify if you are owner of the app to make a rush. Simple add this to `hello.rb`

``` ruby hello.rb
get '/mu-40e93541-db42b8f5-36bd0540-dcbf7834' do
    '42'
end
```

### Push to Cloud Foundry and Heroku

Lets deploy it to cloudfoundry. You need to [install vmc][5].

1. Target vmc to cloudfoundry.com `vmc target api.cloudfoundry.com`
2. Go to directory where you have `hello.rb` and execute `vmc push`.

To deploy it to heroku please fallow this [instructions][6]

### Rush using Blitz.io

Now you are ready to make a rush. Bellow are mine results

#### Heroku

{% img /images/rush_blitz/heroku_hit_rate.jpg %}
{% img /images/rush_blitz/heroku_response.jpg %}
{% img /images/rush_blitz/heroku_summary.jpg %}

#### Cloud Foundry

{% img /images/rush_blitz/cloud_hit.png %}
{% img /images/rush_blitz/cloud_response.jpg %}
{% img /images/rush_blitz/cloud_summary.jpg %}








[1]: http://blitz.io/bb8Efr2XeUJewKEdOjRU7OM
[2]: http://www.heroku.com/
[3]: http://www.cloudfoundry.com/
[4]: http://www.sinatrarb.com/
[5]: http://docs.cloudfoundry.com/tools/vmc/installing-vmc.html/
[6]: https://devcenter.heroku.com/articles/rack
