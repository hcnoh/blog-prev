---
layout: post
title: "이펙티브 파이썬 스터디 WAY 04 정리"
date: 2018-09-11 16:14:35
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: '이펙티브 파이썬 스터디 WAY 04 정리'
---

## WAY 4. 복잡한 표현식 대신 헬퍼 함수를 작성하자
다음 코드는 URL에서 쿼리 문자열을 디코드하는 스크립트이다.
{% highlight python %}
from urllib.parse import parse_qs
my_values = parse_qs("red=5&blue=0%green=", keep_blank_values=True)
print(repr(my_values))

>>>
{"red": ["5"], "green": [""], "blue": ["0"]}
{% endhighlight %}
각 쿼리 문자열의 파라미터는 정수 값을 표현한다.

다음의 코드를 살펴보자.
{% highlight python %}
print("Red: ", my_values.get("red"))
print("Green: ", my_values.get("green"))
print("Opacity: " my_values.get("opacity"))

>>>
Red: ["5"]
Green: [""]
Opacity: None
{% endhighlight %}
red와 green 파라미터는 제대로 나오며 opacity 파라미터는 빠져있기 때문에 `None`으로 나오는 것을 알 수 있다.

파라미터가 없거나 비어있으면 기본값으로 0을 할당하게 하면 좋을 것이다. 파이썬의 문법 덕분에 불(boolean) 표현식으로도 아주 쉽게 처리할 수 있다.
{% highlight python %}
red = my_values.get("red", [""])[0] or 0
green = my_values.get("green", [""])[0] or 0
opacity = my_values.get("opacity", [""])[0] or 0
{% endhighlight %}
