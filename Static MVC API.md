##### IntelliJ 설치 시 컴퓨터 사용자 명이 한글일 시, 오류가 발생하기 떄문에 영문의 사용자 명이 필요하다.


실행중에 동적으로 변한다 : 서버를 열어놓은 상태(Runtime)에서 코드를 수정하는거


정적 컨텐츠 : 파일을 웹브라우저에 그대로 올려놓는것(수정불가 클릭불가)
템플릿 엔진 : 서버에서 데이터를 템플릿에 넣어서 HTML 문서로 작성해 클라이언트에게 전달해준다.

###### 정적 컨텐츠와 템플릿 엔진의 차이 : 파일을 그대로 전달해주냐, 서버에서 약간의 변형(HTML)을 줘서 클라이언트에게 전달해주냐의 차이

##### API : Json방식의 데이터 구조 포맷으로 클라이언트에게 전달하는 방식

#

- 정적 컨텐츠 코딩 예시

>![image](https://user-images.githubusercontent.com/114403546/196033384-d9f2b95b-5a8f-46f9-afa3-c86bc4925f9d.png)

  - 실행 시

>    ![image](https://user-images.githubusercontent.com/114403546/196033454-f80c1935-2137-4acd-af41-c8e103a0c2c8.png)
>
 >    그대로 출력이 된다.
  
  - 이미지로 보는 정적 컨텐츠

> ![image](https://user-images.githubusercontent.com/114403546/196033417-cfb321eb-5fd6-45ea-a737-942ebe009367.png)
>
> 1.해당 url로 접속 시 컨트롤러에서 Hello-static 컨트롤러가 있는지 확인한다
>
> 2.해당 컨트롤러가 없으므로 resources:static/hello-static.html 을 찾은 후 반환한다.
>
> 3.문자열 그대로 출력이 된다.  
  
  
#
  
- MVC 컨텐츠 코딩 예시

> ![image](https://user-images.githubusercontent.com/114403546/196148138-c1ba791b-3bd1-4ef8-b348-ac38333c58b8.png)
>
> 접속주소 : http://localhost:8080/hello-mvc?name=spring
>
> @GetMapping("hello-mvc")는 접속주소의 hello-mvc의 위치다. @GetMapping("bye-mvc")로 바꿀 시 
>
> 접속주소는 http://localhost:8080/bye-mvc?name=spring 로 바뀐다.

> return "hello-templer"는 hello-templer.html을 반환한다. hello-templer가 아닌 다른 문자(dark-templer)로 바꿀 시, html을 dark-templer.html로 바꿔야 한다.
>
> ![image](https://user-images.githubusercontent.com/114403546/196148256-734a8596-cd18-4942-bb93-0b32ebe885bd.png)
>
> @RequestParam("name")은 접속주소의 mvc?(name)의 위치다. 다른 문자(사이트주소)로 바꿀 시, mvc?name을 mvc?사이트주소 로 바꿔야 한다.
>
> ![image](https://user-images.githubusercontent.com/114403546/196150383-5ca9254b-ae5a-4111-8177-040a21648a4a.png)
> 
> ![image](https://user-images.githubusercontent.com/114403546/196150946-3b72de25-fe1b-49fd-b317-14d66ea0788d.png)


> model.addAttribute("name", name);의 "name"은 hello-templer.html에 있는 ${name}을 뜻한다.
>
> "name"을 다른 문자(isthisadream)로 바꿀 시, hello-templer.html에 있는 ${name} 도 $ {hello-templer}로 바꿔야 정상 작동한다.
>
> ![image](https://user-images.githubusercontent.com/114403546/196151705-7a064daf-b098-41c7-b51b-08140768144c.png)
>
>![image](https://user-images.githubusercontent.com/114403546/196151741-d06012d2-e6e7-4ffa-aa3a-1d97304eda6d.png)

 - 이미지로 보는 MVC 컨텐츠

>![image](https://user-images.githubusercontent.com/114403546/196152905-1d411abd-c5bf-4c0f-bb35-c06cdb01c027.png)
>
>1.해당 url로 접속 시 내장 톰캣서버에서 스프링에게 전달을 한다.
>
>2.스프링에서 helloController에 매핑이 되있는걸 확인 후 호출을 하는데, hello-template과 모델(name:spring)값을 반환한다.
>
>3.viewResolver가 hello-template.html을 찾은 후 html을 출력한다.


#

- API 코딩 예시

>![image](https://user-images.githubusercontent.com/114403546/197147129-7109fc40-7c79-4fc7-b248-a71ec0482815.png)
>
>![image](https://user-images.githubusercontent.com/114403546/197147269-a7bda42f-a6f2-4d83-b472-20ebacfc2d57.png)
>
>![image](https://user-images.githubusercontent.com/114403546/197147298-08908166-1cf4-4e6d-89db-0bb6aa358a32.png)
>
>
>![image](https://user-images.githubusercontent.com/114403546/197148819-2f8a2578-561e-4df0-afc8-4455df71ec4a.png)
>
>![image](https://user-images.githubusercontent.com/114403546/197148858-ecb79620-4c1a-4b3e-8285-31f4e00adb35.png)

밑에 Hello-api는 Json 방식으로 출력된다.



 - 이미지로 보는 ResponseBody 작동원리

>![image](https://user-images.githubusercontent.com/114403546/197149709-913e3f50-78cd-4b43-a6be-614fb91ffdc5.png)
>
>1.해당 url로 접속 시 내장 톰캣 서버에서 스프링에게 전달을 한다.
>
>2.스프링에서 @ResponseBody를 인식 한다. @ResponseBody는 Http로 그대로 응답을 넘겨줘야 한다.
>
>3.HttpMessageConverter가 작동한다. 단순 문자를 전달해야 할 시 StringConverter, 객체를 전달해야 할 시 JsonConverter가 작동을 한다.
>
>4.이때 Json방식으로 데이터를 만들어서 요청한 웹브라우저에 전달을 해준다.

 - @ResponseBody에 관한 상세 내용

![image](https://user-images.githubusercontent.com/114403546/197150825-71c59e72-9c13-499b-8503-87f9dbf36a24.png)

(객체를 Json형식으로 바꿔주는 라이브러리중 Jackson이 많이 쓰인다)


#

## 정적 컨텐츠, MVC, API 비교 정리

- 정적 컨텐츠

파일을 그대로 출력한다

- MVC

템플릿 엔진을 MVC 방식으로 분할해서 view를 렌더링해서 렌더링된 html을 클라이언트에게 전달해준다 

- API

객체를 HttpMessageCoverter를 통해 Json방식으로 변환해서 클라이언트에게 반환한다.

