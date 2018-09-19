---
layout: post
title: "WAY 12. for와 while 루프 뒤에는 else 블록을 쓰지 말자"
date: 2018-09-19 10:15:35
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: 'WAY 12. for와 while 루프 뒤에는 else 블록을 쓰지 말자'
---

파이썬의 루프는 다른 프로그래밍 언어와는 다르게 루프에서 반복되는 내부 블록 바로 다음에 `else` 블록을 둘 수 있는 기능이 있다. 이 `else` 블록을 사용함에 있어서 주의해야 할 사항들을 이번 장에서 정리한다.

## else 블록의 특징
- 루프가 종료되자마자 바로 실행:
  - 루프가 완료되어야만 실행되는 것!
  - 루프 내에서 `break` 문을 사용해야만 `else` 블록을 건너뛸 수 있음
{% highlight python %}
for i in range(3):
    print("Loop %d" % i)
    if i == 1:
        break
else:
    print("Else block!")

>>>
Loop 0
Loop 1
{% endhighlight %}
- 빈 시퀀스를 처리하는 루프문에서도 `else` 블록이 즉시 실행
{% highlight python %}
for x in []:
    print("Never runs")
else:
    print("For Else block!")

>>>
For Else block!
{% endhighlight %}
- `while` 루프가 처음부터 거짓인 경우에도 실행
{% highlight python %}
while False:
    print("Never runs")
else:
    print("While Else block!")

>>>
While Else block!
{% endhighlight %}
