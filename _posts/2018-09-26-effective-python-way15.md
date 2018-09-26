---
layout: post
title: "WAY 15. 클로저가 변수 스코프와 상호 작용하는 방법을 알자"
date: 2018-09-26 19:17:19
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 15. 클로저가 변수 스코프와 상호 작용하는 방법을 알자'
---

- 리스트 정렬 예제
  - 특정 그룹의 숫자들이 먼저 오도록 우선순위를 매기는 경우:
    - `sort` 메서드에 헬퍼 함수를 `key` 인수로 넘기는 방법
{% highlight python %}
def sort_priority(values, group):
    def helper(x):
        if x in group:
            return (0, x)
        return (1, x)
    values.sort(key=helper)

numbers = [8, 3, 1, 2, 5, 4, 7, 6]
group = {2, 3, 5, 7}
sort_priority(numbers, group)
print(numbers)

>>>
[2, 3, 5, 7, 1, 4, 6, 8]
{% endhighlight %}

## 위의 정렬 예제가 동작하는 이유
1. 파이썬은 클로저(closure)를 지원
2. 함수는 파이썬에서 일급 객체(first-class object)
3. 파이썬에는 튜플을 비교하는 특정한 규칙 존재
