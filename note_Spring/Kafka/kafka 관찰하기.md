#### messages in per topic

- 데이터 수 : 1e4
- 쓰레드 수
  - 1개 : 222 req/s
  - 4개 : 815 req/s



- 데이터 수 : 1e8
- 쓰레드 수
  - 1개 : 35.5K req/s
  - 4개 : 35.9K req/s



#### produce request per broker

- 데이터 수 : 1e8
- 쓰레드 수
  - 1개 : 115 req/s
  - 4개 : 116 req/s



#### bytes In / Out per broker

- 데이터 수 : 1e8
- 쓰레드 수
  - 1개
    - bytes out : 23.3 kB/s
    - bytes in : 1.89 MB/s
  - 4개
    - bytes out : 23.4 kB/s
    - bytes in : 1.88 MB/s



- 들어오는 바이트 수가 훨씬 큰 것을 알 수 있다.

- 1억개에서는.. 쓰레드 4개와 1개 차이가 없네요..?(1억개 전부를 돌리지는 않음)

- 여기서 뭘 알아야 하는지 알려주세요!
  - 브로커 수 늘리기? 이런건가요??