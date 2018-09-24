---
layout: post
title: "WAY 5. 시퀀스를 슬라이스하는 방법을 알자"
date: 2018-09-16 20:13:57
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 5. 시퀀스를 슬라이스하는 방법을 알자'
---

이번 장에서는 파이썬의 시퀀스 슬라이싱 문법을 정리한다. 슬라이싱의 대상이 되는 것은 파이썬 내장 타입인 `list`, `str`, `bytes`와 `__getitem__`과 `__setitem__`이라는 특별한 메서드를 구현하는 파이썬의 클래스이다.

## 슬라이싱의 기본 문법
- 슬라이싱 문법의 기본 형태:
  - `some_list[start:end]`
  - `start 인덱스`는 포함되고 `end 인덱스`는 제외
- 슬라이싱 예시:
{% highlight python %}
a = ["a", "b", "c", "d", "e", "f", "g", "h"]
print("Firts four:", a[:4])     # 리스트의 처음부터 슬라이스할 때는 인덱스 0 생략: assert a[:5] == a[0:5]
print("Last four:", a[-4:])     # 리스트의 끝까지 슬라이스 할 때는 마지막 인덱스 생략: assert a[5:] == a[5:len(a)]
print("Middle two:", a[3:-3])   # 리스트의 끝을 기준으로 오프셋 계산할 때는 음수로 슬라이스

>>>
First four: ["a", "b", "c", "d"]
First four: ["e", "f", "g", "h"]
Middle two: ["d", "e"]
{% endhighlight %}

## 슬라이싱 및 인덱싱 범위
- 슬라이싱은 `start 인덱스`/`end 인덱스`가 경계를 벗어나도 적절히 처리
{% highlight python %}
first_twenty_items = a[:20]
last_twenty_items = a[-20:]
{% endhighlight %}
- 인덱스 직접 접근은 경계를 벗어날 수 없음
{% highlight python %}
a[20]

>>>
IndexError: list index out of range
{% endhighlight %}
- 음수 인덱싱은 다음과 같은 주의사항이 있음
{% highlight python %}
a[-3:]    # 제대로 동작
assert a[-0:] == a[:]
{% endhighlight %}

## 리스트의 할당
- 슬라이싱의 결과는 완전히 새로운 리스트
{% highlight python %}
a = ["a", "b", "c", "d", "e", "f", "g", "h"]
b = a[4:]
print("Before: ", a)
print("Before: ", b)
b[1] = 99
print("After: ", a)
print("After: ", b)

>>>
Before: ["a", "b", "c", "d", "e", "f", "g", "h"]
Before: ["e", "f", "g", "h"]
After: ["a", "b", "c", "d", "e", "f", "g", "h"]
After: ["e", 99, "g", "h"]
{% endhighlight %}
- 튜플 할당:
{% highlight python %}
a, b = c[:2]
{% endhighlight %}
- 슬라이스 할당:
{% highlight python %}
a = ["a", "b", "c", "d", "e", "f", "g", "h"]
print("Before :", a)
a[2:7] = [99, 22, 14]     # 할당의 길이가 달라도 됨
print("After: ", a)

>>>
Before: ["a", "b", "c", "d", "e", "f", "g", "h"]
After: ["a", "b", 99, 22, 14, "h"]
{% endhighlight %}
- 원본 리스트의 복사: Deep copy
{% highlight python %}
b = a[:]
assert b == a and b is not a    # 같은 내용을 담지만 다른 리스트 인스턴스
{% endhighlight %}
- 리스트의 할당: Shallow copy
{% highlight python %}
b = a
assert a is b                   # 같은 리스트 
{% endhighlight %}
