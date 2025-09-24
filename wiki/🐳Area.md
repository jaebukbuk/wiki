---
aliases:
  - "#🐳Area"
---
# Sub Tags
```dataview
TABLE Without Id
  file.aliases
, file.link                                as "태그페이지"
, dateformat(file.ctime, "yyyy-MM-dd")     as "생성일"
from ""
where length(file.aliases) > 0
 and contains(file.aliases,"🐳Area/")
 sort file.aliases
```

# AREA란?

- Area of Resonsiblity, 책임의 영역
- 목표와 데드라인이 없지만 꾸준히 관리해야할것들
-  EX) 개발, 
--> 정체성
