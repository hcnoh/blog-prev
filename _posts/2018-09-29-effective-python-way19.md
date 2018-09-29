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

## 키워드 인수의 유연성의 이점
- 코드를 처음 보는 사람이 함수 호출을 더 명확하게 이해할 수 있다는 점
- 함수를 정의할 때 기본 값을 설정할 수 있다는 점
    - 큰 통에 들어가는 액체의 유속을 계산하는 예제
{% highlight python %}
def flow_rate(weight_diff, time_diff):
    return weight_diff / time_diff

weight_diff = 0.5
time_diff = 3
flow = flow_rate(weight_diff, time_diff)
print("%.3f kg per second" % flow)

>>>
0.167 kg per second
{% endhighlight %}
