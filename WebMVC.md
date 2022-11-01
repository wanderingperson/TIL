### 회원 웹 기능-홈 화면 추가

![image](https://user-images.githubusercontent.com/114403546/199031903-c1b5cf09-452a-4564-ae16-3ca805fca778.png)

>return homeless에 의해 homeless.html로 이어진다.

![image](https://user-images.githubusercontent.com/114403546/199032216-5efe9b6e-ff29-4b58-a8a8-fae566b4e099.png)

>html에서의 h는 h1~h6까지 있고 글자크기를 나타낸다
>
>p는 문단을 나눈다
>
>a는 하이퍼링크로 href는 실제 링크를 나타낸다 

![image](https://user-images.githubusercontent.com/114403546/199033788-f57615b6-4aa0-4bd7-9e49-359f1146cc9f.png)

- 실제 구동됐을 때 화면

![image](https://user-images.githubusercontent.com/114403546/199034295-f054cafb-7211-467f-9ee9-696c4e23caa1.png)

![image](https://user-images.githubusercontent.com/114403546/199034345-b033ef10-25f8-4b4e-8c4a-3e084cb64edb.png)

![image](https://user-images.githubusercontent.com/114403546/199034357-612207ce-90fd-4a6f-a040-f21c55c7dcfe.png)

>회원 가입과 회원 목록은 아직 만들어놓은게 없어서 whitelabel error가 발생한다

![image](https://user-images.githubusercontent.com/114403546/199033970-0e520216-ca06-4aec-b77e-ba8a80fc1c3c.png)

![image](https://user-images.githubusercontent.com/114403546/199034677-e684769a-cdaf-41d6-9275-be693101dd26.png)

> @GetMapping에 의해 /가 인식돼서 homeless.html로 이어진다

### 회원 웹 기능-등록

![image](https://user-images.githubusercontent.com/114403546/199131566-415b9a55-011e-4a4f-998d-ec09efde237f.png)

> @GetMapping에 의해 members/newperson으로 들어갈 시 createMemberForm.html을 출력한다.

![image](https://user-images.githubusercontent.com/114403546/199132586-818c9549-ad0b-43d3-b4fc-2dfb9105f7a9.png)

![image](https://user-images.githubusercontent.com/114403546/199131780-4fec6bc6-ae81-4dfd-bfbc-e905343f59da.png)

> 이름을 입력시 name="namae"에 의해 post방식으로 저장이 된다.

![image](https://user-images.githubusercontent.com/114403546/199132953-cadd496e-9f18-48d3-a7d6-331b2ad40fb9.png)

![image](https://user-images.githubusercontent.com/114403546/199133174-b28a89c5-5ccc-4e5f-ac37-e4fde99110e0.png)

> @PostMapping에 의해 create 메소드가 호출이 되면서 MemberForm에 setName에 의해 값이 저장이 된다.
> 
> 값을 꺼낼때는(조회) getName을 이용해서 꺼낼 수 있다.

### 회원 웹 기능-조회

![image](https://user-images.githubusercontent.com/114403546/199260372-df4b4a08-9590-4dd4-8684-ec91b7344c9d.png)

![image](https://user-images.githubusercontent.com/114403546/199260489-a8f64a3f-eb1c-4b84-b350-7a23412a516f.png)

![image](https://user-images.githubusercontent.com/114403546/199260571-8f5aa447-1b3f-4d47-8f3b-48d3821f98ab.png)

>회원 등록으로 Sawano Hiroyuki와 Kajiura Yuki를 등록했다.

![image](https://user-images.githubusercontent.com/114403546/199260709-0339bd34-8685-41a0-9248-71b3396e555c.png)

>회원 목록에 들어간 결과

![image](https://user-images.githubusercontent.com/114403546/199261590-d1ed0a49-1453-453c-a4b6-58b3d0aca945.png)

>rememberlist.html의 members(MemberController.java의 mode.addAttribute(attributeName:----)과 동일해야한다)
>
>id와 name은 private으로 설정되있어서 getId와 getName을 통해 가져와서 출력한다.
>
>그것이 ${member.id}와 ${member.name}이다.

#### 만약 Demoapplication을 재실행 시 데이터가 날라가서 다시 등록을 해야한다.

#### 따라서 데이터들을 파일이나 데이터베이스에 저장을 해야한다.
