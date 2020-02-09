---
title: '[Tensorflow] Tensorflow 설치' 
excerpt: 아나콘다에 가상환경에서 Tensorflow 설치하기 
categories:
    - Machine Learning

tag:
    - Anaconda
    - Anaconda3
    - Tensorflow

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2020-02-07T15:00:00+09:00

toc: true   #Table Of Contents 목차 
toc_icon: "cog"
toc_sticky: true
---

## 텐서플로우(Tensorflow)

## 텐서플로우 설치

__1. 아나콘다 가상환경의 터미널에서 설치__

```
conda install tensorflow
```

![2.6-17](/assets/img/anaconda/2.6-17.png)


__2. 설치된 패키지 리스트 조회__

```
conda list
```

![2.6-13](/assets/img/anaconda/2.6-13.png)
.

__3. 주피터 노트북 설치 & 실행__

주피터 노트북 설치 

```
conda install jupyter notebook
```

주피터 노트북 실행

```
jupyter notebook
```

![2.6-14](/assets/img/anaconda/2.6-14.png)


__4. new > Python3__

주피터 노트북을 실행시키면 아래와 같은 화면이 나옵니다.

![2.6-15](/assets/img/anaconda/2.6-15.png)

__5. 코드 작성__

tensorflow 모듈이 잘 설치 되었는지 확인하기 위해 테스트 코드를 작성한 후 실행시켜 봅니다.
아래와 같은 결과가 나온다면 잘 설치된 것입니다.ㅎㅎ 

![2.6-16](/assets/img/anaconda/2.6-16.png)



## 참고 자료
> [Ohjinjin's DevLog - How to install 3rd party librarys on ANACONDA](https://ohjinjin.github.io/anaconda/anaconda-navigator/)