---
aliases:
  - "#🐲Project/개발활동/개인서버구축/Docker강의"
tags:
---
# Tag 내용



# Pages

```dataview
TABLE Without ID
      link(file.name)                          as "파일"
    , file.properties.Objective
    , dateformat(file.ctime, "yyyy-MM-dd")     as "생성일"
FROM ""
FLATTEN substring(file.etags, 1) as etag
where etag = "🐲Project/개발활동/개인서버구축/Docker강의"
SORT etag, file.ctime desc
```
