### Postgresql 테이블 Comment 추가  
```SQL  
COMMENT ON COLUMN test_table.test_colum_yn IS '테스트 컬럼 입니다.';  
```  
  
### PostgreSql 은 컬럼 추가시 Commnet 정보를 바로 입력할수 없다.  
```SQL  
ALTER TABLE test_table ADD test_colum_yn numeric NULL  
COMMENT ON COLUMN test_table.test_colum_yn IS '테스트 컬럼 입니다.';  
```  
-> 해당 쿼리는 Alter table add 문 이후에 바로 Comment 문이 추가된 SQL 으로 PG에서는 오류가 발생한다.   
![Pasted image 20251204133000.png](../../99.%20File/Pasted%20image%2020251204133000.png)  
-> 따라서  
```SQL  
ALTER TABLE test_table ADD test_colum_yn numeric NULL;  
COMMENT ON COLUMN test_table.test_colum_yn IS '테스트 컬럼 입니다.';  
```  
-> 두개의 SQL문으로 컬럼 Comment를 추가 해야한다.