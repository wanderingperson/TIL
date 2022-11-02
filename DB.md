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


