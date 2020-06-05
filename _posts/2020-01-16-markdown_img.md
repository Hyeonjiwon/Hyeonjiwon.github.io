---
title: '[Blog] GitHub Pages 블로그 이미지 업로드' 
excerpt: 마크다운 문법으로 이미지 업로드 하기
categories:
    - Blog

tag:
    - Blog
    - Git
    - Git Page
    - Markdown

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2020-01-16T13:00:00+09:00

toc: true   #Table Of Contents 목차 
toc_sticky: true
---

---
## Intro
Git 블로그를 만들고 처음 포스팅을 하였을 때, 이미지 경로 설정을 잘못해주어서 페이지에 이미지가 나오지 않았습니다. 그래서 경로를 비교적 쉽게 설정하는 방법을 정리해 보았습니다. 

<br>

## 이미지 업로드 
### 마크다운 문법
Github 블로그는 지킬 이라는 사이트 생성기를 통해 만들어집니다. 지킬은 정적 사이트 생성기라고 합니다. 
또한 마크다운 문법을 통해 쉽고 깔끔한 포스팅을 할 수 있습니다. 

마크다운 문법을 이용하여 페이지에 이미지를 업로드 할 수 있습니다. 

[여기에](https://guides.github.com/features/mastering-markdown/)서 확인할 수 있듯이 이미지를 업로드하는 기본적인 방법은 아래와 같습니다.

```
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```

<br>

## TIP
위와 같은 방법으로 경로를 지정해 줄 수 있지만 조금 더 쉬운 방법(?)인 것 같아서 정리해보았습니다.

<br>

### 이미지 경로 설정
1. 자신의 Github Repository에 들어간다.

2. Issues탭에 가면 있는 New issue를 누른다.
![1](https://user-images.githubusercontent.com/47733530/72496134-12210a00-386c-11ea-80a9-d22f01b59af8.png)

3. 이미지 파일을 textbox에 끌어서 놓는다. 또는 붙여넣기로 첨부한다. 
![3](https://user-images.githubusercontent.com/47733530/72496141-16e5be00-386c-11ea-92eb-cdffc77d75ca.png)

4. 마크다운 링크 문법으로 업로드된 이미지 주소를 복사하여 md파일에 붙여넣는다. 
![4](https://user-images.githubusercontent.com/47733530/72496147-18af8180-386c-11ea-8c9a-dbcf36153e8a.png)

__commit하고 결과 확인__
![5](/assets/img/5.png)

<br>

### 이미지 사이즈 조절 
이미지 크기가 너무 커서 크기를 조절 할 수 있는지 찾아보았습니다.
이미지 크기를 조절하는 방법은 몇 가지 방법이 있지만 두 가지만 정리하여 보았습니다. 

- 이미지를 삽입하는 문장 뒤에 {: width=" " height=" "} 추가하기

```
![GitHub Logo](/images/logo.png){: width="50%" height="50%"}
```

- html의 <img> 태그 사용하기

```
<img src="/images/logo.png" width="50%" height="50%">
```

<br>

### 이미지 정렬
이미지를 가운데로 정렬시키는 방법도 사이즈를 조절하는 방법과 마찬가지로 두가지 방법이 있습니다.

- css 파일을 만들고 가운데 정렬 속성을 부여한 후, 이미지에 적용 

```
.center {
    display : block;
    maring : auto;
}
```
그 후, 마크다운 파일에서 이미지에 적용

```
![GitHub Logo](/images/logo.png){: width="50%" height="50%"0}{: .center}
```

- html의 &lt;center&gt; 기능을 이용

```
<center><img src="/images/logo.png" width="50%" height="50%"></center>
```

개인적으로 두번째 방법이 더 간편한것 같아 두번째 방법을 추천드립니다. ㅎ 

<br>

## 결과
[결과 페이지](https://hyeonjiwon.github.io/git/git%20%EB%AA%85%EB%A0%B9%EC%96%B4/git/)에서 이쁘게 정렬된 모습을 확인할 수 있습니다. ㅎㅎ

![결과](https://user-images.githubusercontent.com/47733530/72496152-1b11db80-386c-11ea-87c5-121d8a4ef7fa.png)