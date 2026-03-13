📌 테이블, 함수, 시퀀스 DROP 문          
```SQL          
DROP TABLE    IF exists test_table          
DROP FUNCTION IF exists test_Function          
DROP SEQUENCE IF exists test_squence          
          
/*           
* db Object 미 존재시 해당 결과 출력          
* table "test_table" does not exist, skipping          
*/          
```          
✅ IF Exists 문을 사용하여 안전하게 처리한다.          
