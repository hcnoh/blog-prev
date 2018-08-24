---
layout: post
title: "Git 기본 사용법"
date: 2018-08-20 19:7:44
image: '/assets/img/'
description: 'Git을 사용하기 위한 기초개념 및 사용법 정리'
tags:
- git
categories:
- Development
twitter_text: 'Git 기본 사용법'
---

저번 Git 포스팅을 통해서 Git을 맨 처음 사용하였다면 이번에는 Git을 사용하기 위하여 필요한 기초개념 및 사용법들을 정리하여 필요할때 찾아볼 수 있도록 포스팅을 계획하였다. 링크: [https://hcnoh.github.io/git-first-time/](https://hcnoh.github.io/git-first-time/)

이번 포스팅은 다음의 링크들을 참고하여 작성하였다:

[https://rogerdudler.github.io/git-guide/index.ko.htm](https://rogerdudler.github.io/git-guide/index.ko.html)
[https://nolboo.kim/blog/2013/10/06/github-for-beginner/](https://nolboo.kim/blog/2013/10/06/github-for-beginner/)

## Git이란?
어떤 프로젝트를 여러명의 개발자가 공동으로 작업하는 경우를 생각해보자. 어떤 개발자 A가 특정 소스코드를 작업하고 있을때 다른 개발자 B가 동시에 이 소스코드에서 작업을 수행하기 시작한다. A는 작업을 완료하여 저장하여 서버에 업로드를 하였고 B는 여전히 이전 소스코드에 작업을 하고있다. B가 작업을 끝내고 업로드를 하는 순간 A가 작업한 내용은 지워지던가 아니면 중복되게 될 것이다. 따라서 이러한 공동 작업 환경에서는 버전 관리가 매우 중요한 이슈가 될 것이다. 이러한 프로젝트의 버전을 관리해주는 소프트웨어가 바로 Git이다.

## 작업 내용 추가
add => commit => push
