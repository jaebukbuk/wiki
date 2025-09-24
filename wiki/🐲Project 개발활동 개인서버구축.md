---
aliases:
  - "#🐲Project/개발활동/개인서버구축"
---
## Sub-Item
```dataview
TABLE Without Id
  file.aliases
, file.link                                as "태그페이지"
, dateformat(file.ctime, "yyyy-MM-dd")     as "생성일"
from ""
where length(file.aliases) > 0
 and contains(file.aliases,"🐲Project/개발활동/개인서버구축/")
 sort file.aliases
```


# Overview

- 개인서버는 지금 만들어놓은 서버 컴퓨터에
- ubunto / Docker 
-  + nginx
-  + postgresql
-  + react + next js
-  + java
기반의 프로그램을 만드는것이 목표이다

기한은 12월 안으로 하면 될듯?
