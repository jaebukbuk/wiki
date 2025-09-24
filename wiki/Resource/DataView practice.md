---
날짜: 2025-04-28
tags:
  - "#🦜Resource/Obsidian"
---

# Sub Tages

```dataview
table Without Id
      tags                                        as "하위 태그"
    ,  link( substring(replace(tags,"/"," "), 1)) as "태그 페이지"
    , length(rows.file.link)                      as "하위 페이지 수"
FROM ""
FLATTEN file.tags AS tags 
WHERE file.tags
  and contains(tags,"Project/개발활동/개인서버구축/Docker강의/")
GROUP BY tags
SORT length(rows.file.link) DESC
```

# All Sub Tag Pages

```dataview
TABLE Without ID
      link(file.name)                          as "하위 태그 파일"
    , "#"+etag                                 as "하위 태그"
    , link( replace(etag,"/", " ") )           as "하위 태그 페이지"
    , dateformat(file.ctime, "yyyy-MM-dd")     as "생성일"
FROM ""
FLATTEN substring(file.etags, 1) as etag
where contains(etag, "Project/개발활동/개인서버구축/Docker강의/")
SORT etag, file.ctime desc
```




```dataview
TABLE WITHOUT ID (tag + "(" + length(rows.file.link) + ")") AS Tags, join(rows.file.folder) AS Folder, join(rows.file.link, ", ") AS Files
FROM ""
WHERE file.tags
FLATTEN file.tags AS tag
GROUP BY tag
SORT length(rows.file.link) DESC
```

## [[🐤HomePage]] main dataView

```dataview
table without id
link( substring(replace(tags,"/"," "), 1)) as TagPage
   , tags as search_Tag
   , file
FROM ""
WHERE file.tags
FLATTEN file.tags AS tags 
GROUP BY tags
SORT length(rows.file.link) DESC
```


## tag page number
```dataview
TABLE 
length(rows.file.link) as "Number"
FLATTEN file.tags as tag
GROUP BY tag
```

## tag page number
```dataview
TABLE 
  aliases
, files.link
FLATTEN file as files
FLATTEN file.aliases as aliases
GROUP BY aliases
```

## tag page number
```dataview
TABLE 
  file.name
, file.link
from ""
where length(file.aliases) > 0
```

## 파일 객체 

```dataview
table file
where file.name ="Project"
```



## 맵을 이용한 예제인데 잘모르겠음


```dataview
TABLE file.tags, file.etags, any(mappedTags), all(mappedTags)
  
FROM ""
FLATTEN list( map(this.file.etags, (tag) => contains(file.etags, tag))) as mappedTags
LIMIT 20
```


## 태그 이름 조작
```dataview
table WITHOUT ID (tag + "(" + length(rows.file.link) + ")") AS Tags, join(rows.file.folder) AS Folder, join(rows.file.link, ", ") AS Files
FROM ""
WHERE contains(tags, "#Project")
FLATTEN file.tags AS tag
GROUP BY tag
SORT length(rows.file.link) DESC
```


## 태그 레벨 확인

```dataview
TABLE etag, level 
FROM ""
FLATTEN substring(file.etags, 1) as etag
FLATTEN split(etag, "/") as level
 
```