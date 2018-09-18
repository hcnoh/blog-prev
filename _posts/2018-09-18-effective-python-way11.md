---
layout: post
title: "WAY 11. 이터레이터를 병렬로 처리하려면 zip을 사용하자"
date: 2018-09-18 18:48:37
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 11. 이터레이터를 병렬로 처리하려면 zip을 사용하자'
---

파이썬에서 관련 객체로 구성된 리스트를 많이 사용한다.

## 리스트 컴프리헨션을 이용한 예제
- 파생 리스트의 아이템과 소스 리스트의 아이템은 서로의 인덱스로 연관
- 소스 리스트인 names의 길이만큼 순회하면 두 리스트를 병렬로 순회 가능
{% highlight python %}
names = ["Cecilia", "Lise", "Marie"]
letters = [len(n) for n in names]

longest_name = None
max_letters = 0

for i in range(len(names)):
    count = letters[i]
    if count > max_letters
{% endhighlight %}
