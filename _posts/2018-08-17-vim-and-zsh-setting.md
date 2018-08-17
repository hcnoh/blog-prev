---
layout: post
title: "개발 환경 세팅 on Ubuntu"
date: 2018-08-17 23:29:31
image: '/assets/img/'
description: 'Ubuntu 개발 환경에서 vim 및 zshell 세팅하는 방법 포스팅'
tags:
- vim
- zshell
- Tmux
categories:
- Development
twitter_text: '개발 환경 세팅 on Ubuntu'
---

최근 업무용 개발 서버를 포맷하게 되었다. 따라서 개발용 세팅을 처음부터 다시 해야하는 상황. 세팅을 하며 어려웠던 점이나 팁같은 것들을 한 번 정리해 보았다.

## MobaXterm 설치

먼저 SSH 접속을 위한 터미널 툴인 MobaXterm을 설치하였다. 기존에는 Putty를 사용하였는데 bash shell이나 zshell을 커스터마이징을 하면 Putty는 그것을 예쁘게 잘 반영하지 못하는 듯 해서 MobaXterm으로 갈아탔다. 다운로드 링크는 다음과 같다: [https://mobaxterm.mobatek.net/](https://mobaxterm.mobatek.net/)
![image](/assets/img/20180817_01.png)

Home Edition을 다운받아도 큰 문제는 없을 것이다.

![image](/assets/img/20180817_02.png)

MobaXterm을 통해 업무용 서버로 접속한 모습

## dotfiles를 이용한 setting 가져오기

Tmux 및 zshel, 그리고 vim의 config까지 미리 세팅된 dotfile을 가져와서 간단하게 바로 세팅할 수 있었다. 사용된 dotfiles는 다음의 링크에서 받을 수 있었다: [https://github.com/wookayin/dotfiles](https://github.com/wookayin/dotfiles)

One-liner (if, you trust):
{% highlight bash %}
curl -fsSL https://dotfiles.wook.kr/etc/install | bash
{% endhighlight %}
An alternative:
{% highlight bash %}
git clone --recursive https://github.com/wookayin/dotfiles.git ~/.dotfiles
cd ~/.dotfiles && python install.py
{% endhighlight %}

위의 One-liner 명령어 만으로 한번에 설치가 가능하였다.

![image](/assets/img/20180817_04.png)

설치가 무사히 끝난 상황이다.

![image](/assets/img/20180817_05.png)

`exec zsh` 명령을 통하여 zshell을 실행시킨 결과이다.

## zshell 및 vim 세팅

터미널을 재시작하니 여전히 zshell이 default가 아닌 상황. 일단 zshell을 default로 바꿔주기 위해서는 다음과 같이 하면 된다. 먼저 `dotfiles update` 명령을 통하여 업데이트를 해준다.

![image](/assets/img/20180817_06.png)

![image](/assets/img/20180817_07.png)

업데이트가 완료되었고 다음과 같이 표시가 된다.

![image](/assets/img/20180817_08.png)

터미널을 재시작하니 자동으로 zshell로 들어가지는 것을 확인할 수 있다.

![image](/assets/img/20180817_09.png)

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






