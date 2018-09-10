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
- 파이썬3에서 문자 시퀀스를 나타내는 법?
1. bytes 인스턴스: raw 8 bits
2. str 인스턴스: 유니코드 문자
