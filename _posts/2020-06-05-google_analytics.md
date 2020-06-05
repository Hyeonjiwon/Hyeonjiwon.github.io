---
title: '[Etc] 구글 애널리틱스(Google Analytics)'
excerpt: "구글 애널리틱스(Google Analytics)로 GitHub Pages 블로그에 통계 분석 기능 적용하기"
categories:
    - Etc

tag:
    - Google
    - Google Analytics
    - mininal-mistake
    - Jekyll theme
    - GitHub Pages
    - Git Page

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2020-06-05T12:00:00+09:00

toc: true   #Table Of Contents 목차

toc_sticky: true
---

## Intro
[Google Search Console 등록](https://hyeonjiwon.github.io/etc/search_console/)에 이어서 Google Analytics에 블로그를 등록하여 통계 분석 서비스를 사용해 보도록 하겠습니다. jekyll 테마마다 적용 방법이 다른데 저는 Minimal Mistake Jekyll theme 테마를 사용하고 있습니다. 

## Google Analytics
구글 애널리틱스(Google Analytics)는 내 사이트 및 앱의 사용자가 콘텐츠에 어떻게 참여하고 있는지 웹 사이트 트랙픽을 추적하고 분석해줍니다. 현재 가장 널리 사용되는 웹 분석 서비스 입니다. 웹 로그 분석은 트래픽 소스에 대한 정보와 함께 사이트를 사용하는 개인의 세션 지속 시간, 세션 당 페이지 수, 이탈률 등과 같은 웹 사이트 활동을 추적하는데 사용됩니다.  

## Google Analytics 등록

구글 서치 콘솔에 블로그를 등록하는 과정입니다.

먼저 본인의 구글 계정으로 로그인 한 후, [Google Analytics](https://analytics.google.com/)에 접속하여 줍니다.


![0](https://user-images.githubusercontent.com/47733530/83832969-cb05b980-a725-11ea-87d7-400a5ab8d909.png)

![1](https://user-images.githubusercontent.com/47733530/83832972-cc36e680-a725-11ea-80f0-9d22bc6ebad7.png)

![2](https://user-images.githubusercontent.com/47733530/83832974-cc36e680-a725-11ea-8a3e-396e85876a17.png)

![3](https://user-images.githubusercontent.com/47733530/83833037-f2f51d00-a725-11ea-81a4-5fae52899797.png)

## _config.yml 파일 설정

_config.yml 파일에서 설정을 해줍니다. provider에 google을 입력해주고 tracking_id에 본인의 추적 ID 를 입력해줍니다. 

![4](https://user-images.githubusercontent.com/47733530/83832975-cccf7d00-a725-11ea-89ac-b767379d1cd4.png)

추적 ID는 관리 > 속성 > 추적 정보 > 추적 코드에 있습니다. 

```yaml
# Analytics
analytics:
  provider               : "google" 
  google:
    tracking_id          : "tracking_id"
    anonymize_ip         : fasle 
```