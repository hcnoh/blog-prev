---
layout: post
title: "WAY 17. 인수를 순회할 때는 방어적으로 하자"
date: 2018-09-27 20:16:38
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 17. 인수를 순회할 때는 방어적으로 하자'
---

## 파라미터로 객체의 리스트를 받는 함수 예제
- 정규화 함수
    - 미국 텍사스주의 여행자 수를 분석
    - 데이터 집합은 각 도시의 방문자 수, 각 도시에서 전체 여행자 중 몇 퍼센트를 받아들이는지 확인
{% highlight python %}
def normalize(numbers):
    total = sum(numbers)
    result = []
    for value in numbers:
        percent = 100 * value / total
        result.append(percent)
    return result

visits = [15, 35, 80]
percentages = normalize(visits)
print(percentages)

>>>
[11.538461538461538, 26.923076923076923, 61.53846153846154]
{% endhighlight %}
- 리스트를 확대하려면 텍사스주의 모든 도시가 들어 있는 파일에서 데이터를 읽어야 함:
    - 이 작업을 수행하는 제너레이터를 정의
{% highlight python %}
def read_visits(data_path):
    with open(data_path) as f:
        for line in f:
            yield int(line)
{% endhighlight %}
