---
layout: post
title: "WAY 8. 리스트 컴프리헨션에서 표현식을 두 개 넘게 쓰지 말자"
date: 2018-09-16 22:58:3
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 8. 리스트 컴프리헨션에서 표현식을 두 개 넘게 쓰지 말자'
---

## 리스트 컴프리헨션의 다중 루프
- 리스트 컴프리헨션의 다중 루프 예제
{% highlight python %}
matrix = [[1, 2, 3], [4, 5, 6]]
flat = [x for row in matrix for x in row]
print(flat)

>>>
[1, 2, 3, 4, 5, 6]
{% endhighlight %}
- 입력 리스트 레이아웃을 두 레벨로 중복하여 구성
{% highlight python %}
matrix = [[1, 2, 3], [4, 5, 6]]
squared = [[x**2 for x in row] for row in matrix]
print(squared)

>>>
[[1, 4, 9], [16, 25, 36]]
{% endhighlight %}
