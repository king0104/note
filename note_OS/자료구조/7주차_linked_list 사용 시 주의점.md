### linked list

- node와 linked list 라는 타입 정의하기
  - 멤버변수가 public으로 설정되어있어야 한다!!!!!1
  - class로 정의할 경우 - 맨 위에 public 붙이기
  - struct로 정의할 경우 - 기본값이 public



- 초기화 되어있는 LL은 **head가 NULL** 이다. 그래서 graph[i].head는 맨 처음에 null 임을 주의하자. 일단 값을 삽입해야지 head가 null이 아니다?



- **모든 노드는 포인터로 접근한다.** 이것을 생각하면 코딩하기 편할 것이다.
  - 다른 타입에서는 노드번호(int)로 노드에 접근해서, for문에서 iteration variable이 int i 였다. LL에서는 **포인터로 노드에 접근**하기 떄문에, **iteration variable을 node *i** 와 같이 지정하면 된다. 



- 화살표의 의미
  - **포인터가 가리키는 공간에 접근했다!** 라는 뜻. 그 다음 작업 바로 가능
  - 포인터로 노드에 접근하기 더 쉽게 하는 것이다.
  - 포인터는 해당 공간의 주소이기 때문에, 해당 공간에 접근하려면 (*p)를 한 후 그 다음 작업을 해야하는데, p->를 사용하면 해당 공간에 접근했다는 의미를 지닌다.