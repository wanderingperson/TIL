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

  ![image](https://user-images.githubusercontent.com/114403546/200840819-c36713e0-1753-46d7-bb4c-1197694bdb45.png)
  
  >DB에 Higashino Keigo가 이미 있어서 오류가 발생한다.
  
  ![image](https://user-images.githubusercontent.com/114403546/200840980-dd2b75f3-d4d3-445b-804c-4eaeab360748.png)
  
>따라서 DB에 등록돼있는 멤버를 삭제해야 한다.

  ![image](https://user-images.githubusercontent.com/114403546/200841555-2e28e27a-afa0-4320-9f36-c7aaa9482df9.png)

  ![image](https://user-images.githubusercontent.com/114403546/200841687-54381915-4688-4af3-a3f7-ce3c65921c14.png)

  >@Transactional이 없는 상태에서 실행후 재실행을 할 시 DB에 이미 존재하는 인원으로 처리가 돼서 오류가 발생한다.
  >즉, @Transactional은 테스트를 하기전에 실행 시 테스트가 끝나고 DB를 롤백시킨다. 
  >즉, @Transactional 어노테이션을 추가하면 @AfterEach와 @BeforeEach없이 테스트를 반복해서 할 수 있다.
  
  ![image](https://user-images.githubusercontent.com/114403546/200842340-f1fc7ed1-adba-45ca-9299-896ea1da27c9.png)
  
  >하지만 @SpringBootTest와 @Transactional을 사용하면서 테스트하는건(통합테스트) 시간이 오래 걸리기때문에
  >
  >단위테스트를 분할해서 하고 통합테스트는 적게 하는게 권장된다. (1번째사진 단위테스트105ms, 2번째사진 통합테스트666ms)
  
 ![image](https://user-images.githubusercontent.com/114403546/200842844-499b2f16-f23c-4743-b4b1-a456b7207979.png)
![image](https://user-images.githubusercontent.com/114403546/200843072-6c9e5bc5-4393-410c-8ce3-12c0790146ec.png)
  
#
  
  ### 스프링 JdbcTemplate

  ![image](https://user-images.githubusercontent.com/114403546/201106691-e6d41a90-642a-4da5-8f03-893d7075d1af.png)
  
  >생성자가 하나만 있을떄 스프링빈에 등록되면 @Autowired생략 가능하다
  
  ![image](https://user-images.githubusercontent.com/114403546/201107536-9f625559-9342-4e54-9cad-74640186d092.png)
  
  ![image](https://user-images.githubusercontent.com/114403546/201107837-0430f128-477b-4a7f-b51a-204c7f9c9a00.png)
  
  >람다 형식으로 변경
  
  ![image](https://user-images.githubusercontent.com/114403546/201525930-72a9e3d0-3f51-4025-8241-54bae5467d53.png)
  
  >findById는 jdbcTemplate에 있는 쿼리를 지우고 memberRowMapper()를 통해 결과값을 매핑후 List<Member>를 통해 받아서 Optional형태로 변환
  >
  >findByName는 jdbcTemplate에 있는 쿼리를 지우고 memberRowMapper()를 통해 결과값을 매핑후 List<Member>를 통해 받아서 Optional형태로 변환
  >
  >findAll은 리스트로 반환된 memberRowMapper의 결과를 member로 객체를 매핑후 결과값을 가져온다
  
  
  >테스트 코드는 백엔드에서 매우 중요하다.
  >
  >개발 일정중 60~70%는 테스트 코드를 짜는데 쓰인다고 보면된다.
  >
  >테스트코드를 얼마나 꼼꼼히 짜느냐가 중요
  
  #
  
  ### JPA
  
  JdbcTemplate을 사용시 개발해야하는 반복적인 코드가 줄어들었지만 SQL은 직접 작성해야한다.
  
  하지만 JPA사용 시 SQL을 자동으로 처리해준다.
  
  ![image](https://user-images.githubusercontent.com/114403546/201685102-3eb6a8ac-ed16-4b5a-8266-748740791cbf.png)
  
  국내에서는 마이바티스를 JPA보다 많이 사용하고 있었는데 일정기점 이후로 JPA사용세가 꾸준히 증가하고 있다.
  
  ![image](https://user-images.githubusercontent.com/114403546/201686333-27d2c977-7362-44bd-9a37-935230896d06.png)
  
  >spring.jpa.show-sql = true : jpa가 날린 sql을 확인할 수 있다.
  >
  >spring.jpa.hibernate.ddl-auto = none : jpa사용시 회원객체를 보고 자동으로 테이블을 생성하는데, 이미 생성된 걸 사용할 것이므로 자동생성기능을 끈다.
  
  >JPA는 자바진영의 표준 인터페이스고 구현은 각 업체에서 한다.
  >JPA는 ORM기술이다. Object, Relational, Mapping
  
  ![image](https://user-images.githubusercontent.com/114403546/201687514-f29e1ef5-3716-43bb-b0de-8030640bb18f.png)
  
  >@Entity : JPA에서 관리를 한다.
  >
  >@Id : PK(기본 키)
