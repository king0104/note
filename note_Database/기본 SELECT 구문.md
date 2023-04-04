# SELECT에서 필요한 것들

- LIKE
  - 특정 문자가 포함되어있는지 검색하기 위해 사용
  - WHERE ri.address **LIKE '서울%'**



- ORDER BY
  - ORDER BY 컬럼명 **DESC**
  - 여러개는 이어서 작성
    - ORDER BY **avg(rr.review_score) DESC, ri.favorites DESC**



- 반올림	
  - round(avg(rr.review_score),2)