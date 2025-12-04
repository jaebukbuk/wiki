📌 테이블 삭제 쿼리  
```SQL  
ALTER TABLE test_table  
DROP COLUMN IF EXISTS test_colum_yn3;  
```  
-> CASCADE, 여러 컬럼 동시 삭제 등 DROP 옵션이 존재하지만 꼼꼼하게 하나씩 확인 하면서 진행하자!  
  
✔️ IF EXISTS (컬럼명)   
-> 해당 테이블에 컬럼명 존재 확인후 DROP COLUMN 실행  
![Pasted image 20251204140655.png](../../99.%20File/Pasted%20image%2020251204140655.png)  
-> 없으면 SKIP 한다!  
  
