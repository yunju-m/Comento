# Comento
코멘토 직무부트캠프 - 백엔드 개발 실무

## [1차 과제] 개발환경 셋팅
1. JDK 1.8 설치(1.8u_221 버전)
JDK 설치( **[http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html) 다운로드.**
- 환경변수 셋팅(제어판 > 시스템 > 고급시스템 설정 > 고급 탭 > 환경 변수)
- cmd 창에 javac를 입력하여 동작하는지 확인했습니다.

![jdk설정 확인](https://user-images.githubusercontent.com/74498379/212528216-033b90a3-60e0-40c6-9f04-0f7844ab3a3e.png)

2. Eclipse, Spring 다운로드 및 설치
스프링 개발 환경을 구축하기 위해 먼저 Eclipse IDE for Java EE developers를 다운로드 하였습니다.

1) 설치 완료 후 Eclipse.ini(eclipse 설치 경로에 존재)의 하단의
 -vm C:\Program Files\Java\jdk1.8.0_221\bin\javaw.exe 추가.

이클립스를 실행해보니 다음과 같은 에러가 발생하였습니다.
eclipse.ini에서 jdk가 이전 오라클에서 연동된 것과 겹쳐서 충돌이 발생한 것을 확인하고 -vm 경로를 수정해준 결과 정상적으로 실행된 것을 알 수 있었습니다. 


2) 이클립스 인코딩 셋팅
- Windows > Preferences > workspace 에서 Text file encoding에서 utf-8로 설정하였습니다.
- Windows > Web > jsp file 에서 Encoding 부분을 ISO 10646/Unicode(UTF-8)로 설정하였습니다.

2) spring 설치
Help > Eclipse MarketPlace 에서 STS 검색하여 설치
