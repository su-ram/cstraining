# week1 
> 웹 브라우저 동작 방식
# 브라우저(Browser)
- **Browse** 
> verb. to look at or through something to see what is there

무엇이 있는지 보는 것, 또는 무언가를 통해 보는 것. 
`Browse` + `er`
(웹 페이지를) 볼 수 있게 해주는 것.



- **브라우저란? ** 
> A web browser (commonly referred to as a browser) is a software application for accessing the World Wide Web. When a user requests a web page from a particular website, the web browser retrieves the necessary content from a web server and then displays the page on the user's device.

정확히는 `웹 브라우저`라고 부르는게 맞다. 웹 브라우저는 웹에 접근할 수 있는 소프트웨어이다. 

- **브라우저의 역할** 
> The purpose of a web browser is to fetch content from the Web and display it on a user's device.

사용자가 특정 웹페이지를 요청하면 웹 브라우저는 웹 서버로부터 웹 페이지를 **불러오고** 유저의 화면에 **보여준다.** 


- 정리
브라우저는 다른 컴퓨터(서버)에 있는 웹페이지를 요청하여 가져오고 사용자에게 보여주는 프로그램이다. 가져오는 것은 웹페이지 즉 html 파일이다. 주소창에 URL을 입력하면 웹서버가 주는 웹페이지(html)을 가져와서 사용자의 화면에 보여준다. 다른 서버에 있는 웹페이지를 가져오는 다른 방법도 있다. 
![](https://images.velog.io/images/su-ram/post/ff1c96f2-1e4c-4341-86a1-f557cb4507ce/curl.PNG)
curl로 웹페이지를 가져온 경우 텍스트형식의 html문서를 가져온 것을 볼 수 있다. 브라우저는 이를 예쁘게 파싱해서 시각적으로 렌더링해서 보여준다는 차이점이 있다. 브라우저가 받게 되는 html은 동일하다. 
html은 하나의 긴 텍스트 문서라고 생각하면, 내가 특정한 글로된 정보를 보고 싶은데 그 정보는 어딘가 내가 모르는 다른 컴퓨터 내에 저장되어 있음. 브라우저는 나 대신해서 다른 컴퓨터의 위치를 찾아서 그 정보를 달라고 요청하고 정보를 받아와서 내가 잘 볼 수 있게 변환해서 보여준다. 

# 브라우저의 구성
- **브라우저 구성 요소**
출처: https://d2.naver.com/helloworld/59361

![](https://images.velog.io/images/su-ram/post/8584bef6-0634-4ec7-b394-9f28110eea58/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EA%B5%AC%EC%84%B1%EC%9A%94%EC%86%8C.png)

1. 사용자 인터페이스
	- 주소 표시줄, 이전/다음 버튼, 북마크 메뉴 등. 요청한 페이지를 보여주는 창을 제외한 나머지 모든 부분이다.
2. 브라우저 엔진 
	- 사용자 인터페이스와 렌더링 엔진 사이의 동작을 제어.
3. 렌더링 엔진 
	- 요청한 콘텐츠를 표시. 예를 들어 HTML을 요청하면 HTML과 CSS를 파싱하여 화면에 표시함.
4. 통신 
	- HTTP 요청과 같은 네트워크 호출에 사용됨. 이것은 플랫폼 독립적인 인터페이스이고 각 플랫폼 하부에서 실행됨.
5. UI 백엔드 
	- 콤보 박스와 창 같은 기본적인 장치를 그림. 플랫폼에서 명시하지 않은 일반적인 인터페이스로서, OS 사용자 인터페이스 체계를 사용.
6. 자바스크립트 해석기 
	- 자바스크립트 코드를 해석하고 실행.
7. 자료 저장소 
	- 이 부분은 자료를 저장하는 계층이다. 쿠키를 저장하는 것과 같이 모든 종류의 자원을 하드 디스크에 저장할 필요가 있다. HTML5 명세에는 브라우저가 지원하는 '웹 데이터 베이스'가 정의되어 있다.

# 브라우저의 동작 방식 
- 렌더링 엔진
	- 요청한 웹서버가 html을 body에 담아서 돌려줌.
	- 이때 이 html파일은 완전 텍스트로만 이루어져 있음. 
	- 텍스트 내의 태그들을 해석하여 특정한 구조를 만든다.
	- 시각적으로 렌더링하여 사용자의 화면에 보여준다. 

- 동작 순서
1. HTML파일 파싱. Parsing
	html 형식으로 된 텍스트들을 구문 분석한다. 
    
2. DOM 트리 구축 
	- DOM : document object model. html 문서를 객체 형태의 모델로 변환한 것. 문서 객체 모델. 모든 태그들을 객체로. 
    구분 분석 후 각 요소들을 트리형태로 구성한다. 
    컨텐트(내용)를 구조화 한다. 
    
3. 렌더 트리 구축
	CSS/style 요소들을 파싱하여 트리형태로 구성한다.
    내용을 어떻게 보여줄지(시각적)를 구조화한다. 
    
4. 렌더 트리 배치
	어떤 공간에 위치할지를 정한다. 레이아웃. 
    
5. 렌더 트리 그리기 
	UI 백엔드가 각 노드들을 그린다. 

# 브라우저의 통신 

- HTTP/ HTTPS
    - HTTP : 좀 특별한 문서를 주고 받기 위한 통신 약속
    - HTTPS : 통신에 들어가는 데이터들이 암호화됨.
- DNS
    - 문자로 된 주소를 숫자로 이루어진 주소로 바꾸기 위해 찾는 작업. DNS 서버에 물어본다. 

