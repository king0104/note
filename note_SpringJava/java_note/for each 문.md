### for each 문

for문의 변수가, 배열의 인덱스로 사용되는 경우가 많아지면서 생긴 문법.

```
for(변수 타입 변수 이름 : 배열 이름)
	실행부분;
```



- 예시

```
int[] arr = new int[5];

for(int i : arr){
    i = (Integer.parseInt(br.readLine()));
}
```

- 주의할 점

- - 기본자료형의 배열은 for-each 문으로 배열의 수정이 불가능하다.

    배열에 직접 접근하지 않고 배열 요소의 값을 다른 변수로 받아서 처리하기 때문!!

  - 즉, 입력 불가, 수정 불가.

  - 오직 **배열에서 값 하나하나를 꺼내오는 것만** 가능!!!!!!!!!!

