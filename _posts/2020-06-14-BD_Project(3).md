---
title: '[빅데이터] 텀 프로젝트(3) - 데이터 세트 연산2' 
excerpt: '사용자 정의 함수와 데이터 캐싱'
categories:
    - Big Data

tag:
    - BigData
    - hadoop
    - spark
    - Zeppelin
    - TermProject

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2020-06-14T23:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true
---

## Intro
제플린 노트북에서 진행하는 데이터 세트 연산 실습 내용 입니다. 해상 조난 사고에 대한 데이터세트에 사용자 함수를 적용해보고 캐싱해보는 실습입니다. 

## 데이터세트 캐싱

![슬라이드22](https://user-images.githubusercontent.com/47733530/84595183-88fd1600-ae91-11ea-81a0-893fbe49ca94.PNG)
![슬라이드23](https://user-images.githubusercontent.com/47733530/84595186-8f8b8d80-ae91-11ea-902b-88ec281276b2.PNG)
![슬라이드24](https://user-images.githubusercontent.com/47733530/84595187-90bcba80-ae91-11ea-8364-6d107b918d0c.PNG)
![슬라이드25](https://user-images.githubusercontent.com/47733530/84595189-91555100-ae91-11ea-886d-f93863f0c2e5.PNG)
![슬라이드26](https://user-images.githubusercontent.com/47733530/84595190-91ede780-ae91-11ea-856d-1bf066792781.PNG)
![슬라이드27](https://user-images.githubusercontent.com/47733530/84595192-91ede780-ae91-11ea-9e6a-2cf90bce87ed.PNG)
![슬라이드28](https://user-images.githubusercontent.com/47733530/84595193-92867e00-ae91-11ea-909d-3e4405bcc278.PNG)
![슬라이드29](https://user-images.githubusercontent.com/47733530/84595196-92867e00-ae91-11ea-898b-5ecad4c192e7.PNG)

## 사용자 정의 함수

![슬라이드30](https://user-images.githubusercontent.com/47733530/84595197-931f1480-ae91-11ea-943a-77d174236cd3.PNG)
![슬라이드31](https://user-images.githubusercontent.com/47733530/84595198-93b7ab00-ae91-11ea-9afa-daab3b11c46a.PNG)
![슬라이드32](https://user-images.githubusercontent.com/47733530/84595199-93b7ab00-ae91-11ea-84f4-3f8bd3a510f7.PNG)
![슬라이드33](https://user-images.githubusercontent.com/47733530/84595200-94504180-ae91-11ea-8dfd-eb90a20592bb.PNG)
![슬라이드34](https://user-images.githubusercontent.com/47733530/84595201-94504180-ae91-11ea-91b9-fbdf44cf7d14.PNG)
![슬라이드35](https://user-images.githubusercontent.com/47733530/84595202-94e8d800-ae91-11ea-8d00-1e95265b26a3.PNG)
![슬라이드36](https://user-images.githubusercontent.com/47733530/84595204-94e8d800-ae91-11ea-83f5-54d723820d7b.PNG)
![슬라이드37](https://user-images.githubusercontent.com/47733530/84595205-95816e80-ae91-11ea-9d5e-45a45c4422f8.PNG)
![슬라이드38](https://user-images.githubusercontent.com/47733530/84595206-961a0500-ae91-11ea-8c79-94e3c065bd46.PNG)
![슬라이드39](https://user-images.githubusercontent.com/47733530/84595207-961a0500-ae91-11ea-8f8e-03bb687469db.PNG)
![슬라이드40](https://user-images.githubusercontent.com/47733530/84595208-96b29b80-ae91-11ea-9f57-3e543fb62e4b.PNG)
![슬라이드41](https://user-images.githubusercontent.com/47733530/84595209-96b29b80-ae91-11ea-8ce3-0cdc9c05ccf3.PNG)
![슬라이드42](https://user-images.githubusercontent.com/47733530/84595210-974b3200-ae91-11ea-8357-bb0199457dd7.PNG)
![슬라이드43](https://user-images.githubusercontent.com/47733530/84595211-974b3200-ae91-11ea-9979-6fce711f4a94.PNG)
![슬라이드44](https://user-images.githubusercontent.com/47733530/84595212-97e3c880-ae91-11ea-905b-e38ddb9f4412.PNG)
![슬라이드45](https://user-images.githubusercontent.com/47733530/84595215-97e3c880-ae91-11ea-8328-ed755c417510.PNG)
![슬라이드46](https://user-images.githubusercontent.com/47733530/84595216-987c5f00-ae91-11ea-902a-867b586903df.PNG)
![슬라이드47](https://user-images.githubusercontent.com/47733530/84595217-9914f580-ae91-11ea-94bd-e3abca46baff.PNG)
![슬라이드48](https://user-images.githubusercontent.com/47733530/84595218-9914f580-ae91-11ea-82d5-830d3e41d849.PNG)
![슬라이드49](https://user-images.githubusercontent.com/47733530/84595219-99ad8c00-ae91-11ea-9b78-236acdfd934f.PNG)
![슬라이드50](https://user-images.githubusercontent.com/47733530/84595220-9a462280-ae91-11ea-86f5-434cbd78da0c.PNG)
![슬라이드51](https://user-images.githubusercontent.com/47733530/84595221-9adeb900-ae91-11ea-9b5d-27603abd5844.PNG)
![슬라이드52](https://user-images.githubusercontent.com/47733530/84595224-9adeb900-ae91-11ea-8817-c4251f3d616a.PNG)
![슬라이드53](https://user-images.githubusercontent.com/47733530/84595226-9b774f80-ae91-11ea-8394-0a9a8649024a.PNG)

<br>

## 참고 자료
