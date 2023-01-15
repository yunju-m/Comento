# Comento
코멘토 직무부트캠프 - 백엔드 개발 실무

## [1차 과제] 개발환경 셋팅
**1. JDK 1.8 설치(1.8u_221 버전)** <br/>
JDK 설치( **[http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html) 다운로드.**
- 환경변수 셋팅(제어판 > 시스템 > 고급시스템 설정 > 고급 탭 > 환경 변수)
- cmd 창에 javac를 입력하여 동작하는지 확인했습니다.

![jdk설정 확인](https://user-images.githubusercontent.com/74498379/212528216-033b90a3-60e0-40c6-9f04-0f7844ab3a3e.png)<br/>

**2. Eclipse, Spring 다운로드 및 설치** <br/>
스프링 개발 환경을 구축하기 위해 먼저 Eclipse IDE for Java EE developers를 다운로드 하였습니다.

![설치한 이클립스](https://user-images.githubusercontent.com/74498379/212528777-0da4405c-2112-4e81-b4ef-151500777f09.png)

1) 설치 완료 후 Eclipse.ini(eclipse 설치 경로에 존재)의 하단의
 -vm C:\Program Files\Java\jdk1.8.0_221\bin\javaw.exe 추가.

![이클립스 실행 에러](https://user-images.githubusercontent.com/74498379/212528804-e00c0b3f-a245-4c47-8475-987d99cea78f.png)

이클립스를 실행해보니 다음과 같은 에러가 발생하였습니다.
eclipse.ini에서 jdk가 이전 오라클에서 연동된 것과 겹쳐서 충돌이 발생한 것을 확인하고 -vm 경로를 수정해준 결과 정상적으로 실행된 것을 알 수 있었습니다. <br/>

2) 이클립스 인코딩 셋팅
- Windows > Preferences > workspace 에서 Text file encoding에서 utf-8로 설정하였습니다.
- Windows > Web > jsp file 에서 Encoding 부분을 ISO 10646/Unicode(UTF-8)로 설정하였습니다.

3) spring 설치
Help > Eclipse MarketPlace 에서 STS 검색하여 설치

![Spring설치결과](https://user-images.githubusercontent.com/74498379/212528841-95f3c000-d96c-4ae2-b3da-7b9888011671.png)

**3. 톰캣 설정** <br/>
jdk 1.8을 실행하기 위해 9 버전의 Tomcat을 다운로드 및 설치하였습니다. >( [https://tomcat.apache.org](https://tomcat.apache.org/)  [)](https://tomcat.apache.org/)

이때, 처음에는 9.0 tomcat을 설치해도 해당 파일이 보이지않고 7.0까지밖에 없었습니다.
이를 해결하기위해 help > install new software를 클릭하여 JST server adapters, JST server adapters extensions을 클릭하여 설치하였습니다.

![Tomcat 9 0 안보이는 문제 해결책](https://user-images.githubusercontent.com/74498379/212529792-43fdd0e2-786a-4b0d-b01b-069e8cb1e3cf.png)

![Tomcat 9 0 추가한 결과](https://user-images.githubusercontent.com/74498379/212529715-b04818ef-c0cb-4292-a78d-02cedf11010c.png)


**4. 스프링 프로젝트 Hello World 출력** <br/>
1) File > New > Other > Spring > Spring Legacy Project를 선택하여 settingweb이라는 프로젝트를 생성하였습니다.
2) 패키지명은 com.devfun.settingweb으로 설정하였습니다.
이때, 다음과 같은 오류가 발생하였습니다. <br/>



**5. mariadb, mySql Workbench 설치 및 샘플 DB 구축** <br/>
1) Windows용 MariaDB 설치 한 후 설정한 암호를 입력하여 root계정으로 로그인했습니다.

![MariaDB로그인](https://user-images.githubusercontent.com/74498379/212529800-e0a6577f-9d7d-4c90-ac87-95f6010aec9d.png)

2) mysql workbench 설치
Theater(극장)이라는 스키마를 생성하고 그 안에 Tables, Views, StoredProcedures, Functions 테이블을 생성했습니다.
각 테이블마다 속성을 지정해주고 데이터를 넣고 조회하였습니다.

