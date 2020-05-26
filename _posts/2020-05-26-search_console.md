---
title: '[Etc] 구글 서치 콘솔(Google Search Console)'
excerpt:구글 서치 콘솔(Google Search Console)에 웹 사이트 등록하기
categories:
    - Etc

tag:
    - Google
    - Google Search Console

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2020-05-26T21:00:00+09:00

toc: true   #Table Of Contents 목차

toc_sticky: true
---

## Intro
Google Search Console은 웹 사이트 즉, 현재 제 블로그 포스팅들이 구글 검색 엔진에 노출될 수 있도록 해줍니다. 이번 포스팅에서는 Github blog 글들을 구글에서 검색되도록 설정해 보겠습니다. 

## Google Search ConSole
Google Search Console은 웹 마스터가 색인 상태를 확인하고 웹 사이트의 가시성을 최적화 할 수 있도록 하는 Google의 웹 서비스입니다. 이 서비스를 이용하면 Google에서 키워드 검색을 통해 SERP(검색 엔진 결과 페이지)에 사이트가 게재된 결과와 총 클릭 수, 총 노출 수 및 해당 업체의 평균 클릭률을 확인할 수 있는 기능이 있습니다.  

## Google Search Console과 사이트 연동

구글 서치 콘솔에 블로그를 등록하는 과정입니다.

먼저 본인의 구글 계정으로 로그인 한 후, [Google Search Console](https://search.google.com/search-console/about?hl=ko)에 들어가줍니다.

들어가면 아래와 같은 화면이 나옵니다. 저는 URL 접두어 유형으로 제 블로그를 주소(https://hyeonjiwon.github.io/)를 입력 해주었습니다. 

![0](https://user-images.githubusercontent.com/47733530/82896995-dcb2c880-9f91-11ea-8b9a-d8abd8b94747.png)

계속 버튼을 클릭하면 소유권을 확인하는 페이지가 나옵니다. 구글이 인증 코드를 삽입한 html 파일을 다운받습니다. 

![17-2](https://user-images.githubusercontent.com/47733530/82899606-3ddc9b00-9f96-11ea-8046-410a5e258faa.png)

다운받은 html 파일을 본인의 Github blog 최상위 디렉토리에 올려줍니다.

![17-0](https://user-images.githubusercontent.com/47733530/82899607-3ddc9b00-9f96-11ea-91d7-d784f41d3a48.png)

Github에 업로드(add -> commit -> push)를 한 후에 확인을 클릭하여 인증을 완료 해줍니다. 

아래 화면은 Github에 업로드를 하고 잘 되었는지 인증 html 주소로 접속해 보고 정상확인한 화면입니다. 

![17-1](https://user-images.githubusercontent.com/47733530/82899603-3cab6e00-9f96-11ea-9f3d-360f7ca9ec67.png)

![17-3](https://user-images.githubusercontent.com/47733530/82895620-6b721600-9f8f-11ea-8b50-e602c98a6d60.png)

이제 막 웹사이트를 등록했기 때문에 아무런 데이터가 없어서 Overview를 보면 비어있을 것 입니다. 크롤링은 한 3일 정도 걸리는듯 합니다.

## 사이트맵(Sitemap) 등록

구글 검색 엔진이 지속적으로 크롤링 작업을 할 수 있도록 사이트맵을 등록해주어야 합니다. 

sitemap.xml 파일을 본인의 Github blog 최상위 디렉토리에 아래 내용을 넣고 생성해줍니다. 참고로 _config.yml 파일의 url이 본인의 웹 사이트 주소여야 합니다. 


  ![17-6](https://user-images.githubusercontent.com/47733530/82900673-daec0380-9f97-11ea-9322-d9f7d0f489a7.png)


```html
---
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    {% for post in site.posts %}
    <url>
        <loc>{{ site.url }}{{ post.url | remove: 'index.html' }}</loc>
    </url>
    {% endfor %}

    {% for page in site.pages %}
    {% if page.layout != nil %}
    {% if page.layout != 'feed' %}
    <url>
        <loc>{{ site.url }}{{ page.url | remove: 'index.html' }}</loc>
    </url>
    {% endif %}
    {% endif %}
    {% endfor %}
</urlset>
```

당연히 Github에 업로드 해주어야겠지요? 

## 사이트맵(Sitemap) 제출

sitemap.xml을 생성하였으면 Search Console에 이를 제출하여야 합니다. 왼쪽 메뉴 바 에서 Sitemaps를 선택하여 줍니다. 사이트맵 URL을 입력해주고 제출 해주면 주기적으로 본인의 웹 페이지를 크롤링 할 수 있도록 해주는 Google Search Console에 등록을 완료 한 것 입니다.

![17-4](https://user-images.githubusercontent.com/47733530/82895625-6ca34300-9f8f-11ea-853f-396b0b9e80cf.png)
