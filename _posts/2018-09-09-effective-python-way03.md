---
layout: post
title: "이펙티브 파이썬 스터디 WAY 03 정리"
date: 2018-09-10 10:15:52
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
categories:
- 이펙티브 파이썬 스터디
twitter_text: '이펙티브 파이썬 스터디 WAY 03 정리'
---

## WAY 3. bytes, str, unicode의 차이점을 알자
파이썬에서 문자 시퀀스를 나타내는 타입은 2가지 방식이 있다. 로 8비트(raw 8 bits) 값과 유니코드(Unicode) 문자가 그 2가지 방식이다. 파이썬3과 파이썬2에서는 각각 다른 방식을 사용하는데 그 방식의 차이를 정리해보도록 하자.

- 파이썬3에서 문자 시퀀스를 나타내는 방법
1. bytes 인스턴스: 로 8비트 값
2. str 인스턴스: 유니코드 문자

- 파이썬2에서 문자 시퀀스를 나타내는 방법
1. str 인스턴스: 로 8비트 값
2. unicode 인스턴스: 유니코드 문자

유니코드 문자를 로 8비트 값으로 변환하는 과정을 인코딩(encoding)이라고 한다. 가장 일반적으로 사용되는 인코딩 방식은 `utf-8`이다. 또한 인코딩의 반대 과정을 디코딩(decoding)이라고 한다. 주의할 점은 파이썬3의 str 인스턴스와 파이썬2의 unicode 인스턴스는 연관된 바이너리 인코딩이 따로 없다는 점이다. 파이썬 스크립트 상에서는 encode 메서드와 decode 메서드를 이용하여 인코딩/디코딩이 가능하다.
1. 인코딩 (encode 메서드): 유니코드 문자 => 로 8비트 값
2. 디코딩 (decode 메서드): 로 8비트 값 => 유니코드 문자

파이썬 프로그래밍을 할 때 스크립트 내부에서는 유니코드 문자 타입(파이썬3의 str/파이썬2의 unicode)을 사용하고, 인코딩에 관해서는 어떤 가정도 있어서는 안된다. 즉 유니코드 문자 타입으로 일관성있게 스크립트를 작성하라는 말. 이렇게 구현해놓아야 외부로 텍스트를 내보내거나 외부로부터 받아들일때 다른 텍스트 인코딩을 쉽게 수용 가능하다.
1. 파이썬 스크립트 내부에서는 유니코드 문자 타입만을 사용

파이썬의 두 가지 문자 타입으로 인하여 다음의 두 가지 문제가 생길 수 있다.
1. 인코딩된 로 8비트 값을 처리하려는 상황
2. 인코딩이 없는 유니코드 문자를 처리하려는 상황

이 두 경우에서 서로간의 변환 및 입력값과 스크립트 내부에서 사용되는 타입이 일치하게 하기 위해서는 로 `8비트 값 <=> 유니코드 문자`로의 변환이 가능한 메서드가 필요하다.

- 파이썬 3: str, bytes => bytes
{% highlight python %}
def to_str(bytes_or_str):
    if isinstance(bytes_or_str, bytes):
        value = bytes_or_str.decode("utf-8")
    else:
        value = bytes_or_str
    return value  # str 인스턴스
{% endhighlight %}
- 파이썬 3: str, bytes => str
{% highlight python %}
def to_bytes(bytes_or_str):
    if isinstance(bytes_r_str, str):
        value = bytes_or_str.encode("utf-8")
    else:
        value = bytes_or_str
    return value  # bytes 인스턴스
{% endhighlight %}
- 파이썬 2: unicode, str => unicode
{% highlight python %}
def to_unicode(unicode_or_str):
    if isinstance(unicode_or_str, str):
        value = unicode_or_str.decode("utf-8")
    else:
        value = unicode_or_str
    return value  # unicode 인스턴스
{% endhighlight %}
- 파이썬 2: unicode, str => str
{% highlight python %}
def to_str(unicode_or_str):
    if isinstance(unicode_or_str, unicode):
        value = unicode_or_str.encode("utf-8")
    else:
        value = unicode_or_str
    return value  # str 인스턴스
{% endhighlight %}
