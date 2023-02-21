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

**[에러]** </br>
처음 settingweb 패키지를 생성하자 다음과 같이 34가지의 에러가 발생하였습니다. </br>
이를 해결하기위해 차근차근 하나씩 풀어나갔습니다. </br>
![problem에러](https://user-images.githubusercontent.com/74498379/220381958-574d500d-6c43-4a3e-a408-31757c7b67cd.png)

**(1) user setting file does not exist** </br>
먼저, 대부분의 에러는 Maven Repository가 없었기 때문에 발생하였습니다. 따라서 이를 해결하기위해 Maven을 설치해주었습니다.</br>
Maven홈페이지(https://archive.apache.org/dist/maven/maven-3/) 에 들어가서 버전 **3.6.0**을 다운로드 받았습니다.
(3.8.1 버전부터는 http에 대한 외부 연결을 막는 설정이 default로 변경되었기 때문에 3.8.1미만 버전 설치)

![maven_3 6 0](https://user-images.githubusercontent.com/74498379/217738097-e92bcf82-9d7d-48a8-9bfa-66db47a0b880.png)

여러 파일 중에서 zip 파일인 'apache-maven-3.6.0-bin.zip'을 다운받은 후 C:에서 압축 해제합니다.

![maven_3 6 0zip](https://user-images.githubusercontent.com/74498379/217738114-5df4e370-0960-4aef-a9c2-034bc9e57cf0.png)

> Maven 설치 후 기본 설정 </br>
1) 환경변수 설정
압축을 다 풀었으면 이제 환경변수를 설정합니다. '윈도우키+R'을 눌러서 나타난 실행창에 sysdm.cpl 을 입력한 후, 고급 탭에서 '환경변수'를 클릭합니다.
Maven이 설치된 경로를 Path에 추가하기 위해 '새로 만들기'를 클릭하여 **C:\apache-maven-3.6.0\bin** 를 입력하고 'Enter' 키를 누른다. Path 변수에 주소가 추가된 것을 확인하고 '확인' 버튼을 누릅니다.
이때, 사용자변수와 시스템변수 모두 설정해줍니다!!!

![환경변수](https://user-images.githubusercontent.com/74498379/217738153-c8279a32-c482-4bd6-a670-c88035b599c5.png)

![maven환경변수](https://user-images.githubusercontent.com/74498379/217738163-7a2a1c10-c877-4faa-b9f6-e3f5f05d8ed8.png)

이제 Path 변수에 제대로 등록되었는지 확인하기위해 '윈도우키+R'을 눌러서 나타난 실행창에 'cmd'를 입력해서 콘솔 창을 띄웁니다.
콘솔 창에 **'mvn -version'** 라고 입력해서 아래와 같은 화면이 나타나면 설정이 끝납니다. 만약 **'mvn'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는 배치 파일이 아닙니다.** 라는 문구가 뜬다면 Path 설정이 잘못된 것입니다.

![maven설정확인](https://user-images.githubusercontent.com/74498379/217739471-fae7ce3d-5a9b-443f-a93b-d9cf0313d829.png)

2) Maven Repository 이클립스 설정 </br>
이클립스에서 [Window] - [Preference] - [Maven] - [User Settings] 으로 가서 User Settings 부분에 C:\apache-maven-3.6.0\conf\settings.xml 을 등록합니다.

![user_setting설정](https://user-images.githubusercontent.com/74498379/217738545-24a48f4d-6a32-4598-adb6-13df966634d0.png)

3) Maven Integration 설치
맨 처음에 설치한 Maven은 실제 Maven 소스 및 실행파일이고, 앞으로 설치할 Maven Integration은 이클립스에서 Maven을 사용하기 위한 플러그인입니다.

이클립스에서 메이븐을 사용하려면 'M2E' 라는 Maven Intergration을 설치해야 합니다. 이클립스의 [Help] - [Install New Software]에 들어가면 창이 뜨는데, Work With 란에 https://download.eclipse.org/technology/m2e/releases/latest/ 를 입력 후 엔터를 치면 관련된 소프트웨어가 나오는데 모두 설치합니다.

![m2e설치](https://user-images.githubusercontent.com/74498379/217731520-10fb3e51-c79f-4192-b31f-1b2ecc962d14.png)

**(2)-1 처음 project를 생성한 후Maven Dependencies가 생성되지 않은 경우** </br>
**(2)-2 Project build error: Non-resolvable parent POM... Error code 501, HTTPS Required and 'parent.relativePath' points at no local POM** </br>

2020 년 1 월 15 일부터 Central Repository는 더 이상 일반 HTTP를 통한 안전하지 않은 통신을 지원하지 않으며 리포지토리에 대한 모든 요청은 HTTPS를 통해 암호화되어야합니다. 이 오류가 발생하면 Maven Central에 대한 모든 URL 참조를 표준 HTTPS로 바꿔야합니다.
1) pom.xml에 project안에 다음 코드를 추가해줍니다. </br>

 ``` xml
 <pluginRepositories>
        <pluginRepository>
            <id>central</id>
            <name>Central Repository</name>
            <url>https://repo.maven.apache.org/maven2</url>
            <layout>default</layout>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
            <releases>
                <updatePolicy>never</updatePolicy>
            </releases>
        </pluginRepository>
    </pluginRepositories>
    <repositories>
        <repository>
            <id>central</id>
            <name>Central Repository</name>
            <url>https://repo.maven.apache.org/maven2</url>
            <layout>default</layout>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
        </repository>
    </repositories>
</project>
 ```

저장을 하면 자동으로 maven이 설치되면서 설정했던 5.8.1.RELEASE 버전의 스프링 프레임워크가 생성됩니다. </br>

**(3) Class 'org.springframework.web.servlet.config.AnnotationDrivenBeanDefinitionParser $CompositeUriComponentsContributorFactoryBean' not found [config set: settingweb/web-context]** </br>

![InternalResourceViewResolver에러](https://user-images.githubusercontent.com/74498379/220381501-90dad823-4a49-4c26-8267-64d5dbe2fb48.png)

<해결 방안>
1. 프로젝트 우클릭
2. Spring Tool -> Remove Spring Project Nature
3. Spring Tool -> Add Spring Project Nature


최종적으로 에러를 모두 해결한 모습을 볼 수 있었습니다,, </br>
이밖에 다른 에러들도 있었으나, pom.xml에서 ignore eclipse를 했더니 모두 사라진 것을 확인하였습니다. </br>

![최종 해결](https://user-images.githubusercontent.com/74498379/220381551-316869a2-d041-4d54-9cd2-291813d8db3d.png)

- **참고했던 사이트 목록** </br>
[이클립스 pom.xml 에러 Plugin execution not covered by lifecycle configuration: org.apache.maven.plugins:maven-compiler-plugin 에러 해결](https://yonoo88.tistory.com/868) </br>
[Class 'org.springframework.web.servlet.view.InternalResourceViewResolver' not found 오류](https://supiz.tistory.com/24) </br>
[spring 개발환경구축](https://devpad.tistory.com/23) </br>
[maven repository생성](https://lovelytney.tistory.com/14) </br>
[Maven Central 501 HTTPS Required 에러](https://bamdule.tistory.com/41) </br>

결과적으로 서버를 셋팅한 후 실행한 결과 다음과 같이 "Hellow World"가 출력된 것을 확인하였습니다. </br>



**5. mariadb, mySql Workbench 설치 및 샘플 DB 구축** <br/>
1) Windows용 MariaDB 설치 한 후 설정한 암호를 입력하여 root계정으로 로그인했습니다.

![MariaDB로그인](https://user-images.githubusercontent.com/74498379/212529800-e0a6577f-9d7d-4c90-ac87-95f6010aec9d.png)

2) mysql workbench 설치
Theater(극장)이라는 스키마를 생성하고 그 안에 Tables, Views, StoredProcedures, Functions 테이블을 생성했습니다.
각 테이블마다 속성을 지정해주고 데이터를 넣고 조회하였습니다. </br></br>
![mysql 실행결과](https://user-images.githubusercontent.com/74498379/212532466-3a9f8b5b-257b-4d7d-b187-496fc797c051.png)

이때, mysql workbench를 재실행하였을 때 무한대기하는 문제가 발생하였습니다.
서비스 > mysql80이 실행되지 않은 것을 확인하고 시작을 한 결과 "mysql80 서비스가 로컬 컴퓨터에서 시작했다가 중지되었습니다." 라는 오류 문장이 뜨면서 실행이 되지 않았습니다.
그래서 [작업 관리자]에서 mysqld 데몬 프로세스를 실행취소하고 mysql80을 실행하였더니 문제가 해결되었습니다.</br></br>
![mysql 무한대기문제 해결책](https://user-images.githubusercontent.com/74498379/212532774-5e8c11c0-69c1-4982-8e1e-782d61505f33.png)</br>

**6. 스프링, Mariadb, MyBatis 연동, 데이터 조회**</br>
< 4번 문제 해결 후 6번 진행...>


----
## [2차 과제] 인터페이스 가이드 문서 작성
[SW활용현황 API 가이드문서.pdf](https://github.com/yunju-m/Comento/files/10465738/SW.API.pdf)

> **REST API** </br>

REST API(RESTful API)는 REST 아키텍처 스타일의 제약 조건을 준수하고 RESTful 웹 서비스와 상호 작용할 수 있도록 하는 애플리케이션 프로그래밍 인터페이스(API 또는 웹 API)입니다. API 개발자는 여러 아키텍처를 사용하여 API를 설계할 수 있습니다. REST 아키텍처 스타일을 따르는 API를 REST API라고 합니다. REST 아키텍처를 구현하는 웹 서비스를 RESTful 웹 서비스라고 합니다. RESTful API라는 용어는 일반적으로 RESTful 웹 API를 나타냅니다. 하지만 REST API와 RESTful API라는 용어는 같은 의미로 사용할 수 있습니다.

- **REST란?** </br>
Representational State Transfer(REST)는 API 작동 방식에 대한 조건을 부과하는 소프트웨어 아키텍처입니다. REST는 처음에 인터넷과 같은 복잡한 네트워크에서 통신을 관리하기 위한 지침으로 만들어졌습니다. REST 기반 아키텍처를 사용하여 대규모의 고성능 통신을 안정적으로 지원할 수 있습니다. 쉽게 구현하고 수정할 수 있어 모든 API 시스템을 파악하고 여러 플랫폼에서 사용할 수 있습니다. </br>
REST Architecture style의 원칙에는 균일한 인터페이스, 무상태, 계층화 시스템, 캐시 가능성, 온디맨드 코드등이 있습니다. 

- **REST API의 이점?**
1. **확장성** </br>
REST API를 구현하는 시스템은 REST가 클라이언트-서버 상호 작용을 최적화하기 때문에 효율적으로 크기 조정할 수 있습니다. 무상태는 서버 로드를 제거하고, 잘 관리된 캐싱은 일부 클라이언트-서버 상호 작용을 부분적으로 또는 완전히 제거합니다. 

2. **유연성** </br>
RESTful 웹 서비스는 완전한 클라이언트-서버 분리를 지원합니다. 각 부분이 독립적으로 발전할 수 있도록 다양한 서버 구성 요소를 단순화하고 분리합니다. 서버 애플리케이션의 플랫폼 또는 기술 변경은 클라이언트 애플리케이션에 영향을 주지 않습니다. 애플리케이션 함수를 계층화하는 기능은 유연성을 더욱 향상시킵니다.

3. **독립성** </br>
REST API는 사용되는 기술과 독립적입니다. API 설계에 영향을 주지 않고 다양한 프로그래밍 언어로 클라이언트 및 서버 애플리케이션을 모두 작성할 수 있습니다. 또한 통신에 영향을 주지 않고 양쪽의 기본 기술을 변경할 수 있습니다.


> **HTTP통신** </br>
- **HTTP통신이란?** </br>
인터넷에서, 웹 서버와 사용자의 인터넷 브라우저 사이에 문서를 전송하기 위해 사용되는 통신 규약입니다.
일반적으로 전송 계층 프로토콜로 TCP를 사용하고, 네트워크 계층 프로토콜로 IP를 사용합니다. 이 두 계층을 합쳐서 TCP/IP라는 이름으로 부릅니다. TCP/IP에서는 IP 주소를 사용해서 통신할 컴퓨터를 결정하고, 포트 번호를 사용해서 해당 컴퓨터의 어떤 프로그램과 통신할지를 결정합니다.
(HTTP에서는 기본적으로 80번 포트를 사용합니다.)

- **브라우저에 URL을 입력 후 요청하여 서버에서 응답하는 과정** </br>
브라우저 URL창에 **"naver.com"**이라고 입력했을 경우라고 가정.

1. 통신하기 위해 자신의 IP를 알기위해 PC는 IP를 받을 DHCP서버를 찾습니다. 한 서브넷에 속하는 모든 네트워크 구성원들에게 DHCP서버를 찾는 DHCP Discover 메시지를 보냅니다. </br>
(DHCP Discover패킷은 목적지 MAC주소가 브로드캐스트입니다.)

2. DHCP서버는 Client에게 자신이 DHCP서버라는 것, Client의 IP, 가장 가까운 Router IP, DNS서버 IP등을 알려줍니다.

3. 할당받은 IP가 충돌하는지 양측에서 확인합니다. </br>
**Client측** : 할당받은 IP에 ARP Request전송하고 해당 IP에 대한 Reply가 없다면 사용합니다.
만약 ARP Reply를 받았다면 IP를 설정하지 않고 서버에게 DHCP Decline을 보냅니다. </br>
**Server측** : 할당하려는 IP에 대해 ICMP Echo Request를 보냅니다. Echo Reply가 없다면 IP를 할당해줍니다.

4. IP를 할당받고, 네이버 도메인(www.naver.com)에 접속하기 위해 도메인의 IP가 필요합니다.
브라우저는 가장 먼저 도메인 이름에 해당하는 IP를 찾기 위해 브라우저 캐시 또는 hosts파일을 참조합니다.

5. 만약, host파일에도 없는 경우 DNS서버를 통해 조회합니다.
DNS서버를 찾기 위해서는 자신의 ARP Table을 조회하고 없는 경우 L2 Switch에게 ARP Request를 보내게 됩니다.

6. L2 Switch는 MAC address Table을 참고합니다. DNS서버의 정보가 존재하지 않다면 MAC Flooding이 발생합니다. 모든 호스트에게 브로드캐스트를 한 후 응답을 받고 ARP Reply를 보내어 DNS서버를 알려줍니다.

7. PC는 Local DNS서버를 알게 되므로 이제 Local DNS서버에 (www.naver.com)을 질의합니다.
Local DNS에 (www.naver.com)에 대한 정보가 없을 시 Root DNS에게 질의하게 됩니다.
Root DNS에 (www.naver.com)에 대한 정보가 없다면 Root DNS는 Local DNS에게 com DNS 정보를 줍니다.

8. 정보를 받은 Local DNS는 com DNS에게 (www.naver.com)을 질의합니다.
com DNS에 (www.naver.com) 정보가 없다면 Local DNS에게 naver.com DNS정보를 제공합니다.

9. 정보를 받은 Local DNS는 naver.com DNS에게 (www.naver.com)을 질의합니다.

10. naver.com DNS는 Local DNS에게 (www.naver.com) 도메인에 대한 IP를 제공합니다.

11. 정보를 받은 Local DNS는 사용자에게 (www.naver.com)에 대한 IP를 제공해줍니다.

12. 정보를 받은 사용자는 (www.naver.com) 사이트에 접속을 요청하는 Http Request메시지를 보내게 됩니다.

13. HTTP는 상위 어플리케이션 계층(7계층)에 속합니다. 요청을 보내기 위해서는 프로토콜 스택을 통해 높은 계층에서 낮은 계층으로 가며 변환됩니다. 변환되며 메시지라는 데이터의 단위가 프레임 단위로 잘게 쪼개지게 됩니다. 그러면서 상대의 IP주소, 포트번호, 오류유무, 전송시간, offset등의 부가 정보가 붙게 됩니다.

14. NAVER 홈페이지는 TCP통신이지만 HTTP(80)이 아닌 HTTPS(443)을 이용하므로 TCP 특성상 HandShaking 과정을 하지만, TLS(SSL)을 사용하기 때문에 TLS HandShaking을 필요로 합니다.
사용자의 측에서 먼저 서버와 TLS HandShaking을 하기 위한 ClientHello 메시지를 먼저 보냅니다.

15. 데이터를 보내기 위해 NAVER의 IP를 기반으로 내부에 ARP 패킷을 뿌립니다.
하지만 NAVER는 다른 네트워크에 존재하기 때문에 NAVER 웹서버의 라우터가 받게 됩니다.

16. 라우터는 Routing Table을 참고하여 해당 NAVER 웹서버가 있는 라우터에 패킷을 전달합니다.

17. 패킷이 라우터를 거친 후 방화벽을 거치게 됩니다. 방화벽이 패킷을 검사하고 Rule에 필터링 되지 않는 패킷이라면 통과하고 NAVER 웹서버에 최종적으로 도달합니다.

18. NAVER 웹서버는 Client측의 ClientHello 메시지를 받게 되고 TLS HandShaking 과정을 수행합니다.
이후 Client가 요청한 NAVER의 첫 페이지 데이터를 Http Response로 응답합니다.

19. 최종적으로 naver.com 홈페이지가 사용자의 브라우저에 보이게 됩니다.

[출처] (https://blog.naver.com/tkdldjs35/221977544533)

## [3차과제] RestController를 활용한 간단 API구현
**1. 스프링부트 개발환경 설정**<br/>
1) File > New > Project > Spring Boot > Spring Starter Project 를 클릭하여 프로젝트 생성
2) Pom.xml 수정
부트 버전은 2.2.2로 변경합니다.
3) application.properties 수정 ( src/main/resources )
4) 이미지와 같이 package, folder, jsp, java 파일을 생성 후,
[ src > main ] 아래에 webapp, views 폴더를 차례대로 만들고 **test.jsp**를 만듭니다.

저의 경우 다음과 같이 springboot 프로젝트 생성 과정에서 pom.xml의 parent부분에 에러가 발생하였습니다.
![springboot_parent에러](https://user-images.githubusercontent.com/74498379/216554695-bc8eb0bb-8980-4cbe-aa1f-930286d041d4.png)

**2. 통계(SW활용현황) API를 위한 DB, Table 생성**<br/>
- DB, Table 생성문을 이용하여 DB, TABLE을 생성합니다. ( mySql Workbench 이용 )
- mysql workbench는 작업관리자에서 MySQL이 아닌, MySQL80으로 실행해야 작동!!! </br>

```SQL
CREATE DATABASE statistc;
 
CREATE Table statistc.requestInfo (
    requestID numeric NOT NULL primary key,
    requestCode varchar(5) NOT NULL,
    userID varchar(5),
    createDate varchar(10)
);
 
CREATE table statistc.requestCode (
    requestCode varchar(5) NOT NULL primary key,
    code_explain varchar(50) NOT NULL
);
 
CREATE table statistc.user (
    userID varchar(5) NOT NULL primary key,
    HR_ORGAN varchar(5) NOT NULL,
    USERNAME varchar(5) NOT NULL
);
 
INSERT INTO statistc.requestInfo(requestID, requestCode, userID, createDate )
VALUES(1, 'L', 'AAA', '2008180520'), #20년 8월 18일 5시 20분
(2, 'O', 'DDD', '2004040404'),
(3, 'L', 'BBB', '2006220920'),
(4, 'L', 'CCC', '1906220920');
```

![DBTable결과](https://user-images.githubusercontent.com/74498379/216554609-8a1fdfec-fc48-44ac-ab43-866d5c062b05.png)

