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
def normalize(numbers):
    total = sum(numbers)                    # 이터레이터 한 번 소모
    result = []
    for value in numbers:                   # 이미 순회가 끝난 이터레이터는 순회를 해도 결과가 나오지 않음
        percent = 100 * value / total
        result.append(percent)
    return result
    
def read_visits(data_path):
    with open(data_path) as f:
        for line in f:
            yield int(line)

it = read_visits("/tmp/my_numbers.txt")
percentages = normalize(it)
print(percentages)

>>>
[]
{% endhighlight %}
- 위의 예제에서 제너레이터의 반환 값에 `normalize`를 호출하면 아무 결과도 생성되지 않음
    - 이터레이터가 결과를 한 번만 생성하기 때문
    - 이미 `StopIteration` 예외를 일으킨 이터레이터나 제너레이터를 순회하면 어떤 결과도 얻을 수 없음
{% highlight python %}
it = read_visits("/tmp/my_numbers.txt")
print(list(it))
print(list(it))     # 이미 소진함

>>>
[15, 35, 80]
[]
{% endhighlight %}
- 이미 소진한 이터레이터를 순회하더라도 오류가 일어나지는 않음
- 많은 함수들이 결과가 없는 이터레이터와 결과가 있었지만 이미 소진한 이터레이터의 차이를 알려주지 않음

## 문제점 해결
- 입력 이터레이터를 명시적으로 소진하고 전체 콘텐츠의 복사본을 리스트에 저장하여 해결 가능
- 위의 예제와 동일하지만 입력 이터레이터를 방어적으로 복사하는 함수 예제
{% highlight python %}
def normalize_copy(numbers):
    numbers = list(numbers)     # 이터레이터를 복사
    total = sum(numbers)
    result = []
    for value in numbers:
        percent = 100 * value / total
        result.append(percent)
    return result

def read_visits(data_path):
    with open(data_path) as f:
        for line in f:
            yield int(line)

it = read_visits("/tmp/my_numbers.txt")
percentages = normalize(it)
print(percentages)

>>>
[11.538461538461538, 26.923076923076923, 61.53846153846154]
{% endhighlight %}
- 위의 예제는 이터레이터를 리스트로 복사하는 과정에서 메모리 소모가 클 수 있음
- 메모리 문제를 피하는 방법은 호출할 때마다 새 이터레이터를 반환하는 함수를 받게 하는 것
{% highlight python %}
def normalize_func(get_iter):
    total = sum(get_iter())         # 새 이터레이터
    result = []
    for value in get_iter():
        percent = 100 * value / total
        result.append(percent)
    return result

percentages = normalize_func(lambda: read_visits(path))     # 제너레이터를 호출하여 매번 새 이터레이터를 생성하는 람다 표현식을 넘겨줌
print(percentages)

>>>
[11.538461538461538, 26.923076923076923, 61.53846153846154]
{% endhighlight %}
- 위의 예제도 잘 돌아가기는 하지만 람다 함수를 넘겨주는 방법은 세련되지 못함
- 같은 결과를 얻을 수 있는 더 좋은 방법: 이터레이터 프로토콜을 구현한 새 컨테이너 클래스를 제공하는 것
