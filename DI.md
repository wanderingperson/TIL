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

### 자바 코드로 직접 스프링 빈 등록하기

![image](https://user-images.githubusercontent.com/114403546/198960867-709bafd8-2f0f-4108-99fd-054c55d965cc.png)

>@Bean을 이용해서 직접 등록을 할 수 있다. MemberService()에 밑줄이 그어지는 이유는 ()에 들어가야 하는 요소가 있기 때문이다.

![image](https://user-images.githubusercontent.com/114403546/198961073-33e66ce4-e384-404c-a698-2b506a5d59aa.png)

>MemberService는 memberRepository를 필요로 한다. 따라서 memberRepository()가 안에 들어가야 하는데 그전에 memberRepository도 마찬가지로 스프링 빈에 등록해야한다.

![image](https://user-images.githubusercontent.com/114403546/198961199-912678ce-0a9d-4e25-bfd6-c2b17c550275.png)

![image](https://user-images.githubusercontent.com/114403546/198961256-4847be5a-d09c-4e00-b728-a29af5396891.png)


![image](https://user-images.githubusercontent.com/114403546/198961603-0af32d25-ccee-4bd9-90ab-a19770c1b947.png)

>DI에는 3가지 방법이 있는데 위에서 우리가 한 방식은 생성자 주입이다. (memberService가 MemberController에 주입되는것)

![image](https://user-images.githubusercontent.com/114403546/198961945-fa1dc00e-aaa8-4d37-b1af-01604015d35e.png)

>이러한 방식은 필드 주입인데 중간에 수정이 불가능하기 때문에 그다지 권장되지않는다.

![image](https://user-images.githubusercontent.com/114403546/198962431-4bbc4926-fe1a-416f-a5c1-54c35eee9401.png)

>이러한 방식은 setter 주입인데 public으로 공개가 되어 있어야 하기 때문에 보안상으로 문제가 있을 수 있다.

#### 따라서 DI중 생성자 주입을 권장한다.

>컴포넌트 스캔은 정형화된 컨트롤러, 서비스, 리포지토리에 사용하기 좋다.
>스프링 빈을 사용하는 경우는 구현 클래스를 변경해야할때 사용하기좋다. 구현클래스를 변경할때 컴포넌트 스캔은 여러개를 바꿔야하는 반면 스프링 빈을 사용하는 경우 빈만 수정하면된다.
>@Autowired는 스프링이 관리하는 객체에서만 동작을 한다.
