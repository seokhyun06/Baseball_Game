# Baseball_Game
## [rule]
**1. 숫자는 1~9까지로 제한한다.**   
**2. 서로 다른 숫자 3개로 이루어진 두 개의 배열(com[], usr[])을 비교하여 볼카운트 계산한다.**   
     **컴퓨터가 내는 숫자는  => 입력받는 인수 Vs 컴퓨터가 발생시키는 난수가 있다.**   
**3. 컴퓨터가 내는 숫자 3개의 배열 Vs 사용자가 내는 숫자 3개의 배열을 비교한다.**   
  **&nbsp;&nbsp;: 숫자와 배열의 자릿수가 일치할 때는 strike! 으로 출력한다.   
  &nbsp;&nbsp;: 숫자는 일치하지만 자릿수가 틀릴 때는 ball! 으로 출력한다.   
 &nbsp;&nbsp;: 숫자와 자릿수가 모두 틀릴 때는 strike: 0, ball: 0 으로 출력한다.   
  ex) 컴퓨터 내는 숫자가 [2][4][7], 사용자가 내는 숫자가 [2][7][4] 이면 strike : 1 & ball:2로 출력한다.**
				
### [난수발생]
**컴퓨터로부터 3개의 난수를 받기 위해 인수가 없는 playGame() 메소드를 생성하여 게임 규칙에 맞게 3개의 난수를 각각 정수형 x, y, z에 저장한다.**   
**Random() 클래스를 만들어 'random'이라는 변수를 생성한다.**   
**x는 랜덤한 값을 미리 뽑아둔 후에 do-while문을 통해 다른 변수 y, z도 난수를 발생한다.**   
**조건이 맞으면 다시 한번 난수를 발생 반복한다.**   
**인수 playGame(,,)으로 retrun한다.**   

``` java
import java.io.*;
import java.util.*;

public class BaseBall{
	public static int playGame() throws IOException{ // 컴퓨터가 3개의 난수를 발생시키는 메소드
		int x, y, z; // 컴퓨터가 선택하는 3개 숫자
		Random random = new Random(); // 난수발생 Random() 메소드로 객체 변수 random을 생성
		x = Math.abs(random.nextInt() % 9) + 1; // 1부터 9까지의 난수 발생
		
		do {
			y = Math.abs(random.nextInt() % 9) + 1;
			
		}while(x==y); // 만일 난수 y가 x와 같은 수일 때 다시 한번 난수 발생 반복
		
		do {
			z = Math.abs(random.nextInt() % 9) + 1;
		}while(z==x || z==y); // 만일 난수 z가 x 혹은 y와 같은 수일 때 다시 한번 난수 발생 반복

		System.out.println(x + ", " + y + ", " + z); // 컴퓨터가 발생시킨 난수 확인(게임 시 삭제)
		
		return playGame(x, y, z);
	} 
```
### [입력받는 인수]
**1. BufferedReader()메소드를 생성하여 객체변수 in에 저장한다.**   
**사용자가 입력하는 데이터를 변수 user에 저장한다.**
**usr[0] 배열 0번칸이 정수형이어서 변수 user에 저장된 데이터를 정수형으로 형변환 시켜 usr[0] 배열 0번칸에 저장한다.**
**usr[1], usr[2]도 똑같이 앞에 설명한 것처럼 해준다.**
```java
do {
			System.out.println("\n카운트: " + count );
			
			BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
			// 콘솔 화면에서 사용자가 입력하는 데이터를 받아들이는 BufferedReader() 메소드의 객체변수 in 생성
			
			String user; // 객체변수 in에 들어있는 데이터 내용을 문자형 데이터로 저장할 변수생성
			
			System.out.println("1번째 숫자");
			user = in.readLine(); // 사용자가 입력하는 데이터를 변수 user에 저장
			usr[0] = new Integer(user).intValue(); // 변수 user에 저장된 데이터를 정수형으로 변환시켜 배열 0번칸에 저장
			
			System.out.println("2번째 숫자");
			user = in.readLine();
			usr[1] = new Integer(user).intValue();
			
			System.out.println("3번째 숫자");
			user = in.readLine();
			usr[2] = new Integer(user).intValue();
```

---
**2. 게임규칙**
**0이나 1~9까지 숫자와 모두 다른 숫자를 입력해야지 반복문을 빠져 나온다.**
```java
			if(usr[0] == 0 || usr[1] == 0 || usr[1] == 0) {
				System.out.println("0은 입력하지 마세요, 다시 입력하세요.");
			} else if(usr[0] > 9 || usr[1] > 9 || usr[1] > 9){
				System.out.println("1부터 9까지의 숫자를 입력하세요");
			} else if(usr[0] == usr[2] || usr[1] == usr[0] || usr[1] == usr[2]) {
				System.out.println("다른 숫자를 입력하세요");
			}
			}while((usr[0]==0)||(usr[1]==0)||(usr[2]==0)||
					(usr[0]>9)||(usr[1]>9)||(usr[2]>9)||
					(usr[0]==usr[1])||(usr[1]==usr[2])||(usr[0]==usr[2]));
					// 모든 숫자가 1~9사이, 같은 숫자가 없는 경우에만 반복문을 빠져나옴
     
```
## [실행결과]
밑에 실행결과를 보면 사용자가 입력한 수를 컴퓨터가 생성한 난수와 비교하며 strike와 ball을 카운팅하여 출력한다.
저런식으로 점점 경우의 수를 줄여나가 strike 3개를 완성하면 게임이 끝이 난다. 이때, strike는 컴퓨터가 생성한 난수와 자릿수가 모두 일치하면 1이 증가된다. 반면에 ball은 숫자는 같으나, 자릿수가 다른 경우에 1이 증가한다.
숫자와 자릿수 모두 다르면 아무것도 증가되지 않는다.
![image](https://github.com/seokhyun06/Baseball_Game/assets/122009563/1e3a9996-2d5d-4a5f-8b54-9aa9ae5036fe)

