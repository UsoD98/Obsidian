src/main/resources/static 경로에 index.html 파일 생성
``` html
<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">  
    <title>Title</title>  
</head>  
<body>  
Hello  
<a href="/hello">hello</a>  
</body>  
</html>
```
![[Pasted image 20240325122226.png]]

이를 실행하면 아래와 같은 화면으로 초기화면이 바뀜
 ![[Pasted image 20240325122258.png]]

스프링 부트가 제공하는 Welcome Page 기능
- 'static/index.html'을 올려두면 Welcome page 기능을 제공한다

### 웹에서 검색하여 매뉴얼을 찾아볼 줄 알아야 한다

thymeleaf 템플릿 엔진

hello.hello.spring 밑에다 컨트롤러 패키지 생성
HelloController 생성 후 어노테이션 적용, 코드 작성
![[Pasted image 20240325123318.png]]

`resources/templates/hello.html` 생성 후 코드 작성
``` html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>

    <title>Hello</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>

<body>

<p th:text="'안녕하세요. ' + ${data}" >안녕하세요. 손님</p>

</body>

</html>
```

프로젝트 실행
![[Pasted image 20240325123456.png]]
hello 클릭
![[Pasted image 20240325123525.png]]
위와 같이 html 코드에 작성된 문장이 나온다
이는 컨트롤러에서 GET 방식으로 넘겨서 hello가 url에 매칭이 된 것이다

동작 환경 그림
![[Pasted image 20240325124007.png]]
- 컨트롤러에서 리턴 값으로 문자를 반환하면 뷰 리졸버( `viewResolver` )가 화면을 찾아서 처리한다. 
	- 스프링 부트 템플릿엔진 기본 viewName 매핑
	- `resources:templates/` +{ViewName}+ `.html`
- 참고: `spring-boot-devtools` 라이브러리를 추가한다면, `html` 파일을 컴파일만 해주면 서버 재시작 없이 View 파일 변경이 가능하다.
	- 인텔리J 컴파일 방법: 메뉴 build Recompile
