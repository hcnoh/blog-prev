---
layout: post
title: "WAY 16. 리스트를 반환하는 대신 제너레이터를 고려하자"
date: 2018-09-27 20:5:43
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 16. 리스트를 반환하는 대신 제너레이터를 고려하자'
---

- 리스트를 반환하는 예제
{% highlight python %}
def index_words(text):
    result = []
    if text:
        result.append(0)
    for index, letter in enumerate(text):
        if letter == " ":
            result.append(index + 1)
    return result

address = "four score and seven years ago..."     # 샘플 입력이 적은 경우는 함수가 잘 동작
result = index_words(address)
print(result[:3])

>>>
[0, 5, 11]
{% endhighlight %}
- 위 예제의 문제점
  - 코드가 복잡하고 깔끔하지 않음
