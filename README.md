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

### [입력받는 인수]

				
### [난수발생]
컴퓨터가 선택하는 3개 숫자 변수를 만든다.
``` java
import java.io.*;
import java.util.*;

public class BaseBall{
	public static int playGame() throws IOException{ // 컴퓨터가 3개의 난수를 발생시키는 메소드
		int x, y, z; // 컴퓨터가 선택하는 3개 숫자
		Random r = new Random(); // 난수발생 Random() 메소드로 객체 변수 r을 생성
		x = Math.abs(r.nextInt() % 9) + 1; // 1부터 9까지의 난수 발생
		
		do {
			y = Math.abs(r.nextInt() % 9) + 1;
			
		}while(x==y); // 만일 난수 y가 x와 같은 수일 때 다시 한번 난수 발생 반복
		
		do {
			z = Math.abs(r.nextInt() % 9) + 1;
		}while(z==x || z==y); // 만일 난수 z가 x 혹은 y와 같은 수일 때 다시 한번 난수 발생 반복

		System.out.println(x + ", " + y + ", " + z); // 컴퓨터가 발생시킨 난수 확인(게임 시 삭제)
		
		return playGame(x, y, z);
	} 
```
##[실행결과]

