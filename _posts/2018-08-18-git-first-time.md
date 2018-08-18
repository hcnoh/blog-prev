---
layout: post
title: "Git 처음 사용하기"
date: 2018-08-18 14:13:35
image: '/assets/img/'
description: 'Git을 처음 사용하며 느낀 어려운 점과 해결책들을 정리한 포스팅'
tags:
- git
categories:
- Development
twitter_text: 'Git 처음 사용하기'
---

최근 시작한 프로젝트로 Google DeepMind의 WAVENET 논문을 구현 작업을 시작했다. 프로젝트 진행은 GitHub를 통하여 백업 및 버전 관리를 할 계획인데 오늘 코드 작업 결과물인 `model.py`를 GitHub에 업로드하기 위하여 Git을 처음 사용하였고, 처음 사용하며 느낀 어려웠던 점이나 팁같은 것들을 한 번 정리해 보았다.

## Git Config 설정

일단 Git은 설치가 되어있는 상황에서 시작한다. 먼저 Git에게 나의 정보를 알려주는 과정인 Config 설정을 시작해보자. 다음의 명령어를 사용하여 Config 설정을 끝내자.
{% highlight bash %}
git config user.email "rhc0624@gmail.com"
git config user.name "hcnoh"
{% endhighlight %}
`git config -global user.name ~` 명령을ㄹ 사용하여도 되지만 현재 공용 서버를 활용 중이라 global로 선언하지는 않는 걸로 하였다. 이 부분은 좀 헷갈려서 추후에 확인하고 기록하도록 하겠다.

## GitHub Repository 생성

그 다음으로는 먼저 GitHub 상에서 `wavenet`이라는 이름으로 repo를 하나 만들어 준다. 이 이름은 현재 작업중인 프로젝트의 디렉토리 이름과 같다는 점을 확인하자.
현재 작업중인 디렉토리의 경로는 `~/wavenet`이다. 이 디렉토리 상에서 `git init` 명령을 통하여 이 디렉토리 `~/wavenet`이 로컬 git repository라고 선언한다.
