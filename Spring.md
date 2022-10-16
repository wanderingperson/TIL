##### IntelliJ 설치 시 컴퓨터 사용자 명이 한글일 시, 오류가 발생하기 떄문에 영문의 사용자 명이 필요하다.


실행중에 동적으로 변한다 : 서버를 열어놓은 상태(Runtime)에서 코드를 수정하는거


정적 컨텐츠 : 파일을 웹브라우저에 그대로 올려놓는것(수정불가 클릭불가)
템플릿 엔진 : 서버에서 데이터를 템플릿에 넣어서 HTML 문서로 작성해 클라이언트에게 전달해준다.

###### 정적 컨텐츠와 템플릿 엔진의 차이 : 파일을 그대로 전달해주냐, 서버에서 약간의 변형(HTML)을 줘서 클라이언트에게 전달해주냐의 차이

##### API : Json방식의 데이터 구조 포맷으로 클라이언트에게 전달하는 방식

- 정적 컨텐츠 코딩 예시

![image](https://user-images.githubusercontent.com/114403546/196033384-d9f2b95b-5a8f-46f9-afa3-c86bc4925f9d.png)

  - 실행 시

    ![image](https://user-images.githubusercontent.com/114403546/196033454-f80c1935-2137-4acd-af41-c8e103a0c2c8.png)

     그대로 출력이 된다.
  
  - 이미지로 보는 정적 컨텐츠

![image](https://user-images.githubusercontent.com/114403546/196033417-cfb321eb-5fd6-45ea-a737-942ebe009367.png)

1.해당 url로 접속 시 컨트롤러에서 Hello-static 컨트롤러가 있는지 확인한다
2.해당 컨트롤러가 없으므로 resources:static/hello-static.html 을 찾은 후 반환한다.
3.문자열 그대로 출력이 된다.
