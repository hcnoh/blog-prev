---
layout: post
title: "WAY 14. None을 반환하기보다는 예외를 일으키자"
date: 2018-09-26 17:39:13
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 14. None을 반환하기보다는 예외를 일으키자'
---

## 자연스럽지 않은 None 사용
- 파이썬 프로그래머들은 유틸리티 함수를 작성할 때 반환 값 `None`에 특별한 의미를 부여하는 경향이 있음
- 하지만 다음과 같은 경우에는 문제가 발생할 수 있음: 어떤 숫자를 다른 숫자로 나누는 헬퍼 함수 예제
{% highlight python %}
def divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return None
{% endhighlight %}
- 이 경우 0으로 나누는 경우에는 결과가 정의되어 있지 않기 때문에 `None`을 반환하는 것이 자연스러워 보임
{% highlight python %}
result = divide(x, y)
if result is None:
    print("Invalid inputs")
{% endhighlight %}
