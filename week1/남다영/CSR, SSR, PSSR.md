### CSR (Client Side Rendering)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26e776a2-7753-42f7-947b-d8ec86651e8a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26e776a2-7753-42f7-947b-d8ec86651e8a/Untitled.png)

react, vue 등의 SPA(Single Page Application)에서 사용되는 방식이다.

데이터를 제외한 화면을 그리는 코드들이 프론트 서버에서 다운받아진다. 클라이언트의 요청이 발생하면 필요한 데이터만 백엔드 서버에 요청해서 받아온다. 이후로도 계속 필요한 데이터만 갱신하며 화면을 구성하고, 화면 끊김 현상이 발생하지 않는다. 

최초에 화면을 그리는 코드들을 js파일에 한번에 번들로 전달받아오기 때문에 이 파일을 처음에 다운받는데 시간이 걸린다.(초기 로딩 속도가 느리다.)code splitting으로 다소 해결이 가능하다.)

초기에 데이터가 존재하지 않기 때문에 검색 봇이 해당 페이지를 빈 페이지로 착각하여 검색 엔진 최적화(SEO)에 취약할 수 있다. (구글 검색 봇 예외)

장점

- 서버 부하가 적다.
- 초기 javascript가 로드되면 컨텐츠를 비동기적으로 로드할 수 있다.

단점

- 초기 로딩 속도가 느리다
- 검색 엔진 최적화에 취약하다.

### SSR(Server Side Rendering)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/df38bbc3-5cc3-4798-90ca-58c48abda454/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/df38bbc3-5cc3-4798-90ca-58c48abda454/Untitled.png)

클라이언트 데이터 요청 발생

⇒ 브라우저 → 프론트 서버 → 백엔드 서버 → 데이터베이스 

의 과정으로 데이터를 가져온 후 반대방향으로 돌아와 브라우저에 화면을 표시한다.

서버에서 데이터를 포함한 모든 페이지를 구성한 후 브라우저에 전달하는 렌더링 방식이다.

→ 클라이언트의 요청이 생길때마다 이 과정을 반복하기 때문에 화면에서 바뀌지 않아도 되는 부분도 계속해서 다시 렌더링이 되고, 서버 부하나 화면 이동간 깜빡거리는 끊김 현상이 일어날 수 있다.

초기 로딩 속도가 빠르다.

[https://www.sarah-note.com/클론코딩/posting2/](https://www.sarah-note.com/%ED%81%B4%EB%A1%A0%EC%BD%94%EB%94%A9/posting2/)

### PSSR(Progressive Server Side Rendering, PR, Progressive Rendering)

서버에서 중요한 컨텐츠를 렌더링 한 후 중요하지 않은 컨텐츠는 기다리지 않고 클라이언트에게 보여주는 방식이다. 중요한 컨텐츠의 덩어리가 수신되는 즉시 페이지에서 html을 점진적으로 렌더링하기 시작하고, 나중에 서버에서 중요하지 않은 컨텐츠를 전부 수신받으면 중요하지 않은 컨텐츠를 표시한다.

1. 브라우저, 서버에 HTML 요청
2. 서버에서 API request 생성 후, 중요 콘텐츠 우선 렌더링하고 브라우저로 스트리밍
3. 브라우저, HTML 청크 로드 후 렌더링(paint)
4. 서버에서 중요하지 않은 컨텐츠를 렌더링하여 클라이언트로 스트리밍
5. 브라우저, 나중에 중요하지 않은 컨텐츠 수신하고 렌더링(paint)
6. 전체 페이지 로드 후, 브라우저는 일반적으로 이벤트 핸들러 및 기타 상호작용 동작을 연결하는 DOM element에 대한 상호 작용 수행

PSSR을 이용하는 경우 javascript를 사용해서 컨텐츠를 로드하지 않고도(CSR처럼) 비동기적으로 사이트를 더 빠르게 로드 할 수 있다.

ex) 이미지 지연 로딩, 보이는 컨텐츠의 우선순위 설정.

[https://velog.io/@bisu8018/점진적-렌더링Progressive-Rendering-이란](https://velog.io/@bisu8018/%EC%A0%90%EC%A7%84%EC%A0%81-%EB%A0%8C%EB%8D%94%EB%A7%81Progressive-Rendering-%EC%9D%B4%EB%9E%80)