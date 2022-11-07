### H2 데이터 베이스 설치

- h2.bat 실행 후 앞 ip주소만 localhost로 변경했을때

![image](https://user-images.githubusercontent.com/114403546/199490885-28059ef7-8c8e-4534-afb0-867b4fdb1f85.png)

![image](https://user-images.githubusercontent.com/114403546/199491370-02350851-8f7f-4d28-a69e-cc35760524c9.png)

>이후부터는 tcp://localhost/가 붙어있는 경로로 접속해야 한다.

![image](https://user-images.githubusercontent.com/114403546/199492016-638927d7-8118-43b9-9c1e-c7aa6d7a62ef.png)

>멤버 테이블을 작성한다.
>
>id를 bigint타입으로 (인텔리제이에선 long타입이였다), 그리고 null값(아무값도 없는)을 받을 시 자동으로 id를 채운다.
>
>이름은 최대 255자까지 넣을 수 있다.

#

- 멤버 테이블에 등록하기

![image](https://user-images.githubusercontent.com/114403546/199492886-b1a6f3d2-d591-4c6e-a832-24bbed2d2cb1.png)

![image](https://user-images.githubusercontent.com/114403546/199493015-ea281429-8716-4d63-8105-c3c4472e0380.png)

- 결과값

![image](https://user-images.githubusercontent.com/114403546/199493053-cf4f679a-97ca-434c-b738-cfabd584ff5e.png)

#

### 순수 Jdbc

![image](https://user-images.githubusercontent.com/114403546/199953278-10d7739f-f6cb-4dca-a555-a50812ceaadb.png)

![image](https://user-images.githubusercontent.com/114403546/199953486-cdb9cdbc-d169-4654-8651-da6fc385a160.png)

![image](https://user-images.githubusercontent.com/114403546/199954737-88b3a2ba-5231-4c0f-8699-ef833fab6f16.png)

![image](https://user-images.githubusercontent.com/114403546/200174955-63c9ec7e-0889-46ce-a733-d1c99e8975ed.png)

>Jdbc로 구현할 Repository 클래스 생성 후 MemberRepository로 구현

![image](https://user-images.githubusercontent.com/114403546/200175871-a938339b-feb3-4b0e-a2cc-d7ec46391c9c.png)

>ResultSet=결과를 받는것
>
>conn = getConnection(); //연결을 가져온다
>
>pstmt.setString(1, member.getName()); //숫자1은 insert into ~~ values(?)의 (?)와 매칭된다. 그 후 그 안에 member.getName()의 값을 넣는다.
>
>pstmt.executeUpdate(); //DB의 실제 쿼리값이 날라간다
>
>rs = pstmt.getGeneratedKeys(); //Statement.RETURN_GENERATED_KEYS와 매칭되고, 이 RETURN_GENERATED_KEYS값을 가져온다.

![image](https://user-images.githubusercontent.com/114403546/200337152-b9e46ff2-2f2a-478c-985b-b180204b4bc5.png)

>스프링을 쓰는 이유 : 기존의 코드는 손대지 않고 어플리케이션 어셈블리만 편집하면 다른걸 건드릴 필요가 없다.

![image](https://user-images.githubusercontent.com/114403546/200341563-bac69daf-96ad-4255-95bf-9e795669766e.png)

![image](https://user-images.githubusercontent.com/114403546/200342435-9e0158c6-cc90-4839-87f5-c6e867197993.png)

>MemberService는 MemberRepository에 의존하고 있고, MemberRepository는 MemoryMemberRepository와 JdbcMemberRepository의 구현체가 있다.
>
>스프링 컨테이너에서 <memory>memberRepository를 빼고 <jdbc>memberRepository로만 변경하면 나머진 변경할 필요가없다.

#
  
### 스프링 통합 테스트
