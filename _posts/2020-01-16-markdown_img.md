---
title: '[Github] Git 블로그 글에 이미지 업로드' 
excerpt: Git 블로그에 포스팅에 이미지 업로드 & 경로 설정
categories:
- github
- markdown
- image

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2020-01-16T13:00:00+09:00

toc: true   #Table Of Contents 목차 
toc_sticky: true
---

---
## Intro
Git 블로그를 만들고 처음 포스팅을 하였을 때, 이미지를 업로드 하는 과정에서 약간의 문제가 있었습니다.
그래서 같은 문제로 헤매고 있으시는 분들이 있을것 같아서 조금이나마 도움이 되고자 본 포스팅을 작성합니다. 

## 이미지 업로드
### 마크다운 문법
Github 블로그는 지킬이라는 사이트 생성기를 통해 만들어 집니다. 지킬은 정적 사이트 생성기라고 합니다. 
또한 마크다운 문법을 통해 쉽고 깔끔한 포스팅을 할 수 있습니다. 

마크다운 문법을 이용하여 페이지에 이미지를 업로드 할 수 있습니다. 

[여기에](https://guides.github.com/features/mastering-markdown/)서 확인할 수 있듯이 이미지를 업로드하는 기본적인 방법은 아래와 같습니다.

```
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```

## TIP
사진이 왜 안나오는지 구글링을 하다가 이미지 경로 설정이 잘못되었다는 것을 알게되었습니다.
(아직까지 저게 왜 잘못된 경로인지 모르겠슴...)

### 이미지 경로 설정
1. 자신의 Github Repository에 들어간다.

2. Issues탭에 가면 있는 New issue를 누른다.
![1](https://user-images.githubusercontent.com/47733530/72496134-12210a00-386c-11ea-80a9-d22f01b59af8.png)

3. 이미지 파일을 textbox에 끌어서 놓는다. 또는 붙여 넣기로 첨부 한다. 
![3](https://user-images.githubusercontent.com/47733530/72496141-16e5be00-386c-11ea-92eb-cdffc77d75ca.png)

4. 마크다운 링크 문법으로 업로드 된 이미지 주소를 복사하여 md파일에 붙여넣는다. 
![4](https://user-images.githubusercontent.com/47733530/72496147-18af8180-386c-11ea-8c9a-dbcf36153e8a.png)

__commit 하고 결과 확인__



### 이미지 사이즈 조절 
이미지 크기가 너무 커서 크기를 조절 할 수 있는지 찾아 보았습니다.
이미지 크기를 조절하는 방법은 몇가지 방법이 있지만 두가지만 정리하여 보았습니다. 

- '{: width=" " height=" "}' 추가하기

```
![GitHub Logo](/images/logo.png){: width="50" height="100"}
```

- html의 <img> 태그 사용하기

```
<img src="/images/logo.png" width="50%" height="50%">
```

### 이미지 정렬
이미지를 가운데로 정렬시키는 방법도 사이즈를 조절하는 방법과 마찬가지로 두가지 방법이 있습니다.

## 결과
결과 이쁘게 정렬된 모습을 확인할 수 있습니다. ㅎㅎ
![결과](https://user-images.githubusercontent.com/47733530/72496152-1b11db80-386c-11ea-87c5-121d8a4ef7fa.png)