📌테이블 컬럼 null 허용 설정    
```SQL    
ALTER TABLE test_table    
ALTER COLUMN test_colum_yn SET NOT NULL;    
```    
    
📌테이블 컬럼 Not Null 설정    
```SQL    
ALTER TABLE test_table    
ALTER COLUMN test_colum_yn DROP NOT NULL;    
```    
✅ SET NULL 이 아닌 DROP NOT NULL 이다!    
