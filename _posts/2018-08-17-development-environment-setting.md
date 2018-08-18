---
layout: post
title: "Ubuntu 개발 환경 세팅"
date: 2018-08-17 23:29:31
image: '/assets/img/'
description: 'Ubuntu 개발 환경에서 vim, zshell 및 Tmux 세팅하는 방법 포스팅'
tags:
- vim
- zshell
- Tmux
categories:
- Development
twitter_text: 'Ubuntu 개발 환경 세팅'
comments: true
---

최근 업무용 개발 서버를 포맷하게 되었다. 따라서 개발용 세팅을 처음부터 다시 해야하는 상황. 세팅을 하며 어려웠던 점이나 팁같은 것들을 한 번 정리해 보았다.

## MobaXterm 설치

먼저 SSH 접속을 위한 터미널 툴인 MobaXterm을 설치하였다. 기존에는 Putty를 사용하였는데 bash shell이나 zshell을 커스터마이징을 하면 Putty는 그것을 예쁘게 잘 반영하지 못하는 듯 해서 MobaXterm으로 갈아탔다. 다운로드 링크는 다음과 같다: [https://mobaxterm.mobatek.net/](https://mobaxterm.mobatek.net/)
![image](/assets/img/2018-08-17-development-environment-setting/20180817_01.png)

Home Edition을 다운받아도 큰 문제는 없을 것이다.

![image](/assets/img/2018-08-17-development-environment-setting/20180817_02.png)

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

![image](/assets/img/2018-08-17-development-environment-setting/20180817_04.png)

설치가 무사히 끝난 상황이다.

![image](/assets/img/2018-08-17-development-environment-setting/20180817_05.png)

`exec zsh` 명령을 통하여 zshell을 실행시킨 결과이다.

## zshell 및 vim 세팅

터미널을 재시작하니 여전히 zshell이 default가 아닌 상황. 일단 zshell을 default로 바꿔주기 위해서는 다음과 같이 하면 된다. 먼저 `dotfiles update` 명령을 통하여 업데이트를 해준다.

![image](/assets/img/2018-08-17-development-environment-setting/20180817_06.png)

![image](/assets/img/2018-08-17-development-environment-setting/20180817_07.png)

업데이트가 완료되었고 다음과 같이 표시가 된다.

![image](/assets/img/2018-08-17-development-environment-setting/20180817_08.png)

터미널을 재시작하니 자동으로 zshell로 들어가지는 것을 확인할 수 있다.

![image](/assets/img/2018-08-17-development-environment-setting/20180817_09.png)

## 문제점 해결

sudo 권한이 없으면 설치가 안된다! 보통 sudo 권한 때문에 생기는 에러는 `~/.config` 내에서 `fsh` 디렉토리를 생성할 수 없다던가 또는 생성이 안되던가 하는 따위의 에러 메시지를 뱉어내곤 한다. 어쨌든 이런 경우에 `~/.config`의 접근 권한을 내 것으로 바꿔주면 무난히 해결이 가능하다.

Window 10 환경에서 MobaXterm을 활용하는 경우에 발생할 수 있는 문제는 vim 내에서 커서가 보이지 않는 경우이다.

![image](/assets/img/2018-08-17-development-environment-setting/20180817_10.png)

임시 방편으로 `set cursorcolumn`을 통하여 어느정도 해결하였으나 근본적인 해결은 될 수 없었다. 열심히 구글링해본 결과 다음과 같은 링크를 통해서 해결 방법을 찾아냈다: [https://www.reddit.com/r/vim/comments/4tu22w/set_termguicolors_makes_cursor_invisible/](https://www.reddit.com/r/vim/comments/4tu22w/set_termguicolors_makes_cursor_invisible/)

링크에서는 `set termguicolors`가 원인이 될 수 있다고 하였다. `set termguicolors`을 검색을 통하여 찾아낸 결과

![image](/assets/img/2018-08-17-development-environment-setting/20180817_11.png)

위의 부분을 발견하였고

![image](/assets/img/2018-08-17-development-environment-setting/20180817_12.png)

위와 같이 맨 밑에 줄에 있는 `call s:auto_termcuicolors`를 주석처리 해주었다.

![image](/assets/img/2018-08-17-development-environment-setting/20180817_13.png)

결과적으로 위와 같이 무사히 해결할 수 있었다.





