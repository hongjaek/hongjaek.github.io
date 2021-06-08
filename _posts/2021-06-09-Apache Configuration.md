---
title:  "Apache Configuration"
categories: 
  - Apache
tags:
  - Apache
  - Configuration
  - httpd.conf
---

# Apache Configuration 정리
Apache 2.4, CentOS 7을 기준으로 작성하였습니다.
주기적으로 업로드 진행 예정

## httpd.conf 항목 분석
- Include `conf파일 위치` -- 다른 설정파일을 포함시킬 수 있음.
```
Include /usr/local/apache2/conf/ssl.conf
```
<br>
- LoadModule `모듈 이름` -- Apache는 모듈을 읽어 기능을 확장하게 되는데 이때 모듈을 로드하도록 설정
```
LoadModule status_module modules/mod_status.so
```
- &lt;IfModule&gt; ~ &lt;/IfModule&gt; -- 특정 모듈이 있는 경우만 선택적으로 처리할 수 있도록 블럭화
<br>
- ServerRoot "`디렉토리`" -- Apache 서버의 Root 디렉토리 설정
- Servername `도메인` -- 서버 도메인 설정
- Listen `포트` -- 포트 지정
- &lt;VirtualHost&gt; ~ &lt;/VirtualHost&gt; -- 여러 주소와 포트에 대해 다른 행동을 지정할 수 있도록 설정 가능
  ```
  80포트 - http
  443포트 - https
  이렇게 두 프로토콜에 대한 설정을 모두 할 수 있다.

  <VirtualHost *:80>
    ServerAdmin hong@example.com
    DocumentRoot "/www/hong/pages"
    ServerName hong.blog.com
  </VirtualHost>

  <VirtualHost *:443>
    ServerAdmin hong@example.com
    DocumentRoot "/www/hong/pages"
    ServerName hong.blog.com
  </VirtualHost>
  ```

### 참조
https://httpd.apache.org/docs/2.4/en/configuring.html