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
log("Hi there", [])             # 빈 리스트를 넘겨야 하는 것이 불편함

>>>
My numbers are: 1, 2
Hi there
{% endhighlight %}
- 로그로 남길 값이 없을 때 빈 리스트를 넘겨야 하는 것이 불편함:
    - `*` 기호를 마지막 위치 파라미터 이름 앞에 붙이면 것으로 해결 가능
{% highlight python %}
def log(message, *values):  # 첫 번째 파라미터인 message는 필수, 그 다음에 나오는 위치 인수는 몇 개든 선택적임
    if not values:
        print(message)
    else:
        value_str = ", ".join(str(x) for x in values)
        print("%s: %s" % (message, values_str))

log("My numbers are", 1, 2)
log("Hi there")             # 호출하는 쪽만 수정

>>>
My numbers are: 1, 2
Hi there
{% endhighlight %}
- `*` 연산자를 이용하여 리스트를 입력으로 사용할 수 있음
{% highlight python %}
def log(message, *values):  # 첫 번째 파라미터인 message는 필수, 그 다음에 나오는 위치 인수는 몇 개든 선택적임
    if not values:
        print(message)
    else:
        value_str = ", ".join(str(x) for x in values)
        print("%s: %s" % (message, values_str))

favorites = [7, 33, 99]
log("Favorite colors", *favorites)

>>>
Favorite colors: 7, 33, 99
{% endhighlight %}

