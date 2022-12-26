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
