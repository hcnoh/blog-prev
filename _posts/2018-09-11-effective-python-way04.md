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
