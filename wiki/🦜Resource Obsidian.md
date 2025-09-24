---
aliases:
  - "#🦜Resource/Obsidian"
---
## Pages

```dataview
TABLE Without ID
      link(file.name)                          as "파일"
    , file.properties.Objective
    , dateformat(file.ctime, "yyyy-MM-dd")     as "생성일"
FROM ""
FLATTEN substring(file.etags, 1) as etag
where etag = "🦜Resource/Obsidian"
SORT etag, file.ctime desc
```
