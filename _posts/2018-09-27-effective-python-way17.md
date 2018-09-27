---
layout: post
title: "WAY 17. 인수를 순회할 때는 방어적으로 하자"
date: 2018-09-27 20:16:38
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 17. 인수를 순회할 때는 방어적으로 하자'
---

## 파라미터로 객체의 리스트를 받는 함수 예제
- 정규화 함수
{% highlight python %}
def normalize(numbers):
    total = sum(numbers)
    result = []
    for value in numbers:
        percent = 100 * value / total
        result.append(percent)
    return result
{% endhighlight %}
