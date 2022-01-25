- DDL

```java
create table user
(
    id   int  not null
        auto_increment primary key,
    name varchar(20) null,
    age  int         null
);
```

- auto_increment는 int형만 가능
- **@GeneratedValue(strategy = GenerationType.IDENTITY) 와  DDL의 auto_increment는 세트**임을 명심하자!!

