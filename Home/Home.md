```contributionWidget
id: d50cad01-288a-4727-b4ef-2a7fa163a614
type: multi
widgets:
  - id: 4d04964b-cc03-4949-a427-79fe666d093a
    type: markdown
    titleAlign: center
    backgroundStyle: card
    maxHeight: 300
    contentAlign: left
    markdownsSource: content
    markdownValue: |
      <div style=" width: 100%; height:220;overflow: hidden; "><iframe src="https://widget.pkmer.cn/free/ColorfulClock?user=c032e124-df9e-4fe4-a08c-27f90aea6f41&font-color=%234f46e5&ring-color-1=%23e13e78&ring-color-2=%23e79742&ring-color-3=%234483ec&ring-color-4=%238f30eb&lang=zh-cn" allow="fullscreen" style=" height: 100%; width: 100%;"></iframe></div>
    maxWidthRatio: 29
  - id: 4fd8c432-eba1-46bc-b94a-996bd567874f
    type: count
    maxWidthRatio: 25
    query:
      type: page
      filter:
        conditions: []
    title: Totally
    fontColor: "#9dd6ffff"
    backgroundColor: "#00000000"

  - id: 46867d3e-fae3-4c5f-8a15-bd353b05e00f
    type: count
    maxWidthRatio: 25
    query:
      type: page
      filter:
        conditions:
          - type: file_path
            value: Record
            operator: contains
            property: "Record"
            id: 80e996cd-3131-4a2a-b5bb-b28fe0144407
    title: ⭐️Record
    fontColor: "#ffb9b9ff"
    backgroundColor: "#ffffff00"
  - id: 2b4a69cc-0632-431c-93f6-61a666778227
    type: count
    titleAlign: center
    maxWidthRatio: 23
    query:
      type: page
      filter:
        conditions:
          - type: tag
            value:
              - "#NOTE"
            operator: contains
            property: ""
            id: bfd2a60a-935e-4465-a29b-93baddda5af6
    title: MyNOTE
  - id: 9cbf6683-c67d-4e99-ad98-61ec7298a446
    type: countdown
    titleAlign: center
    maxWidthRatio: 21
    repeatType: none
    showEndDateTime: false
    endHour: 0
    endMinute: 59
    endSecond: 59
    timeTextPattern: d
    endYear: 2024
    endMonth: 11
    endDayOfMonth: 31
    title: 今年还剩
backgroundColor: "#00b2ff00"
```

```contributionWidget
id: af68bffe-f2d2-420f-b53c-ff316204d8e8
type: multi
titleAlign: center
backgroundStyle: none
widgets:
  - id: 873512fb-b21a-48f6-82de-b2546ec37b49
    type: multi
    titleAlign: center
    backgroundStyle: none
    widgets:
      - id: c72d5dcb-df4d-49fb-a926-bd341bd1a9f0
        type: quote
        titleAlign: center
        backgroundStyle: card
        maxWidthRatio: 200
        contentType: block
        coverType: url
        filter:
          conditions:
            - type: tag
              value:
                - "#Management"
              operator: contains
              id: 89c7b976-be17-4d9c-9b55-ce0277209bba
        maxHeight: 600
    layoutType: tab
    maxWidthRatio: .nan
```

```contributionWidget
id: af68bffe-f2d2-420f-b53c-ff316204d8e8
type: multi
titleAlign: center
backgroundStyle: none
widgets:
  - id: b6d233d0-ba22-4311-be9b-d10f1bae88c7
    type: multi
    titleAlign: center
    backgroundStyle: none
    widgets:
      - id: 5fe0371b-45d4-4240-b80e-f62c21011932
        type: dataview
        titleAlign: center
        query: |-
          list from !"Workflow/Obsidian/Templaters" where status="UNFINISHED"
        queryType: dataview
        backgroundStyle: card
        maxHeight: 300
        contentAlign: left
        dynamicParamComponents: []
        title: Tasks
      - id: bea4806a-ba0c-4ad4-8975-5bc0230593e8
        type: dataview
        titleAlign: center
        query: |-
          table WITHOUT ID file.link AS "标题",file.mtime as "时间"
          from !"模板" and !"kanban"
          sort file.mtime desc
          limit 16
        queryType: dataview
        backgroundStyle: card
        maxHeight: 300
        contentAlign: center
        dynamicParamComponents: []
        title: |-
          👨🏻‍💻
          最近编辑
        backgroundColor: "#1e1e2eff"
        maxWidthRatio: 100
      - id: 084f1b01-c906-42aa-b81b-41043b5bbf67
        type: dataview
        titleAlign: center
        query: |
          table file.ctime as 创建时间
          from ""
          where date(today) - file.ctime <=dur(7 days)
          sort file.ctime desc
          limit 16
        queryType: dataview
        backgroundStyle: card
        maxHeight: 300
        contentAlign: left
        dynamicParamComponents: []
        title: |-
          📚
          一周内创建的笔记
        backgroundColor: "#1e1e2eff"
        maxWidthRatio: 100
    layoutType: tab
    maxWidthRatio: 97.31040246696544
  - id: 873512fb-b21a-48f6-82de-b2546ec37b49
    type: multi
    titleAlign: center
    backgroundStyle: none
    widgets:
      - id: c72d5dcb-df4d-49fb-a926-bd341bd1a9f0
        type: quote
        titleAlign: center
        backgroundStyle: card
        maxWidthRatio: 200
        contentType: block
        coverType: url
        filter:
          conditions:
            - type: tag
              value:
                - "#NOTE"
              operator: contains
              property: ""
              id: 89c7b976-be17-4d9c-9b55-ce0277209bba
        maxHeight: 300
      - id: d517d4b9-b6ac-48dd-b5ec-718adf9790d5
        type: dataview
        titleAlign: center
        query: |
          TABLE  file.tags,file.ctime
          from "" where 
          contains(file.name, "{{fileName}}") and contains(file.tags, "{{tag}}") sort createTime desc
          limit 6
        queryType: dataview
        backgroundStyle: card
        maxHeight: 300
        contentAlign: center
        dynamicParamComponents:
          - id: 2500cb12-d830-496a-8a6c-d72e9f52906d
            type: text
            name: fileName
            defaultValue: ""
            placeholder: ""
            fromProperty: ""
            label: FileName
          - id: 1c3cf833-405e-460f-b8da-817aa07e4e1e
            type: text
            name: tag
            defaultValue: ""
            placeholder: ""
            fromProperty: ""
            label: SearchTag
        title: 🔍Compound Search
        maxWidthRatio: 100
      - id: 71673572-c7b8-40f7-a1b3-3fdaa984ee88
        type: dataview
        titleAlign: center
        maxWidthRatio: -1
        query: |-
          table from "Record" 
          
        queryType: dataview
        backgroundStyle: card
        maxHeight: 300
        dynamicParamComponents: []
        title: Record
    layoutType: tab
    maxWidthRatio: .nan
```

```contributionWidget
id: ca104698-835f-41dd-b519-6c5d6ad26a71
type: dataview
titleAlign: center
query: |-
  let month = moment().format('MM')
  let date = moment().format('MMDD')
  let url = `https://baike.baidu.com/cms/home/eventsOnHistory/${month}.json`
  let res = await request({url: url,method: "GET"});
  let data = JSON.parse(res)
  dv.table(
   ['年度','事件','链接'],
   data[month][date].slice(0,100).map(p=>[p.year,p.title,`[Visit](${p.link})`])
  )
queryType: dataviewjs
backgroundStyle: card
maxHeight: 300
contentAlign: center
dynamicParamComponents: []
title: 历史上的今天
maxWidthRatio: 100
```

```contributionWidget
id: fc1a89a8-74a8-4f19-b246-5b607f9a8b0c
type: dataview
titleAlign: center
maxWidthRatio: -1
query: |-
  // 日期格式化
  const dateFormat = "YYYY-MM-DD"
  // 表头：期望的展示的属性列表
  const headers = ["status"]
  // 当前页码
  const pageNum = {{pageNum}};
  // 单页数量
  const pageSize = {{pageSize}};
  // 文件名称
  const pageTitleLike = "{{pageTitle}}"
  // 标签
  const tagLike = "{{tag}}"
  const tagMatch = (page, tag) => {
    if (tag) {
     return page.file.tags && page.file.tags.some(t => t.includes(tagLike))
    }
    return true;
  }

  const data = dv.pages("")
  .where(p => p.file.name?.toLowerCase().includes(pageTitleLike?.toLowerCase()))
  .where(p => tagMatch(p, tagLike))
  .sort(p => p.file.ctime, "{{sort}}")
  .map(p => {
    return [p.file.link, ...headers.map(property => p[property]), moment(Number(p.file.ctime)).format(dateFormat), p.file.size];
  })

  const pageData = data.slice((pageNum - 1) * pageSize, pageNum * pageSize)
    .limit(pageSize)
  dv.paragraph("共有 " + data.length +" 条数据")
  dv.table(["name", ...headers, "ctime", "size"], pageData)
queryType: dataviewjs
backgroundStyle: card
maxHeight: 300
dynamicParamComponents:
  - id: de132a8e-cd12-4a05-b6e3-9ef62263b337
    type: text
    name: pageTitle
    defaultValue: ""
    placeholder: ""
    fromProperty: ""
    label: 标题
  - id: e678f322-6aee-4888-b888-98d330a155bb
    type: text
    name: tag
    defaultValue: ""
    placeholder: ""
    fromProperty: ""
    label: 标签
  - id: 2c45ff87-4308-4f1b-a734-f2f503416bbe
    type: number
    name: pageNum
    defaultValue: "1"
    placeholder: ""
    fromProperty: ""
    label: 页码
  - id: 14029232-94ca-41cf-bdc8-956fee52f68d
    type: number
    name: pageSize
    defaultValue: "10"
    placeholder: ""
    fromProperty: ""
    label: 数量
  - id: ac3276ef-c501-4579-bb96-47e9b7828105
    type: select
    name: sort
    defaultValue: desc
    placeholder: ""
    fromProperty: ""
    label: 文件创建时间排序
    options:
      - id: 0d7ff531-2802-4ba7-823c-cb592499adc4
        label: 降序
        value: desc
      - id: 57a84f2b-66ae-4ef4-8fce-690248a87518
        label: 升序
        value: asc
title: 复合检索

```



```contributionGraph
title: ""
graphType: month-track
dateRangeValue: 3
dateRangeType: LATEST_MONTH
startOfWeek: 1
showCellRuleIndicators: true
titleStyle:
  textAlign: center
  fontSize: 22px
  fontWeight: normal
dataSource:
  type: PAGE
  value: ""
  dateField: {}
  countField:
    type: DEFAULT
fillTheScreen: true
enableMainContainerShadow: false
cellStyleRules:
  - id: Halloween_a
    color: "#fdd577"
    min: 1
    max: 2
  - id: Halloween_b
    color: "#faaa53"
    min: 2
    max: 3
  - id: Halloween_c
    color: "#f07c44"
    min: 3
    max: 5
  - id: Halloween_d
    color: "#d94e49"
    min: 5
    max: 9999
mainContainerStyle:
  backgroundColor: "#1E1E2E"
  boxShadow: rgba(0, 0, 0, 0.16) 0px 1px 4px

```

```contributionWidget
id: 0beb4e2e-f32e-4d3b-a560-2f4eac94f5a7
type: dataview
titleAlign: center
maxWidthRatio: -1
query: |-
  // 日期格式化
  const dateFormat = "YYYY-MM-DD"
  // 表头：期望的展示的属性列表
  const headers = ["status"]
  // 当前页码
  const pageNum = {{pageNum}};
  // 单页数量
  const pageSize = {{pageSize}};
  // 文件名称
  const pageTitleLike = "{{pageTitle}}"
  // 标签
  const tagLike = "{{tag}}"
  const tagMatch = (page, tag) => {
  	if (tag) {
  		return page.file.tags && page.file.tags.some(t => t.includes(tagLike))
  	}
  	return true;
  }

  const data = dv.pages("")
    .where(p => p.file.name?.toLowerCase().includes(pageTitleLike?.toLowerCase()))
    .where(p => tagMatch(p, tagLike))
    .sort(p => p.file.ctime, "{{sort}}")
    .map(p => {
  	  return [p.file.link, ...headers.map(property => p[property]), moment(Number(p.file.ctime)).format(dateFormat), p.file.size];
    })
  const pageData = data.slice((pageNum - 1) * pageSize, pageNum * pageSize)
    .limit(pageSize)
  dv.paragraph("共有 " + data.length +" 条数据")
  dv.table(["name", ...headers, "ctime", "size"], pageData)
queryType: dataviewjs
backgroundStyle: card
maxHeight: -1
dynamicParamComponents:
  - id: 93051e03-f464-4c32-8108-d76e88d2c228
    type: text
    name: pageTitle
    defaultValue: ""
    placeholder: ""
    fromProperty: ""
    label: 标题
  - id: 9c15e095-f9ee-4e10-ace0-033576c7c678
    type: tagSuggestions
    name: tag
    defaultValue: ""
    placeholder: ""
    fromProperty: ""
    label: 标签
  - id: 0b0999b1-2abe-4cba-90f3-407bff00e53e
    type: number
    name: pageNum
    defaultValue: "1"
    placeholder: ""
    fromProperty: ""
    label: 页码
  - id: 07739f36-696d-4d8e-ba6b-52449507de5a
    type: number
    name: pageSize
    defaultValue: "20"
    placeholder: ""
    fromProperty: ""
    label: 数量
  - id: 0e5f37e4-162f-4698-9442-07b81017f62b
    type: select
    name: sort
    defaultValue: desc
    placeholder: ""
    fromProperty: ""
    options:
      - id: a0c29755-1fbf-4750-b5bd-79c99982dc3d
        label: 降序
        value: desc
      - id: bac80e8a-3260-4502-858e-f7b004e3b8d6
        label: 升序
        value: asc
    label: 文件创建时间排序
title: Search
```

