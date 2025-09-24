---
Aliases: [ "#🫎Archive" ]
---
## Sub Tags
```dataview
TABLE Without Id
  file.aliases
, file.link                                as "태그페이지"
, dateformat(file.ctime, "yyyy-MM-dd")     as "생성일"
from ""
where length(file.aliases) > 0
 and contains(file.aliases,"🫎Archive/")
 sort file.aliases
```

## Pages

```dataview
TABLE Without ID
      link(file.name)                          as "파일"
    , file.properties.Objective
    , dateformat(file.ctime, "yyyy-MM-dd")     as "생성일"
FROM ""
FLATTEN substring(file.etags, 1) as etag
where etag = "🫎Archive"
SORT etag, file.ctime desc
```
