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
2014-11-15 21:10:10.371432: Hi there!       # 타임스탬프 동일하게 출력
2014-11-15 21:10:10.371432: Hi again!
{% endhighlight %}
- `datetime.now`는 함수를 정의할 때 딱 한 번만 실행: 타임스탬프 동일하게 출력
    - 이 코드를 담고 있는 모듈이 로드된 후에는 기본 인수인 `datetime.now`를 다시 평가하지 않음
- 결과가 기대한 대로 나오게 하려면 기본값을 `None`으로 설정하고 `docstring`(문서화 문자열)으로 실제 동작을 문서화하는 것이 관례
    - "WAY 49. 모든 함수, 클래스, 모듈에 docstring을 작성하자" 참고
    - 코드에서 `None`이 나타나면 알맞은 기본값을 할당하면 됨
{% highlight python %}
def log(message, when=None):
    """ Log a message with a timestamp.
    
    Args:
        message: Message to print.
        when: datetime of when the message occurred.
            Defaults to the present time.
    """
    when = datetime.now() if when is None else when
    print("%s: %s" % (when, message))

log("Hi there!")
sleep(0.1)
log("Hi again!")

>>>
2014-11-15 21:10:10.4772303: Hi there!      # 타임스탬프 다르게 출력
2014-11-15 21:10:10.5773395: Hi again!
{% endhighlight %}
