### 비즈니스 요구사항 정리

- 일반적인 웹 애플리케이션 계층 구조

![image](https://user-images.githubusercontent.com/114403546/197279755-8cdb7370-7690-4327-a870-ae903d86ef35.png)

> 컨트롤러: 웹 MVC의 컨트롤러 역할
>
>서비스: 핵심 비즈니스 로직 구현(예시 : 회원은 중복가입이 불가능 하게 만들기)
>
>리포지토리: 데이터베이스에 접근, 도메인 객체를 DB에 저장하고 관리
>
>도메인: 비즈니스 도메인 객체, 예) 회원, 주문, 쿠폰 등등 주로 데이터베이스에 저장하고 관리됨

- 클래스 의존관계

![image](https://user-images.githubusercontent.com/114403546/197279985-84b666c7-8ccc-4fa3-83ac-873f5af8d017.png)

> 회원비즈니스 로직에 있는 MemberService
> 아직 데이터 저장소를 설정 안해서 인터페이스로 구현 클래스를 변경 하도록 설계한다
> 회원을 저장하는 건 MemberRepository에 저장예정(데이터 저장소, 즉 DB가 아직 선정되지 않은 상태로 가정)
> 일단은 데이터를 단순하게 저장한다.

#

### 회원 도메인과 멤버 리포지토리 만들기

- 회원 객체

![image](https://user-images.githubusercontent.com/114403546/197400239-ac6cee82-4725-4853-becd-fe827df31188.png)

- 회원 리포지토리 인터페이스

![image](https://user-images.githubusercontent.com/114403546/197400311-a71b5913-080e-496f-972d-e500958bc258.png)

- 회원 리포지토리 메모리 구현체  

![image](https://user-images.githubusercontent.com/114403546/197400392-ce47fe83-5387-494b-9907-4126082b8089.png)
![image](https://user-images.githubusercontent.com/114403546/197400406-ecb1dbe4-2e05-4bd5-be6d-1cb5129df7a8.png)

> - ###  private static Map<Long, Member> store = new HashMap<>();에서 Map<Long, Member>의 뜻
> 
> Map은 Map<Key, Value>으로 이루어져 있다. Key는 고유값이고, Value는 중복이 가능하다. 
> 
> Key의 값이 동일한데 Value값이 다르면 최신 데이터로 갱신이 된다.

> - ### Optional.ofNullable(store.get(id));에서 store.get(id)만 안쓰고 Optional.ofNullable을 사용하는 이유
>
>store.get(id)를 사용하면 null값을 반환할시 오류가 생기기 때문에 Optional을 이용해서 오류가 발생하지 않는다.

> - ### store.values().stream()에서 stream()의 뜻
> 
> stream은 컬렉션(store.values())에 저장되어 있는 요소들을 하나씩 찾는것이다

> - ### .filter(member -> member.getName().equals(name))와 .findAny();의 뜻
> 
> 검색을 해서(filter) member가 member.getName의 name과 같은게(equals)
> 
> .findAny(); 하나라도 있으면 반환한다.

### 회원 리포지토리 테스트 케이스 작성

개발한 기능을 실행해서 테스트 할 때 자바의 main 메서드를 통해서 실행하거나, 웹 애플리케이션의
컨트롤러를 통해서 해당 기능을 실행한다. 

다만 이러한 방법은 준비하고 실행하는데 오래 걸리고, 반복 실행하기
어렵고 여러 테스트를 한번에 실행하기 어렵다는 단점이 있다. 

자바는 JUnit이라는 프레임워크로 테스트를
실행해서 이러한 문제를 해결한다.

- 회원 리포지토리 메모리 구현체 테스트

 #### 멤버가 저장되는지 확인하는 테스트

![image](https://user-images.githubusercontent.com/114403546/197781990-d41dc16c-c23e-429b-82c3-eef62eaf4735.png)

>Optional에서 값을 꺼내올려면 get()을 사용한다.


>- ### Assertions.assertEquals(result, member)의 뜻
>member의 값이 result와 같으면 참을 반환한다 (Junit방식)


>- ### Assertions.assertThat(member).isEqualTo(result)의 뜻
>member의 값이 result와 같으면 참을 반환한다. (Assertj방식)


#### 멤버 이름 검색이 되는지 확인하는 테스트

![image](https://user-images.githubusercontent.com/114403546/197783814-e37beebe-aaa5-4026-b8aa-05af40f957e2.png)

#### 멤버 회원 수가 리스트의 수와 일치하는지 확인하는 테스트

![image](https://user-images.githubusercontent.com/114403546/197804095-82a5f283-1ffb-4fb0-ae5b-dcb5c08b5174.png)

>이 테스트만 하면 정상적으로 작동하지만, 전체 테스트를 할시 오류가 생긴다.

![image](https://user-images.githubusercontent.com/114403546/197804597-0b9507b0-dd75-4eb8-afdf-9adc2e1da20e.png)

>이러한 오류가 생기는 이유는 멤버이름 검색테스트와 멤버회원수 테스트에 똑같은 멤버 이름이라서 오류가 나기때문이다
>
>이런 경우를 대비해서 테스트가 끝날때마다 코드를 지워주는 역할이 필요하다

![image](https://user-images.githubusercontent.com/114403546/197805239-f373320e-0633-4a8c-b64d-ee0d5b918607.png)

>aftereach는 테스트가 끝날때마다 작동하고
>
>clearstore는 저장되있는걸 삭제한다.

#### 회원 서비스 개발

![image](https://user-images.githubusercontent.com/114403546/198039806-209b7e0b-77f4-494f-a7e3-73273a93c4c0.png)

#### 회원 서비스 테스트

![image](https://user-images.githubusercontent.com/114403546/198199072-5ff55002-bd8c-4152-9824-f6c6105e4848.png)

>테스트를 작성할때는 given, when, then을 이용해서 작성을 하는게 좋다

>given : 이런상황내에서 무슨상황이 주어졌는데
>
>when : 이걸 실행했을때
>
>then : 이런 결과가 나와야 한다

#### 테스트는 정상작동보다 변수를 처리(예외처리)하는것이 더 중요하다.

#### 중복 회원 예외 테스트

![image](https://user-images.githubusercontent.com/114403546/198203158-4b93ea2f-455a-4aa9-ad89-6c0238ae7085.png)


>try, catch를 넣어서 예외처리를 해도 되지만 일일이 넣기가 애매해서 assertThrows를 넣는다
>memberService에 member2를 넣었을때 예외가 발생해야한다.

>이렇게하면 회원가입테스트와 중복회원예외 테스트의 멤버 이름이 같아서 오류가 생긴다.
>
>따라서 마찬가지로 clearstore을 해야하는데 memberService가 아닌 MemoryMemberRepository를 클리어해줘야한다

![image](https://user-images.githubusercontent.com/114403546/198203780-5490397f-cf7b-42f6-95e2-745a4eca2508.png)

>하지만 이렇게 설정을 하면
>#### Test의 MemoryMemberRepository는 new MemoryMemberRepository라서 
>같은 MemoryMemberRepository로 바꿔주는게 좋다. (이 상황에서는 MemoryMemberRepositry의 근간이 되는 MemberRepository가 static형태여서 큰 상관이 없지만 static이 아닐 시 안좋음)

![image](https://user-images.githubusercontent.com/114403546/198204710-2229a6ac-0bd5-46e4-9b27-17efde048c96.png)

>따라서 의존성주입(DI, Dependency Injection)을 사용한다.
>새로운 MemoyMemberRepository를 만들고 위의 MemoyMemberRepository memberRepository에 넣은다음
>디렉토리경로 MemberService의 memberRepository에 넣어줘서 같은 memberRepository를 사용하게 만든다.
