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
print("Red: ", red)
print("Green: ", green)
print("Opacity, ", opacity)

>>>
Red: "5"
Green: 0
Opacity: 0
{% endhighlight %}

red의 경우 my_values 딕셔너리 내부에 key가 있으며 value는 멤버 하나(문자열 "5")만 있는 리스트이다. 따라서 암시적으로 이 문자열은 `True`가 되며 red는 or 표현식의 첫 번째 부분을 할당받는다.

green의 경우 my_values 딕셔너리의 value가 멤버 하나(빈 문자열)만 있는 리스트이다. 빈 문자열은 암시적으로 `False`이므로 or 표현식의 결과는 두 번째 부분인 0이 된다.

opacity의 경우는 my_values 딕셔너리에 key가 아예 존재하지 않는다. get 메서드는 key가 딕셔너리에 없으면 두 번째 인수를 반환한다. 이때 반환되는 기본값은 멤버 하나(빈 문자열)만 있는 리스트이다. 따라서 or 표현식의 두 번째 부분인 0을 할당받는다.


