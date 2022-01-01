### 컬렉션 등장 배경

-  결국 여러 정보를 넣을 수 있는 타입은 `String`과 `리스트` 입니다.
- `String`의 경우는 처리에 제약(숫자와 글자가 섞일수는 있으나, 하나의 덩어리로 취급 해야 하므로)이 있으므로, 결국 `리스트`만이 우리가 배운 유일한 것이였습니다.
- 본 수업에서는 `리스트`처럼 복수의 데이터를 처리하면, 각각 서로 다른 특징과 용도를 갖는 `tuple`, `set`, `dictionary`에 대해서 배웁니다.

### 1. set

- { } 기호 사용
- 정렬되지 않은 수학의 `집합`
- 중복 미허용

  - 중복되는 값 들어오면, 1개 빼고 나머지 제거

#### 예시

- ```python
  exSet1 = { 1, 2, 3, 4, 5 }
  print(exSet1)
  
  exSet2 = { 'a', 'p', 'p', 'l', 'e' }
  print(exSet2)
  ```

  

#### set() 함수

- 파라미터 하나만 허용

#### 예시

- ```python
  aSet = set()
  print("(a)", aSet)
  
  bSet = set([1,2,3,4,5])
  print("(b)", bSet)
  
  cSet = set({1,3,5,7,9})
  print("(c)", cSet)
  
  dSet = set(range(5))
  print("(d)", dSet)
  
  eSet = set((2,4,6,8,10))
  print("(e)", eSet)
  ```

  

#### set 타입 메서드

- set도 하나의 클래스로서, 메서드를 가진다.

- add(), remove() 등

---

### 2. tuple

- ( ) 기호 사용

- `tuple`는 여러 부분 리스트와 매우 유사한데
- 가장 큰 차이점은 `tuple`의 아이템은 **변경이 불가(immutable)**하다는 점입니다.

#### 예시

- ```python
  tempTuple = (1,2,3,4,5)
  
  print(tempTuple)
  type(tempTuple)
  ```

  

- 리스트와 유사한 점
  - tuple[0:3] 과 같이 분할, 복사 등 가능
  
  - ```python
    tempTuple = (1,2,3,4,5)
    
    print(tempTuple[0])
    print(tempTuple[0:3])
    ```
  
    
- 리스트와 다른 점
  - 변경 불가능.
  
  - tuple[0] = 0 같은 것 못함.
  
  - ```python
    tempTuple[0] = 0 # Erron in this statement
    ```
  
    

#### 주의

- 단 하나의 아이템을 갖는 튜플 생성 시 주의

  - (3) 으로 하면, 타입 그냥 정수로 뜸
  - 그냥 괄호로 인식해버리게 된다.

- tuple 아이템의 아이템은 수정 가능

  - `tuple`의 아이템을 수정하면 안되지만, `tuple`의 아이템이 리스트와 같은 data collection type이라면, 이 안의 값은 수정이 가능합니다.
    다음의 예제를 통해서 이를 확인해 봅시다.

    아래의 예제에서 `sampleList[0] = ["Python", 'B']` 구문은 `tuple`의 아이템을 직접 바꾸려고 하기에 에러가 납니다.
    하지만 `sampleList[0][1] = 'A'`은 `tuple`의 **아이템이 아닌, 아이템 안에 포함된 정보의 수정**을 하려는 목적으로 허용됩니다.
    따라서 `tuple`의 아이템이 data collection type이라면, 아이템 자체는 바꿀수 없지만, 해당 아이템이 가진 정보의 수정은 가능한 것입니다.

---

### 3. dictionary

- "단어 : 의미(값)" 으로 저장 = " key : value "

  - 단어 : 중복 불가능 = key
  - 의미 : 중복가능 = value
- 예시


#### 1) 초기화

- { "key" : "value",  "key2" : "value2" }  

 ```python
 langAuthor = {"python":"Guido van Rossum","C++":"Bjarne Stroustrup"}
 print(type(langAuthor), langAuthor)
 ```

#### 2) 사용

- dictionaryName[ 'key값' ]

```python
print(langAuthor['python'])
print(langAuthor['C++'])
```

#### 3) 아이템 변경(=value 변경)

- dictionaryName[ 'key값' ] = "new value값"

```python
langAuthor['C++'] = "Bjarne Stroustrup".upper()
print(langAuthor['C++'])
```

#### 4) 아이템 추가

- dictionaryName[ 'new key값' ] = "new value값"

```python
langAuthor['C++'] = "Bjarne Stroustrup"
print(type(langAuthor), langAuthor)
```

#### 5) 반복문에서 사용하기

- for <key값 받을 변수> in dictionaryName

```python
for item in langAuthor:
    print(item, "is designed by ", langAuthor[item])
```

