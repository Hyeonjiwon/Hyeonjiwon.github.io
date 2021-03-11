---
title: '[Etc] Vscode에 JAVA 개발 환경 설정' 
excerpt: "macOS에서 Vscode에 JAVA 개발 환경 설정하기"
categories:
    - Etc

tag:
    - JAVA
    - Vscode
    - macOS

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2021-03-11 T16:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true
---

## Intro

M1 macOS에서 VSCode로 JAVA를 사용할 수 있도록 개발 환경을 설정해보겠습니다. VSCode가 설치되어 있다는 가정하에 진행하였습니다.

## Install JDK 

[Java SE Downloads](https://www.oracle.com/kr/java/technologies/javase-downloads.html)로 들어가 JDK Download 버틀을 눌러줍니다. 

<img width="1117" alt="0" src="https://user-images.githubusercontent.com/47733530/110754220-e8564e00-828a-11eb-863f-0131a8598efe.png">

macOS Installer에서 Java SE 15.0.2 버전을 설치해줬습니다.

<img width="1117" alt="1" src="https://user-images.githubusercontent.com/47733530/110754239-ec826b80-828a-11eb-8180-7155ddfb8083.png">

다운로드 된 JDK 파일을 설치

<img width="831" alt="2" src="https://user-images.githubusercontent.com/47733530/110754244-edb39880-828a-11eb-91cc-91abfe2bc73a.png">

아래 명령어로 잘 설치되었는지 확인해줍니다. 

```
java --version
javac --version
```

<img width="682" alt="3" src="https://user-images.githubusercontent.com/47733530/110754248-eee4c580-828a-11eb-890c-2b96af2ea4a5.png">


## Java Extension install

VScode 의 Extension에서 java를 검색하면 가장 첫번째에 나오는 Java Extension Pack 을 설치해줍니다. 

<img width="1136" alt="4" src="https://user-images.githubusercontent.com/47733530/110754252-ef7d5c00-828a-11eb-82ad-0db7292b8dbd.png">


## 실행 해보기 

.java 파일을 만들고 코드를 작성해 준 뒤 오른쪽 플레이 버튼을 누르고 실행시켜줍니다.  

<img width="915" alt="5" src="https://user-images.githubusercontent.com/47733530/110754257-f015f280-828a-11eb-8eba-6aa08a690637.png">