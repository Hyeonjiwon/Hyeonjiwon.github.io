---
title: '[Etc] Mac OS 환경에서 Git 설치' 
excerpt: 'Git 설치와 Homebrow 설치'
categories:
    - Etc

tag:
    - Git 
    - Homebrow
    - Mac OS

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2021-02-22T16:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true
---


## 터미널 열기

- Launchpad로 실행

Launchpad > 기타 > 터미널 을 눌러 실행시킵니다.  

<img width="1440" alt="1" src="https://user-images.githubusercontent.com/47733530/108676347-6d233700-752b-11eb-909c-86df4e909e3f.png">

- Spotlight 검색으로 실행

command + space 를 눌러 Spotlight 검색 창에 terminal 또는 터미널을 입력한 후 실행 시킵니다. 

<img width="792" alt="2" src="https://user-images.githubusercontent.com/47733530/108676366-72808180-752b-11eb-96f1-43cc18a9714b.png">


## Homebrew 설치

맥OS 에 git을 설치하기에 앞서 Homebrew를 설치 합니다. Homebrew는 맥 OS 용 패키지 관리자 입니다. 

[Homebrew](https://brew.sh/)에 들어가 보면 설치 방법이 있습니다.

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

해당 문장을 터미널에 붙여 넣으면 Homebrew가 설치 됩니다.
Password를 입력하라고 나오면 맥 OS의 비밀번호를 입력해주면 설치가 완료 됩니다. 

<img width="682" alt="3" src="https://user-images.githubusercontent.com/47733530/108677715-6a294600-752d-11eb-9820-1c5c54171c4d.png">

<img width="682" alt="4" src="https://user-images.githubusercontent.com/47733530/108678236-2d118380-752e-11eb-828d-5d25dfceb13e.png">

위의 방법으로 Homewbrew 설치를 하고 git을 설치하려고 하니 

```
zsh: command not found: brew
```

라고 나왔습니다. 원인은 저는 M1 Mac을 사용하기 때문이였습니다. 

<br>

- M1 Mac 에서 HomewBrew 설치하는 방법

Finder > 터미널 정보 가져오기 > Rosetta를 사용하여 열기 활성화 

<img alt="5" src="https://user-images.githubusercontent.com/47733530/108679876-7d89e080-7530-11eb-82aa-8faf56e9101b.png">

<img alt="6" src="https://user-images.githubusercontent.com/47733530/108679888-8084d100-7530-11eb-8c11-c85319ca22ce.png">

설정한 터미널을 열고 아래 명령어를 입력하여 Homebrew 설치하면 됩니다. 

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

명령어로 잘 설치 되었는지 확인을 해주었습니다. 

```
brew help
```

<img width="682" alt="7" src="https://user-images.githubusercontent.com/47733530/108680314-11f44300-7531-11eb-95c3-746b027df0f2.png">


## Git 설치

Git은 분산 버전 관리 시스템(Distributed Version Control System, DVCS) 입니다. 

Homebrew를 설치하였으면 터미널에 다시 접속한 다음 

``` 
brew install git
```

을 입력해주면 git 설치가 완료됩니다.

``` 
git --version
```

명령어를 입력하여 잘 설치 되었는지 깃 버전을 확인합니다. 

<img width="682" alt="8" src="https://user-images.githubusercontent.com/47733530/108680569-5f70b000-7531-11eb-8b74-8adb02546e41.png">


## Git bash 사용하기 

- 오류발생 

```
zsh: command not found: code 
``` 

<img width="682" alt="9" src="https://user-images.githubusercontent.com/47733530/109114517-1fa00780-7781-11eb-9be9-f5454506ecd8.png">

- 해결방법

1.  VS Code 

2. Command Palette (command + shift + p) 

3. install 'code' command in PATH

<img width="555" alt="10" src="https://user-images.githubusercontent.com/47733530/109114530-23338e80-7781-11eb-9254-5b6e0ddd129c.png">

<p> 4. 터미널에서 code . 으로 확인 </p>

<img width="1016" alt="11" src="https://user-images.githubusercontent.com/47733530/109114909-a359f400-7781-11eb-8869-35c75f8d30d9.png">