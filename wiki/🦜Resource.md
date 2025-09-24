---
aliases:
  - "#🦜Resource"
---
# Sub Tags
```dataview
TABLE Without Id
  file.aliases
, file.link                                as "태그페이지"
, dateformat(file.ctime, "yyyy-MM-dd")     as "생성일"
from ""
where length(file.aliases) > 0
 and contains(file.aliases,"🦜Resource/")
 sort file.aliases
```
