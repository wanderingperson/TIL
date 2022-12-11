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
