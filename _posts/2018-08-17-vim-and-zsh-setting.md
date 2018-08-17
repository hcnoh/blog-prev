---
layout: post
title: "개발 환경 세팅 on Ubuntu"
date: 2018-08-17 23:29:31
image: '/assets/img/'
description: 'Ubuntu 개발 환경에서 vim 및 zshell 세팅하는 방법 포스팅'
tags:
- vim
- zshell
categories:
- Development
twitter_text: '개발 환경 세팅 on Ubuntu'
---

최근 업무용 개발 서버를 포맷하게 되었다. 따라서 개발용 세팅을 처음부터 다시 해야하는 상황. 세팅을 하며 어려웠던 점이나 팁같은 것들을 한 번 정리해 보았다.

## MobaXterm 설치

먼저 SSH 접속을 위한 터미널 툴인 MobaXterm을 설치하였다. 기존에는 Putty를 사용하였는데 bash shell이나 zshell을 커스터마이징을 하면 Putty는 그것을 예쁘게 잘 반영하지 못하는 듯 해서 MobaXterm으로 갈아탔다. 다운로드 링크는 다음과 같다: [https://mobaxterm.mobatek.net/](https://mobaxterm.mobatek.net/)
![image](github.com/hcnoh/hcnoh.gitub.io/assets/img/20180817_01.png)

## Site and User Settings

You have to fill some informations on `_config.yml` to customize your site.

{% highlight ruby %}
# Site settings
description: A blog about lorem ipsum dolor sit amet
baseurl: "" # the subpath of your site, e.g. /blog/
url: "http://localhost:3000" # the base hostname & protocol for your site 

# User settings
username: Lorem Ipsum
user_description: Anon Developer at Lorem Ipsum Dolor
user_title: Anon Developer
email: anon@anon.com
twitter_username: lorem_ipsum
github_username:  lorem_ipsum
gplus_username:  lorem_ipsum
disqus_username: lorem_ipsum
{% endhighlight %}

## Color customization

All color variables are in `src/styl/variable`. To change the main color, just set the new value at `main` assignment. Another colors are for texts and the code background color.

## Creating posts

You can use the `initpost.sh` to create your new posts. Just follow the command:

{% highlight bash %}
./initpost.sh -c Post Title
{% endhighlight %}

The new file will be created at `_posts` with this format `date-title.md`.

## Front-matter 

When you create a new post, you need to fill the post information in the front-matter, follow this example:

{% highlight ruby %}
---
layout: post
title: "How to use"
date: 2015-08-03 03:32:44
image: '/assets/img/post-image.png'
description: 'First steps to use this template'
tags:
- jekyll 
- template 
categories:
- I love Jekyll
twitter_text: 'How to install and use this template'
---
{% endhighlight %}


## Running the blog in local

In order to compile the assets and run Jekyll on local you need to follow those steps:

- Install [NodeJS](https://nodejs.org/)
- Run `npm install` 
- Run `gulp`

## Questions

Having a problem getting something to work or want to know why I setup something in a certain way? Ping me on Twitter [@willian_justen](https://twitter.com/willian_justen) or file a [GitHub Issue](https://github.com/willianjusten/will-jekyll-template/issues/new).

## License

This theme is free and open source software, distributed under the The MIT License. So feel free to use this Jekyll theme on your site without linking back to me or using a disclaimer.

If you’d like to give me credit somewhere on your blog or tweet a shout out to [@willian_justen](https://twitter.com/willian_justen), that would be pretty sweet.






