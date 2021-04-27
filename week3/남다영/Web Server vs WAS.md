Web

- 인터넷을 기반으로 정보를 공유, 검색할 수 있게 하는 서비스
- 웹의 세가지 요소: url(주소), http(통신 규칙), HTML(내용)

server

- 클라이언트에게 네트워크를 통해 정보/서비스를 제공하는 컴퓨터 시스템

static page

- 웹 서버는 파일 경로 이름을 받아 경로와 일치하는 파일 컨텐츠를 반환
- 항상 동일한 페이지를 반환

dynamic page

- 인자의 내용에 맞게 동적인 컨텐츠 반환

web server

- 인터넷을 기반으로 클라이언트에게 웹 서비스를 제공하는 컴퓨터
- 하드웨어: web server가 설치된 컴퓨터
- 소프트웨어: 웹 브라우저로부터 HTTP요청을 받아 정적인 컨텐츠(html, css, jpeg)를 제공하는 컴퓨터 프로그램
- 기능
    1. 정적인 컨텐츠 제공 (WAS 없는 경우)
    2. 동적인 컨텐츠를 제공하기 위한 요청 전달 (클라이언트의 request를 WAS에 보내고 WAS가 처리한 결과(response)를 클라이언트에게 전달)
- 정적인 파일들을 application server까지 갈 필요 없이 web server에서 빠르게 보내주기 위해 필요하다. (정적 컨텐츠만 처리하도록 기능을 분배하여 서버의 부담을 줄인다.)
- ex) apache, nginx

WAS(=web container, servlet container)

*(container: JSP, servlet을 실행시킬 수 있는 소프트웨어)

- DB조회, 다양한 로직 처리를 요구하는 동적인 컨텐츠를 제공하기 위해 만들어진 application server
- Web Server + Web Container
- 기능
    1. 프로그램 실행 환경과 db 접속 기능 제공
    2. 여러 개의 트랜잭션 관리 기능
    3. 업무를 처리하는 비즈니스 로직 수행
- Web Server만 사용하는 경우, 사용자가 원하는 요청에 대한 결과값을 모두 미리 만들어서 서비스 해야한다. (이렇게 하려면 자원이 부족해서 실질적으로 어렵다)
- ex) tomcat, jboss

WAS와 Web Server을 분리해야 하는 이유

- 기능을 분리해서 서버 부하 방지, 응답 속도 단축
- 물리적으로 분리해서 보안 강화
- 여러 대의 WAS 연결 가능 → fail over(장애 극복), fail back 처리에 유리
- 여러 웹 어플리케이션 서비스 가능