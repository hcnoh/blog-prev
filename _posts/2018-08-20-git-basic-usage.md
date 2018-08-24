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
어떤 프로젝트를 여러 명의 개발자가 공동으로 작업하는 경우를 생각해보자. 어떤 개발자 A가 특정 소스코드를 작업하고 있을때 다른 개발자 B가 동시에 이 소스코드에서 작업을 수행하기 시작한다. A는 작업을 완료하여 저장하여 서버에 업로드를 하였고 B는 여전히 이전 소스코드에 작업을 하고 있다. B가 작업을 끝내고 업로드를 하는 순간 A가 작업한 내용은 지워지던가 아니면 중복되게 될 것이다. 따라서 이러한 공동 작업 환경에서는 버전 관리가 매우 중요한 이슈가 될 것이다. 이러한 프로젝트의 버전을 관리해주는 소프트웨어가 바로 Git이다.

## Git 작업의 구성 요소
Git 작업의 구성 요소는 크게 로컬 Repository와 온라인 Repository로 나뉘어진다. 온라인 Repository가 origin이 되어서 여러 명의 개발자들이 자신들의 로컬 Repository로 branch를 따와서 작업을 하여 자신만의 버전을 만든다. 작업을 끝낸 후에 프로젝트의 메인 디렉토리인 master branch에 자신들의 branch를 합친다.

## Git 초기 설정
일단 Git이 설치가 되었다면 자신의 로컬 컴퓨터에서 Git의 config를 설정함으로써 초기 설정을 수행할 수 있다. 이 작업을 위해서는 GitHub (현재 우리 연구소에서는 업무용으로 GitLab을 사용한다.)의 계정이 필요하다.  

다음의 명령어를 타이핑해보자.  
{% highlight bash %}
>>> git config --global user.email "rhc0624@gmail.com"
>>> git config --global user.name "hcnoh"
{% endhighlight %}
여기서 이메일과 이름이 GitHub 계정을 생성할 때 사용한 정보들과 일치한다는 점을 기억하자. 이러한 config 설정을 통해 commit하는 과정에서 매번 저런 정보들을 타이핑할 필요가 없을 것이다.

## 온라인 Repository 생성
Git으로 작업을 수행하기 위해서는 origin이 될 온라인 Repository의 생성이 선행되어야 한다. GitHub를 사용한다면 GitHub.com에 접속하여 `new repository page`로 들어가서 새로운 Repository를 생성한다. 일반적으로 Repository을 줄여서 repo라고 부른다.

`Initialize this repository with a README.`는 체크해도 되고 하지 않아도 된다. 큰 상관은 없다. 다만 처음 생성하는 경우에는 연습삼아서 체크해 보는 것이 좋을 것이다. 체크를 하고 repo를 생성하면 repo 내에 `Readme.md`파일이 같이 생성된다.

## 로컬 Repository 생성
이제 로컬에서 작업하기 위한 로컬 repo를 생성해야 한다. 현재 온라인 repo의 프로젝트 이름과 일치하는 디렉토리를 로컬에 만들어 준다.
{% highlight bash %}
>>> mkdir ~/wavenet
{% endhighlight %}
그 다음 방금 생성된 디렉토리가 로컬 repo라고 설정을 해줘야 한다. 먼저 방금 생성된 폴더로 이동한다.
{% highlight bash %}
>>> cd ~/wavenet
{% endhighlight %}
그 다음 `git init` 명령을 통해 현재 디렉토리를 로컬 repo로 설정한다.
{% highlight bash %}
>>> git init
Initialized empty Git repository in /home/hcnoh/wavenet/.git/
{% endhighlight %}
초기화가 제대로 되었음을 확인할 수 있다. 이제 현재 디렉토리인 `~/wavenet`은 wavenet 온라인 repo 작업을 위한 로컬 repo로 설정되었다.

## 작업 내용 추가
add => commit => push
