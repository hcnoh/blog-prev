---
layout: post
title: "TensorFlow 설치"
date: 2018-09-17 1:28:2
image: '/assets/img/'
description: 'Virtualenv를 이용하여 TensorFlow 설치하는 방법 정리'
tags:
- python
- tensorflow
- virtualenv
categories:
- Development
twitter_text: 'TensorFlow 설치'
---

Tmux 및 zshell, vim까지 세팅이 대충 끝나고 이제는 TensorFlow를 설치하여 작업 환경 구축을 마무리할 생각이다. TensorFlow는 여러 가상환경 위에서 설치하는 것을 제공하지만 여기서는 Virtualenv를 이용한 가상환경 위에서 설치하는 방법을 정리하였다.

## 가상환경 만들기
먼저 다음과 같이 파이썬 가상환경을 만들어 준다. 물론 Virtualenv는 이미 설치가 되어있는 상태이다. 가상환경의 이름은 tensorflow로 한다.
{% highlight bash %}
>>> virtualenv tensorflow
{% endhighlight %}
이렇게 하면 tensorflow라는 이름의 가상환경을 만들 수 있다.
{% highlight bash %}
>>> virtualenv --system-site-packages -p python3 tensorflow
{% endhighlight %}
