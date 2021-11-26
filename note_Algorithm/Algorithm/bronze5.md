- 제곱수 구하기

```c
// #include <math.h>
// double pow(double x, double y)
l = (int)pow(a, 2);
```

- 여러개 숫자 저장할 공간 동적 할당

```c
int* data = (int*)calloc(5, sizeof(int));

for (int i = 0; i < 5; i++) {
	scanf("%d", &data[i]); // &data[i] == data+i;
}

free(data);

```

- escape sequence

```c
int main()
{
	printf(".  .   .\n");
	printf("|  | _ | _. _ ._ _  _\n");
	printf("|/\\|(/.|(_.(_)[ | )(/."); // 여기서 \를 \로 표현하기 위해서 escape sequence \가 앞에 붙어야 한다. 이건 출력 갯수에 영향 안미치는 것
}
```

- array vs string

  - array

    같은 타입 여러개를 담을 수 있는 변수. 기본적인 배열이다.

  - string

    char array[ ] 를 의미.

    즉, char 타입을 여러개 담을 수 있는 배열이다.

    마지막에 NULL이 무조건 들어가야 한다.(그래서 NULL자리까지 생각해주어야 함)

  - char

    단순히 char 타입을 의미.

    NULL이 없다.

    ' '으로 초기화된다.

    

- string에 대하여

  1. NULL이 무조건 들어갈 자리가 있어야 하고 들어가야 한다. 없을 시에 컴파일러가 자동으로 생성한다.

  2. string store by pointer vs store by array

     1. by pointer

        value가 text segment에 저장된다.

        수정 불가능. 오직 읽기만 가능하다

     2. by array

        value가 data segment에 저장된다

        수정 가능.

        

     => **결국, string은 store by array 방식을 따르는 것이 좋다.**

     

  3. string은 결국 pointer

     - string 관련 함수는 입력이 99.9퍼센트 포인터이다.
     - %s : pointer를 dereferening 하는 연산자.



- array 초기화
  1. array는 하나 정의해주면 나머지 요소 다 0으로 초기화 한다.

```c
#include <stdio.h>

int main()
{
    int numArr[10] = { 0, };      // 배열의 요소를 모두 0으로 초기화
}
```



- array와 strlen

  - 먼저 메모리 공간을 잡아주는 것 뿐이다.

  - ```c
    int main()
    {
    	char s1[1000001];
    	int length;
    	
    	scanf("%s", s1);
    	length = strlen(s1); 
        // strlen(s1)은 1000001이 아니라
        // 그러므로 strlen(s1)은 입력된 문자의 갯수를 반환한다.
    }
    ```

  - 

- strlen
  
  1. 널문자는 빼고 반환



- 문자열의 끝까지 반복하기 / toupper 함수 

  ```c
  int s = 0;
  	char c;
  	while (s1[s]) { // 문자열의 끝까지 반복하고 싶다? -> while문과 문자열 활용
  		c = s1[s];
  		s1[s] = toupper(c); // toupper 함수로 대문자로 변환
  		s++;
  	}
  ```

  