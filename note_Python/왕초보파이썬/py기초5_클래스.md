### 클래스

- attriubte = 멤버변수
- method = 메서드



- new 안씀
- className(param, ..) 으로 생성
- this  대신 self

#### 예시

```python
class Student:
    id = 0
    name = ''
    
student1 = Student()
student2 = Student()

student1.id = 20190001
student1.name = "Harry Potter"

student2.id = 20190002
student2.name = "Hermione Granger"
```



#### 생성자

-  \__init__() 함수 사용

- 

- ```python
  class Student:
      def __init__(self):
          self.id = 0
          self.name = ''
  ```



#### \__str__() 함수

- toString() 을 오버라이딩 한 것과 같다.

- ```python
  def __str__(self):
      msg = "id:{}, name:{}".format(self.id, self.name)
      return msg
  ```



#### 클래스 변수 & 인스턴스 변수

#### private 변수

- __ 를 변수 앞에 붙이면 된다.

- ```python
  class Student:
      # Class variables
      __countStudent = 0
  ```

  