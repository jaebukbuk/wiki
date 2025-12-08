📌컬럼 데이터 타입 변경  
```SQL  
ALTER TABLE test_table  
ALTER COLUMN test_colum_yn TYPE VARCHAR(10);  
  
// ALTER COLUMN (컬럼명) TYPE (변경할 데이터 타입)(길이)  
```  
✅ 기존 컬럼에 정의된 속성들은 변경없이 컬럼 데이터 타입만 변경된다.  
  
  
📌 매핑 로직을 통한 컬럼 데이터 타입 변경  
```SQL  
ALTER TABLE test_table  
ALTER COLUMN test_colum_yn TYPE Boolean;  
  
/*  
// 타입 변경 불가로 인한 오류!  
SQL Error [42804]: ERROR: column "test_colum_yn" cannot be cast automatically to type boolean  
  Hint: You might need to specify "USING test_colum_yn::boolean".  
    
// defalut 값 설정으로 인한 오류!  
ERROR: default for column "test_colum_yn" cannot be cast automatically to type boolean  
*/  
```  
✅ 동일 타입 으로 변경시에는 별도의 작업 없이 SQL 이 동작 하지만 컬럼데이터 타입이 자동으로 변경되기 어려운 경우 등 '별도의 작업이 필요한 경우' 오류가 발생한다.  
(자동 형변환 불가 또는 매핑 로직 필요)  
  
```SQL  
ALTER TABLE test_table  
ALTER COLUMN test_colum_yn TYPE boolean USING (test_colum_yn = 'Y')::boolean ;  
  
/***************************************************  
* -> Using 절의 표현식은  
* select (test_colum_yn = 'Y')::boolean from test_table  
* 과 같이 진행하여 확인한다.  
*****************************************************/  
```  
✅ USING 표현식을 이용하여 해당 컬럼 데이터를 매핑하는 구문을 통해 타입변경을 진행할수 있다.  
