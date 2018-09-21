---
layout: post
title: "WAY 13. try/except/else/finally에서 각 블록의 장점을 이용하자"
date: 2018-09-20 14:55:45
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 13. try/except/else/finally에서 각 블록의 장점을 이용하자'
---

## 파이썬 예외처리 과정
- 4번의 구분되는 시점
  - `try`, `except`, `else`, `finally`
- 각 블록들을 다양하게 조합하면 유용

## finally 블록
- 예외는 전달하고 싶지만, 예외가 발생해도 정리 코드를 실행하고 싶을 때
  - 사용 예시: 파일 핸들러를 제대로 종료하는 작업
{% highlight python %}
handle = open("/tmp/random_data.txt") # IOError가 일어날 수 있음
try:
    data = handle.read()  # UnicodeDecodeError가 일어날 수 있음
finally:
    handle.close()        # try 이후에 항상 실행
{% endhighlight %}
- `read` 메서드에서 발생한 예외는 항상 호출 코드까지 전달
- `close` 메서드 또한 `finally` 블록에서 실행되는 것이 보장
- 파일을 열 때 일어나는 예외는 `finally` 블록에서 처리하지 않아야 하므로 `try` 블록 앞에서 `open`을 호출해야 함

## else 블록
- 어떤 예외를 처리하고 어떤 예외를 전달할지를 명확하게 하고 싶을 때
- `try` 블록이 예외를 일으키지 않으면 `else` 블록이 실행

