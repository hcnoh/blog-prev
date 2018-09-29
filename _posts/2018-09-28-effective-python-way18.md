---
layout: post
title: "WAY 18. 가변 위치 인수로 깔끔하게 보이게 하자"
date: 2018-09-28 20:59:58
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 18. 가변 위치 인수로 깔끔하게 보이게 하자'
---

## 디버그 정보 몇 개를 로그로 남기는 예제
{% highlight python %}
def log(message, values):
    if not values:
        print(message)
    else:
        value_str = ", ".join(str(x) for x in values)
        print("%s: %s" % (message, values_str))

log("My numbers are", [1, 2])
log("Hi there", [])

>>>
My numbers are: 1, 2
Hi there
{% endhighlight %}

