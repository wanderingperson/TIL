
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

