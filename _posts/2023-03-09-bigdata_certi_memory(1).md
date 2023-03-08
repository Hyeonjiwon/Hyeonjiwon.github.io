---
title: '[자격증] 정형 Data 수집 (빅공남 암기 - 1과목 : 빅데이터 이해)' 
excerpt: '빅데이터분석기사 - 필기'
categories:
    - Certification

tag:
    - Certification  
    - Bigdata
    - 빅데이터분석기사

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2023-03-09T00:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true
---


# 1-3 데이터 수집 및 저장 이해
## 정형 Data 수집
- FTP (File Transfer Protocol) 
  - 인터넷을 통한 파일 송수신을 위해 고안된 서비스
  - TCP/IP 기반 프로토콜
  - 장점 : www. 방식보다 빠르게 정보 송수신
  - 단점 : 빠른 전송이 목적이기에 스트리밍 불가능, 서버에서 완전히 파일을 다운로드 한 후에 확인 가능
  - 20(데이터.파일 전송), 21번(신호/명령 제어) 포트 사용
  - Active FTP : 
    1. 클라이언트가 다운받을 포트를 FTP 서버에게 알려줌 (21번 포트를 통해 내용 전달)
    2. FTP 서버가 20번 포트를 통해서 요청한 포트로 전달 
  - Passive FTP :서버가 클라이언트에게 21번으로 알려줌, 데이터는 1024 이후 포트 사용 

<br>

- API (Application Programming Interface)
  - 시스템 간 연동을 통해 데이터를 **실시간**으로 수신할 기능을 제공하는 소프트웨어

<br>

- SQOOP : SQL + Hdoop
  - 정형 데이터를 수집해서 하둡으로 넘겨주는 기술
  - 커넥터를 통해서 관계형 DB(RDBMS)와 하둡 간의 연결
  - 적재과정 자동화 및 병렬처리

<br>

- RYSNC 
  - 리눅스 방식으로 1:1 서버 - 클라이언트 파일과 디렉토리 연결

<br>

- DB TO DB
  - 데이터베이스간 동기화 및 전송
  
<br>

- ETL (Extract Transfer Load)
  - 추출 -> 변형 -> 적재
  - 추출 변형 새로운 테이블을 만들어 내는 과정
  - 정형 데이터는 ETL 프로세스를 거쳐 DW 에 저장 -> Data mart에 연결 -> 각 팀에 전달


## 참고

> [빅데이터 분석기사 암기 같이해요(WITH 빅공남)](https://www.youtube.com/watch?v=x67PIdfosdM&list=PLjskUEbH65lfzk3F5geNZk_qNhFvnhaPr&ab_channel=%EB%B9%85%EA%B3%B5%EB%82%A8%28%EB%B9%85%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B3%B5%EB%B6%80%ED%95%98%EB%8A%94%EB%82%A8%EC%9E%90%29)