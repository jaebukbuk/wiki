📌테이블 컬럼명 변경 쿼리      
```SQL      
ALTER TABLE test_table      
RENAME COLUMN test_colum_yn2 TO test_colum_yn3      
```      
✅ old_column To new_column_name      
✅ 컬럼명 변경시 기존 old_column 의 Comment는 삭제 된다. 