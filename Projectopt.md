[spring.io/guides](https://spring.io/guides) 에서 메뉴얼 참조가능


- #### application.yml

![image](https://user-images.githubusercontent.com/114403546/204135935-20f5b523-ad5a-4ba7-a8e8-663b0a3f6a6a.png)

show_sql : true는 system.out을 통해서 출력하기 때문에 되도록 사용 안한다.

org.hibernate.SQL은 로거를 통해서 출력하기 때문에 주로 사용한다

![image](https://user-images.githubusercontent.com/114403546/204306880-b6b46358-6ce9-4349-b2e5-d2b4ee60866f.png)

@Transactional은 테스트가 끝나면 바로 롤백을 한다.(데이터가 지워진다)

@Rollback은 롤백유무를 뜻하고 (value=false)로 할시 롤백을 비활성화한다.


![image](https://user-images.githubusercontent.com/114403546/205501374-e327370b-57cb-49fd-bca6-45d8b90467dd.png)

FK는 Foreign Key로 외래키다.

외래키는 보통 일대다 관계에서 다에 속해있는 경우가 많다.

![image](https://user-images.githubusercontent.com/114403546/205501526-8bda3808-0ca1-4bc2-971b-124be0720803.png)

![image](https://user-images.githubusercontent.com/114403546/205646346-e07d7aeb-8152-4ca2-8221-a1743f555408.png)

![image](https://user-images.githubusercontent.com/114403546/205646676-7dd0d062-6582-4a81-a9e9-25db6568aba7.png)

![image](https://user-images.githubusercontent.com/114403546/205647797-44f1d6f0-0628-47b0-bf68-8f665c57e490.png)

도메인의 Member클래스는 ![image](https://user-images.githubusercontent.com/114403546/205647880-5d812194-0858-4b76-b3ac-c85458f7f4f0.png)에 있는 id, name, address, orders가 들어간다.

![image](https://user-images.githubusercontent.com/114403546/206934351-f4f05a3d-edac-4b7d-abff-41a04dd16357.png)

![image](https://user-images.githubusercontent.com/114403546/206934483-fbe194e9-a021-46a1-a453-e1b90b8e0d9c.png)

![image](https://user-images.githubusercontent.com/114403546/206934595-2efd83bb-e211-4d01-801f-33fa0897d5cd.png)

![image](https://user-images.githubusercontent.com/114403546/206934750-15fa65c3-f4d3-409a-8367-fb9ce76a3a0d.png)

![image](https://user-images.githubusercontent.com/114403546/206934761-a7958a79-3f44-4cd9-a20c-6b3106cf060a.png)

### 엔티티 설계 시 주의점

![image](https://user-images.githubusercontent.com/114403546/208660294-27c189df-403e-49fd-a244-2f9f4ae2551e.png)

![image](https://user-images.githubusercontent.com/114403546/208660420-ecc985cc-8e24-47c2-a2fe-6f3795b30945.png)

즉시로딩을 할 시 모든 연관관계를 가져오느라 시간이 매우 소요된다.

![image](https://user-images.githubusercontent.com/114403546/208665723-f4358a93-48bf-4ace-96e2-0e2579dad665.png)

![image](https://user-images.githubusercontent.com/114403546/208841178-177e38a6-a008-48d9-80ea-75258abf9e85.png)

![image](https://user-images.githubusercontent.com/114403546/208841577-2c547888-e0b7-40ac-abf6-c4e04e88e6ab.png)

https://docs.spring.io/spring-boot/docs/2.1.3.RELEASE/reference/htmlsingle/#howtoconfigure-hibernate-naming-strategy

http://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/

예시 : orderTable -> order_table로 변경된다.

논리명 : 테이블이나 컬럼명을 명시하지 않았을때 기본옵션

물리명 : 모든 테이블이나 컬럼명에 무조건 적용되는 필수옵션 으로 생각하면 된다.

![image](https://user-images.githubusercontent.com/114403546/208842812-26400be4-b6b7-4369-8bee-dac3d60e1550.png)

#### cascade는 영속화로 부모 엔티티가 영속화될 때 자식 엔티티도 같이 영속화되고, 부모 엔티티가 삭제될 때 자식 엔티티도 삭제되는 등 

#### 특정 엔티티를 영속 상태로 만들 때 연관된 엔티티도 함께 영속 상태로 전이되는 것을 의미한다.
