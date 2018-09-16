---
layout: post
title: "이펙티브 파이썬 스터디 WAY 06 정리"
date: 2018-09-16 20:51:23
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: '이펙티브 파이썬 스터디 WAY 06 정리'
---

# WAY 6. 한 슬라이스에 start, end, stride를 함께 쓰지 말자
이전 장에서 기본 슬라이싱 문법을 정리했는데 파이썬에서는 추가적으로 매 n번째 아이템을 가져올 수 있는 stride 문법을 제공한다.

## stride 기본 문법
- stride 문법의 기본 형태:
  - `some_list[start:end:stride]`
- stride 예시
{% highlight python %}
a = ["a", "b", "c", "d", "e", "f"]
odds = a[::2]
evens = a[1::2]
print(odds)
print(evens)

>>>
["a", "c", "e"]
["b", "d", "f"]
{% endhighlight %}
- -1 stride
{% highlight python %}
x = b'abcde'    # 바이트 문자열, 아스키 문자에는 잘 동작
y = x[::,-1]
print(y)

>>>
b'edcba'
{% endhighlight %}
{% highlight python %}
w = '原原'
x = w.encode("utf-8")   # `utf-8` 바이트 문자열로 인코드된 유니코드 문자에서는 동작하지 않음
y = x[::-1]
z = y.decode("utf-8")

>>>
UnicodeDecoderError: 'utf-8' codec can't decode byte 0x9d in position 0: invalid start byte
{% endhighlight %}
- -n stride
{% highlight python %}
a = ["a", "b", "c", "d", "e", "f", "g", "h"]
a[::2]    # ["a", "c", "e", "g"]
a[::-2]   # ["h", "f", "d", "b"]
{% endhighlight %}
