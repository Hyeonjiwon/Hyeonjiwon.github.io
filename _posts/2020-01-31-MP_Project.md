---
title: '[마이크로프로세서] 스마트 횡단보도' 
excerpt: 3-2 마이크로프로세서 텀프로젝트
categories:
- Project

tag:
    - HTML
    - CSS
    - Android Studio
    - Amazon LightSail
    - Apache
    - PHP
    - MySQL
    - JAVA
    - Arduino
    - Raspberry Pi

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2020-01-31T16:00:00+09:00

toc: true   #Table Of Contents 목차 
toc_sticky: true
---

## Intro
3학년 2학기 마이크로프로세서 과목을 수강하면서 진행한 텀프로젝트 입니다.
시골이나 작은 도시에서는 밤 11시 12시만 되면 신호등이 모두 꺼지거나 차량 신호등만 주황색 점멸 신호로 바뀝니다. 제가 사는 곳에서도 그랬었는데 밤늦은 시간 횡단보도를 건너고 있으면 멀리서 차가 너무 빠르게 와서 사고가 날까봐 두려웠습니다. 또한 보행자 사망사고의 52.9%가 횡단보도에서 발생한다고 합니다. 그래서 어떻게 하면 밤 늦은시간 주황색 차량 점멸신호를 대신해서 안전하게 보행자들이 횡단보도를 건널 수 있을지 고민해보다가 스마트 횡단보도라는 주제로 프로젝트를 시작하였습니다.

## 설계
사용센서와 모듈은 보행자를 인식하기 위한 초음파센서(HC-SR04), 신호위반 차량을 촬영하기 위한 카메라 모듈(Pi Camera 8MP), 자동차를 인식하기 위한 레이저 모듈과 조도 센서를 사용하였습니다.

사용 보드는 라즈베리파이3(Raspberry Pi 3)과 아두이노 메가(Arduino Mega)를 이용하였습니다. 라즈베리파이와 아두이노는 서로 시리얼(Serial) 통신을 하며 데이터를 주고 받습니다. 

## 구현
__Front-End__

프론트엔드(Front-End)는 HTML(HyperText Markup Language)로 웹 문서를 작성하였습니다. <br>
CSS(Cascading Style Sheet)는 부트스트랩(Bootstrap)을 사용하였습니다. <br>

안드로이드 어플을 개발하면서 어플의 화면은 XML(eXtensible Markup Language)로 작성하여 디자인 하였습니다.

__Back_End__

백엔드(Back-End)에서 웹 서버(Web Server)는 아마존 라이트세일(Amazon LighSail)을 사용하였습니다. 라이트세일은 아마존에서 제공하고 있는 가상 사설 서버 호스팅 서비스 입니다. 인스턴스를 생성한 후, 고정 IP를 할당 받았습니다. 

WinSCP(Window Secure CoPy)를 이용하여 가상 서버의 파일을 관리하였습니다. 그 중 PHP 파일들을 작성하고 관리하였습니다. 
WinSCP는 Widow용 그래픽 유저 인터페이스 SFTP 및 FTP 클라이언트 프로그램 입니다. 

데이터베이스는 관계형 데이터베이스 관리 시스템인 MySQL을 사용하였는데, PuTTY를 이용하여 MySQL 서버에 접속하였습니다.

PHP와 MySQL 서버를 연결하여 일일 횡단보도의 정보가 담긴 CrossWalk 테이블의 데이터를 조회한 후, JSON 포맷으로 가공하여 Android에서 사용하였습니다. 

HTTP을 이용하여 고정 IP에서 JSON 포맷으로 변경된 CrossWalk 테이블의 데이터를 조회하였습니다.

__Sensor & Module Control__

가장 핵심적인 센서와 모듈 제어는 아두이노와 라즈베리 파이를 통해 구현하였습니다. 아두이노는 초음파센서의 값을 받아와 거리로 변환한 후, 사람이 횡단보도 앞에 왔는지 오지 않았는지를 판단합니다. 횡단 보도 신호가 빨간불로 점등되었다가 다시 돌아온 경우, 즉 보행자가 길을 완전히 건넌 경우 카운트를 하여 라즈베리파이로 값을 전달합니다. 차량 신호등이 빨간불 일 때,레이저와 조도 센서가 신호위반 차량을 감지하기 위해 작동됩니다. 조도 센서의 값이 일정 값을 넘으면 그 값을 라즈베리파이로 전달합니다. 또한, 상황에 맞게 차량 신호등과 횡단보도의 LED를 조절합니다. 

라즈베리파이는 아두이노에게서 받은 카운트 값을 데이터베이스에 insert 합니다. 아두이노에서 전달받은 조도 센서 값이 있으면 운전자 차량을 신호위반으로 간주하여 사진을 촬영합니다. 

## Project

![슬라이드1](https://user-images.githubusercontent.com/47733530/73722394-bc07fe00-4769-11ea-8083-9a3d237ba5dd.PNG)

<br>

![슬라이드2](https://user-images.githubusercontent.com/47733530/73522085-fb250f00-444a-11ea-9cc1-05922ecd2a75.PNG)

<br>

![슬라이드3](https://user-images.githubusercontent.com/47733530/73522086-fbbda580-444a-11ea-80f9-73108d1324f7.PNG)
![슬라이드4](https://user-images.githubusercontent.com/47733530/73522087-fbbda580-444a-11ea-9251-e0940d696422.PNG)
![슬라이드5](https://user-images.githubusercontent.com/47733530/73522088-fbbda580-444a-11ea-840c-ab26e66b6c54.PNG)
![슬라이드6](https://user-images.githubusercontent.com/47733530/73522089-fbbda580-444a-11ea-951b-fa122dc95f19.PNG)
![슬라이드7](https://user-images.githubusercontent.com/47733530/73522091-fc563c00-444a-11ea-8630-490106d970c1.PNG)
![슬라이드8](https://user-images.githubusercontent.com/47733530/73522124-0bd58500-444b-11ea-9104-6657db81c475.PNG)
![슬라이드9](https://user-images.githubusercontent.com/47733530/73522125-0bd58500-444b-11ea-827a-53b98884c204.PNG)
![슬라이드10](https://user-images.githubusercontent.com/47733530/73522126-0c6e1b80-444b-11ea-8c2d-21670e02ab97.PNG)
![슬라이드11](https://user-images.githubusercontent.com/47733530/73522128-0c6e1b80-444b-11ea-9b3a-6a12f7602166.PNG)
![슬라이드12](https://user-images.githubusercontent.com/47733530/73522130-0c6e1b80-444b-11ea-98b2-4972465ece35.PNG)
![슬라이드13](https://user-images.githubusercontent.com/47733530/73522131-0c6e1b80-444b-11ea-8721-32fe00868735.PNG)
![슬라이드14](https://user-images.githubusercontent.com/47733530/73522133-0d06b200-444b-11ea-9357-d0ba4608af7b.PNG)
![슬라이드15](https://user-images.githubusercontent.com/47733530/73522134-0d06b200-444b-11ea-9be8-5d27d090bd5c.PNG)
![슬라이드16](https://user-images.githubusercontent.com/47733530/73522136-0d06b200-444b-11ea-981f-d60adacdefcc.PNG)
![슬라이드17](https://user-images.githubusercontent.com/47733530/73522138-0d06b200-444b-11ea-8c2c-32466c2fd49f.PNG)
![슬라이드18](https://user-images.githubusercontent.com/47733530/73522139-0d9f4880-444b-11ea-86cd-0ca8ef77349c.PNG)
![슬라이드19](https://user-images.githubusercontent.com/47733530/73522141-0d9f4880-444b-11ea-9095-2c2effff2035.PNG)

<br>

![슬라이드20](https://user-images.githubusercontent.com/47733530/73522142-0d9f4880-444b-11ea-9a56-4adcd2b401c2.PNG)
![슬라이드21](https://user-images.githubusercontent.com/47733530/73522144-0d9f4880-444b-11ea-9a98-fe44f41d0f3e.PNG)
![슬라이드22](https://user-images.githubusercontent.com/47733530/73522145-0e37df00-444b-11ea-9c7a-6122c1338725.PNG)
![슬라이드23](https://user-images.githubusercontent.com/47733530/73522148-0e37df00-444b-11ea-9508-2daaa34dd1bd.PNG)
![슬라이드24](https://user-images.githubusercontent.com/47733530/73522150-0e37df00-444b-11ea-96d9-508b8bbdd008.PNG)
![슬라이드25](https://user-images.githubusercontent.com/47733530/73522151-0e37df00-444b-11ea-966f-6d7e213b6f06.PNG)
![슬라이드26](https://user-images.githubusercontent.com/47733530/73522152-0ed07580-444b-11ea-82af-e4415be34b0b.PNG)
![슬라이드27](https://user-images.githubusercontent.com/47733530/73522153-0ed07580-444b-11ea-8f6f-5d3c2d44f453.PNG)
![슬라이드28](https://user-images.githubusercontent.com/47733530/73522154-0ed07580-444b-11ea-9b5e-b071fafebc61.PNG)
![슬라이드29](https://user-images.githubusercontent.com/47733530/73522156-0ed07580-444b-11ea-9603-950f8d93cebd.PNG)
![슬라이드30](https://user-images.githubusercontent.com/47733530/73522157-0f690c00-444b-11ea-9cfd-f3919dbf0a27.PNG)
![슬라이드31](https://user-images.githubusercontent.com/47733530/73522158-0f690c00-444b-11ea-9b59-da3243d1ccd0.PNG)

<br>

![슬라이드32](https://user-images.githubusercontent.com/47733530/73522159-0f690c00-444b-11ea-9b23-5c04e621f99c.PNG)
![슬라이드33](https://user-images.githubusercontent.com/47733530/73522161-0f690c00-444b-11ea-93b7-8c810b017aeb.PNG)
![슬라이드34](https://user-images.githubusercontent.com/47733530/73522162-1001a280-444b-11ea-9782-ba4f49ad07cf.PNG)
![슬라이드35](https://user-images.githubusercontent.com/47733530/73522163-1001a280-444b-11ea-88dd-dffa3c806da9.PNG)
![슬라이드36](https://user-images.githubusercontent.com/47733530/73522164-1001a280-444b-11ea-94e9-95ceedbc68f5.PNG)
![슬라이드37](https://user-images.githubusercontent.com/47733530/73522165-109a3900-444b-11ea-9bcb-9423dc028dcb.PNG)
![슬라이드38](https://user-images.githubusercontent.com/47733530/73522166-109a3900-444b-11ea-9461-d95a7cbec54e.PNG)

## 결과영상

[![결과](https://www.youtube.com/watch?v=_eKLK-5hce8/1.jpg)](https://www.youtube.com/watch?v=_eKLK-5hce8)

▲ 결과 영상 클릭
