![image](https://user-images.githubusercontent.com/114403546/209304131-f1c5ce5d-5edd-4086-ac91-7e36bee53450.png)

![image](https://user-images.githubusercontent.com/114403546/209553920-135a1961-5a47-4bcd-9790-98ad62cae3a1.png)

![image](https://user-images.githubusercontent.com/114403546/209556497-b491a16a-a9c0-4619-8e01-e18238f268b1.png)

![image](https://user-images.githubusercontent.com/114403546/209556552-984d8628-bacc-4c88-bfc8-e8e3cbd89e7a.png)

이런 방법은 테스트를 할때 수정을 할수 있는 방법이 없다. 다른 방법으로는 Setter를 통한 인젝션을 사용한다.

![image](https://user-images.githubusercontent.com/114403546/209556797-7b770cb4-540a-4fe2-b704-ff96ceac78a1.png)

Setter를 통해 주입이 된다. 테스트를 할때 편하지만 
#### 누군가 개발 중간에 데이터를 바꿀 가능성이 있다

그래서 Setter보다 권장되는 방법은 생성자를 통한 인젝션을 사용하는 것이다.

![image](https://user-images.githubusercontent.com/114403546/209556797-7b770cb4-540a-4fe2-b704-ff96ceac78a1.png)

최근에는 Transactional을 제거 후 final을 추가하는 게 낫다. final 어노테이션은 값을 넣었는지 안넣었는지 체크가 가능하다.

![image](https://user-images.githubusercontent.com/114403546/209557766-b8847fff-dfb0-4f76-aed7-a5c38fb08e6c.png)

이것보다 권장되는 방법은 롬복의 @AllArgsConstructor를 이용해서 생성자 주입을 만들어주는 것이다.

![image](https://user-images.githubusercontent.com/114403546/209557866-e23d47c7-45d9-43f0-bad0-785ab3ab049e.png)

이것보다 나은 방법은 롬복의 @RequiredArgsConstructor를 이용하는건데 final 어노테이션이 있는것만 생성자 주입을 만들어준다.

![image](https://user-images.githubusercontent.com/114403546/209557954-12480fae-73d5-42ef-8128-f4cb3f900efb.png)

![image](https://user-images.githubusercontent.com/114403546/209680961-66de01f1-a796-4c5f-9aa3-20c4d587e2e9.png)

![image](https://user-images.githubusercontent.com/114403546/209681008-e1fe632d-5b5e-4748-8d51-237d6d1dbc01.png)

![image](https://user-images.githubusercontent.com/114403546/210074186-d0136186-a3cb-4e83-a7f2-e2922a863b80.png)

![image](https://user-images.githubusercontent.com/114403546/210074959-8154ae21-7782-47c8-9a47-150be4e30667.png)

Stock관리를 할때 Item에 관련되있으므로 Item패키지 안에서 처리를 이루어지게 한다. 처리가 안에서 이루어지므로 @Setter를 빼도된다.

![image](https://user-images.githubusercontent.com/114403546/210075074-40fc9043-2186-4ce6-97d7-d8f9cca5407d.png)

#### 상품 리포지토리 개발

![image](https://user-images.githubusercontent.com/114403546/210174981-4ba61702-c6a0-4002-8120-0d18114f7a2f.png)

#### 상품 서비스 개발

![image](https://user-images.githubusercontent.com/114403546/210233199-8f9c7213-1ef9-4bd9-974d-c26b61610f23.png)

#### 주문 도메인 개발

![image](https://user-images.githubusercontent.com/114403546/210356562-1fae8ff3-f86b-49f5-9404-21f06b931951.png)

##### 생성 메서드

![image](https://user-images.githubusercontent.com/114403546/210359037-8885230e-7d05-4156-9e3c-6bb6106ae92b.png)

##### 비즈니스 로직

![image](https://user-images.githubusercontent.com/114403546/210359552-5441e8fe-bc29-4344-afc6-e44eeca7e9ef.png)

![image](https://user-images.githubusercontent.com/114403546/210359117-429d69c4-29d9-4d9d-a751-2edcf7959637.png)

##### 조회 로직

![image](https://user-images.githubusercontent.com/114403546/210359183-e3c25c40-a8f1-40ca-b6f6-9b68f0a8b1c8.png)

#### 주문 서비스 개발

![image](https://user-images.githubusercontent.com/114403546/210802809-73e39838-153d-4b35-953d-59b4a50d35de.png)

![image](https://user-images.githubusercontent.com/114403546/210963574-52332b9a-0a7c-4b67-8d6f-2e84f52f6f8c.png)

![image](https://user-images.githubusercontent.com/114403546/210963693-bc24bcf6-fd71-4e6a-8d63-44ddf7d9289f.png)
