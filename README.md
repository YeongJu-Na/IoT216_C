# C_Class
IoT-2021-1 Class resource
2021-03-02 IoT Class daily report
### C언어 1강
printf의 사용 - 서식지정자, 이스케이프 시퀀스

### C언어 2강
- 변수:
void타입은 포인터 쓸 때 많이 사용
 /unsigned는 실수형 자료형x
 /3byte, 5 등은 메모리 관리 문제, 정렬 문제(2의 배수형태로?) 등으로 쓰지x

* 상수:
리터럴 상수 -> int a=3+4;	→ 메모리 공간차지함 → | 3 | 4 | 7(a) |

* 연산자: shift연산자
비트shift로 <<1은 *2, >>1은 /2	 ⇒ c++에서는 입출력 관련 문자
 /a+=b; // cpu의 클럭속도를 덜 잡아먹음 -> 선호방식

* 입력받기: scanf
서식문자열?에는 다른내용(prompt ?) 들어가면 안됨
 /변수의 타입과 다른 값 입력 시 오류 → 이러한 오류발생 가능성이 많아서 윈도우즈 프로그램에선 다른 것으로 대체하여 사용 → 추후 학습할 것

* 조건문
switch문이 ifelse에 비해 장점이 될 수 있는 부분 : 많은 elseif중 어느것도 해당되지 않는 경우(else) 앞의 모든 elseif 들을 모두 거쳐야함→ 시간 delay발생  (1st조건 만족하는 값과 else만족하는 값간에 동기화 어려울 수 있다…..
⇒ 반면 switch는 동일 → 제어 타이밍 중요한 경우 필요

### C언어 3강
* scanf:  ‘ ‘, ‘\t’, ‘\n’만날때 까지 데이터 가져오고 버퍼에서 삭제
--->  %c, 문자 1개 받는 경우, 버퍼 내의 enter도 하나의 문자로 인식되어 새로운 입력을 받지 않고 남은 버퍼 값으로 추출해냄  ⇒ 이런 값은 0(또는 NULL)으로 구별가능(입력받은 문자열의 종료도 알 수 있음)  (개행문자(\n): 입력 종료로 받아들임)

* getch()함수- #include <conio.h> 필요-> console의 con / 단일 키 값을 반환
⇒ scanf는 반드시 enter키 입력필요했음 , 얘는 뭐가됐든 그대로 char값으로 되돌림, scanf보다 lowlevel
⇒ 원래는 int로 반환해줌

* 16진수 비트 연산 → 대, 소문자 변환- 대문자는 4?(16) / 소문자는 6? ⇒ 4=0100, 6=0110

* 함수 - 함수의 원형 미리 선언해야

* < 배열 >
--많은 양의 데이터 일괄처리 시 유용
--char배열: 문자열의 끝은 항상 0으로 인식하므로 반드시 필요 → 원소(문자) 수 + 1개의 방 필요 ⇒  고려하지 않고, 크기이상의 원소들 넣으면 쓰레기값들 나올 수 있음(배열의 끝을 인식하지 못해서)
⇒ for문의 조건문이 0이 아닌 동안 루프 실행: for(int i=0;buf[i];i++) == for(int i=0;buf[i]!=0;i++)
	--c컴파일러는 배열의 길이 신경쓰지 않음..!-> 즉, 배열의 길이 등을 검사해서 오류 출력해주지 않음-> 개발자가 직접 신경써야함 ex) int arr[3]={1,2,3}; arr[3]=100; 0부터3까지 출력시 arr[3]으로도 나옴 but, arr 크기출력해보면 3으로 나옴
	--배열 초기화 시, 개별 인덱스만 초기화 하거나 초기화하지 않을 경우 쓰레기값 나옴
→ int arr[3]; arr[0]=10; 이렇게 -> 0번만 제대로 나오고 나머지는 쓰레기값
	→ but, int arr[]={10}; → 10 0 0 나머지는 0으로 나옴
	--배열 크기 명시하기- 2차원에서 행값, 열값 둘다 안하면 error

* < 배열과 포인터 >

-- 1차원 배열에서 buf[]를 매개변수로 가능 but, 2차원은 buf[][] 안됨
-- 2차원행렬에선 *(a+1)과 a[1]은 모두 1행의 주소  → 1차원이면 1인덱스의 값이지만 2차원이면 1행의 주소가 됨
--  2차원포인터 ⇒ int**a  / 매개변수로 2차원 배열 넘길때 int (*ptr)[4]
