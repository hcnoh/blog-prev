---
layout: post
title: "WAY 20. 동적 기본 인수를 지정하려면 None과 docstring을 사용하자"
date: 2018-09-30 22:48:14
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 20. 동적 기본 인수를 지정하려면 None과 docstring을 사용하자'
---

## 비정적 타입의 키워드 인수
- 이벤트 발생 시각까지 포함해 로깅 메시지를 출력하는 예제
{% highlight python %}
def log(message, when=datetime.now()):
    print("%s: %s" % (when, message))

log("Hi there!")
sleep(0.1)
log("Hi again!")

>>>
2014-11-15 21:10:10.371432: Hi there!
2014-11-15 21:10:10.371432: Hi again!
{% endhighlight %}
