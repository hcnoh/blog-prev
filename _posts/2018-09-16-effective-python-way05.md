---
layout: post
title: "이펙티브 파이썬 스터디 WAY 05 정리"
date: 2018-09-16 20:13:57
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: '이펙티브 파이썬 스터디 WAY 05 정리'
---

# WAY 5. 시퀀스를 슬라이스하는 방법을 알자
이번 장에서는 파이썬의 시퀀스 슬라이싱 문법을 정리한다. 슬라이싱의 대상이 되는 것은 파이썬 내장 타입인 `list`, `str`, `bytes`와 `__getitem__`과 `__setitem__`이라는 특별한 메서드를 구현하는 파이썬의 클래스이다.

## 슬라이싱의 기본 문법
- 슬라이싱 문법의 기본 형태:
  - `some_list[start:end]`
  - start 인덱스는 포함되고 end 인덱스는 제외
- 슬라이싱 예시:
{% highlight python %}
a = ["a", "b", "c", "d", "e", "f", "g", "h"]
print("Firts four:", a[:4])     # 리스트의 처음부터 슬라이스할 때는 인덱스 0 생략: assert a[:5] == a[0:5]
print("Last four:", a[-4:])
print("Middle two:", a[3:-3])

>>>
First four: ["a", "b", "c", "d"]
First four: ["e", "f", "g", "h"]
Middle two: ["d", "e"]
{% endhighlight %}
