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

