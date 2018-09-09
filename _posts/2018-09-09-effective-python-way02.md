---
layout: post
title: "이펙티브 파이썬 스터디 WAY 02 정리"
date: 2018-09-09 20:25:48
image: '/assets/img/'
description: '이펙티브 파이썬 코딩의 기술 책 스터디 정리'
tags:
- python
- effective python
categories:
- Development
twitter_text: '이펙티브 파이썬 스터디 WAY 02 정리'
---
이번 포스팅은 다음의 링크를 참고하여 작성하였다.
- [https://hashcode.co.kr/questions/963/%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%97%90%EC%84%9C-%EB%93%A4%EC%97%AC%EC%93%B0%EA%B8%B0%EB%8A%94-%ED%83%AD-%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EC%A4%91-%EC%96%B4%EB%8A%90%EA%B1%B8%EB%A1%9C-%ED%95%98%EC%8B%9C%EB%82%98%EC%9A%94](https://hashcode.co.kr/questions/963/%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%97%90%EC%84%9C-%EB%93%A4%EC%97%AC%EC%93%B0%EA%B8%B0%EB%8A%94-%ED%83%AD-%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EC%A4%91-%EC%96%B4%EB%8A%90%EA%B1%B8%EB%A1%9C-%ED%95%98%EC%8B%9C%EB%82%98%EC%9A%94)

## WAY 2. PEP 8 스타일 가이드를 따르자
- PEP 8이란?
1. 파이썬 개선 제안서 (Python Enhancement Proposal) #8
2. 파이썬 코드를 어떻게 구성할지 알려주는 스타일 가이드
3. 유지보수, 가독성을 위해서 일관성있는 스타일을 지키는 것이 중요

## PEP 8의 규칙 예시
- 화이트 스페이스: 공백이라고도 한다. 파이썬에서 공백은 문법적으로 의미가 있기 때문에 주의해야 한다.
1. 탭이 아닌 스페이스로 들여 쓴다. 하지만 탭을 사용해도 되며 한 코드 내에서는 일관성을 유지해야 한다.
2. 들여쓰기 수준은 스페이스 4개
3. 한 줄에 79자 이하
4. 길어서 다음 줄로 이어지면 들여쓰기 수준을 위해 스페이스 4개 사용
5. 파일 내에서 함수/클래스는 빈 줄 두 개로 구분
6. 클래스 내에서 메서드 사이는 빈 줄 하나로 구분
7. 리스트 인덱스, 함수 호출, 키워드 인수 할당에는 스페이스를 사용하지 않음
8. 변수 할당 앞뒤에 스페이스 하나만 사용:
{% highlight python %}
a = b
{% endhighlight %}
위의 스크립트에서 '=' 앞뒤로 스페이스 하나만 사용하라는 의미인 듯하다.

- 명명(Naming): 이 스타일을 따르면 코드를 읽을 때 각 이름에 대응하는 타입을 구별하기 쉬움
1. 함수, 변수, 속성은 lowercase_underscore 형식
2. Protected 인스턴스 속성은 _leading_underscore 형식
