[spring.io/guides](https://spring.io/guides) 에서 메뉴얼 참조가능


- #### application.yml

![image](https://user-images.githubusercontent.com/114403546/204135935-20f5b523-ad5a-4ba7-a8e8-663b0a3f6a6a.png)

show_sql : true는 system.out을 통해서 출력하기 때문에 되도록 사용 안한다.

org.hibernate.SQL은 로거를 통해서 출력하기 때문에 주로 사용한다

![image](https://user-images.githubusercontent.com/114403546/204306880-b6b46358-6ce9-4349-b2e5-d2b4ee60866f.png)

@Transactional은 테스트가 끝나면 바로 롤백을 한다.(데이터가 지워진다)

@Rollback은 롤백유무를 뜻하고 (value=false)로 할시 롤백을 비활성화한다.
