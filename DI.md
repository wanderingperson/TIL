### 컴포넌트 스캔과 자동 의존관계 설정

![image](https://user-images.githubusercontent.com/114403546/198884294-a245a836-7946-44ee-9bb4-cf6ba59ed93d.png)

>이런 식으로 각 컨트롤러마다 여러개의 MemberService를 생성해야한다.
>이런 경우를 위해 스프링 컨테이너에 등록을 하면 하나의 MemberService만 이용할 수 있다.

![image](https://user-images.githubusercontent.com/114403546/198885087-d2c07ba4-8aae-410e-8c49-a1c0019a169e.png)

>@Autowired를 사용 시 스프링 컨테이너에 있는 MemberService를 연결해준다.

- 오류가 발생하는 이유

![image](https://user-images.githubusercontent.com/114403546/198885376-0d7fc44e-2311-4c22-95e6-f38bc887e47e.png)

![image](https://user-images.githubusercontent.com/114403546/198885612-c02d1fe3-66c9-4776-810b-b088c82a5d7f.png)

>MemberService는 순수한 자바코드라서 Autowired를 그냥 받지 못한다.
>
>MemberService에 @Service를 추가시 스프링 컨테이너에 MemberService를 등록한다

![image](https://user-images.githubusercontent.com/114403546/198885718-b2102da1-10ba-41f4-ac56-d1f43e3d38b8.png)

![image](https://user-images.githubusercontent.com/114403546/198885761-5466ce65-300d-47ad-aa97-476f788f30a7.png)

>@Repository, @Controller도 마찬가지다.

![image](https://user-images.githubusercontent.com/114403546/198886021-549d8a2a-e620-4c96-9053-1b4e4434e793.png)

>따라서 위의 memberService와 memberRepository가 스프링 컨테이너에 스프링 빈으로 등록되어 있다.

>아무 클래스에나 @Component 관련 어노테이션을 설정하면 스프링 빈으로 등록이 되는가?
>
>아니다. hello.hellospring의 하위 패키지부턴 가능하지만 그 이외에는 설정을 해줘야한다

