
### AOP가 필요한 상황

![image](https://user-images.githubusercontent.com/114403546/202633395-62516a19-5b5f-4a8e-affd-c47a8d453142.png)

>모든 메소드의 호출 시간을 측정해야 할때, 그 측정 시간단위를 (s->ms) 바꿔야 할때

![image](https://user-images.githubusercontent.com/114403546/202634030-aa329e7f-27c7-4dc7-822e-92e06c57eaa4.png)

>System.currentTimeMillis() : ms단위로 측정을 한다
>
>즉, 시작할때 시간을 측정하고(start = System.currentTimeMillis();), 끝날때 시간을 측정하면(finish = System.currentTimeMillis();)
>
>시간의 차가 소요 시간이다

![image](https://user-images.githubusercontent.com/114403546/202637083-c2b11c54-03b2-4c3a-b0fb-3350470e68c1.png)

### AOP 적용

![image](https://user-images.githubusercontent.com/114403546/202906887-23c22878-3440-443a-aadf-458dddd75b78.png)

>이러한 문제점을 해결하기 위해 있는것이 AOP이다

![image](https://user-images.githubusercontent.com/114403546/202907390-c16f9e32-1350-4738-a0b2-f371c44b164a.png)

>스프링 빈에 AOP를 등록해준다.

![image](https://user-images.githubusercontent.com/114403546/202907524-856111db-97f6-4331-b860-a99cf1675ce6.png)

>혹은 @Component를 추가한다.

![image](https://user-images.githubusercontent.com/114403546/202907681-bdaa598b-84e3-4f12-9797-510a15b54069.png)

>@Around로 범위지정을 할수 있다. 이 경우는 com.example.demo 패키지 하위에 전체적용하는 것이다.

![image](https://user-images.githubusercontent.com/114403546/202908021-7091ed8b-f864-4b10-a92f-39dce49e83a8.png)

![image](https://user-images.githubusercontent.com/114403546/202907725-504a27bd-43cc-4876-aee9-e8cc47b2e4f1.png)

>실행을 할 시 소요시간이 발생한다.
