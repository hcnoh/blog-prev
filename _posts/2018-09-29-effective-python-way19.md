---
layout: post
title: "WAY 19. 키워드 인수로 선택적인 동작을 제공하자"
date: 2018-09-29 15:51:2
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 19. 키워드 인수로 선택적인 동작을 제공하자'
---

## 위치 인수 / 키워드 인수
{% highlight python %}
def remainder(number, divisor):
    return number % divisor

remainder(20, 7)                  # 위치 인수
remainder(20, divisor=7)          # 위치 인수 + 키워드 인수
remainder(number=20, divisor=7)   # 키워드 인수
remainder(divisor=7, number=20)   # 키워드 인수
{% endhighlight %}
- 위치 인수는 키워드 인수 앞에 지정해야 함
{% highlight python %}
remainder(number=20, 7)

>>>
SytaxError: non-keyword arg after keyword arg
{% endhighlight %}
- 각 인수는 한 번만 지정할 수 있음
{% highlight python %}
remainder(20, number=7)

>>>
SytaxError: remainder() got multiple values for argument "number"
{% endhighlight %}
