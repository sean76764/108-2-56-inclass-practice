---
title: "homework 6"
output: html_document
params:
  studentName: "你的名字"
  studentID: "你的學號"
editor_options: 
  chunk_output_type: console
---

# 注意事項

存檔與填寫注意事項：

假設你叫王小明，學號41078392。

  1. 有些同學可能家裡電腦不是utf-8設定，為防萬一，請於存檔時使用：File > save with enconding, 然後選utf-8

  2. 本文檔開始的Frontmatter中，studentID（即key）其value目前為"你的學號"，以上面學號為例則必需改成"41078392"；而studentName（key）其value目前為"你的名字"，以上面名字為例則必需改成"王小明"
  
> 每次作業滿分10分：有寫作業於期限內上傳得3分，剩餘7分依作業準確率決定最後得分多寡，除非該題另有規定。

> 前述存檔與frontmatter要求缺任何一個則扣1分。

請先執以下code chunk, 引入所需packages，答案禁止引用其他套件（Package）。


# 題目

## 1. 所得層級別消費者物價指數

資料來源：<https://data.gov.tw/dataset/6020>



### 1.1 認識你的資料物件
查詢cpiByIncome的元素名稱，並存在names_element1 (class character)


### 1.2 對每個元素進行粹取
取出cpiByIncome裡每個Item元素並以factor形式存在items物件（class factor）。（map回傳的值一定是list，所以有時要適時unlist它）


### 1.3 建立家庭分類
建立一個family_type物件(class factor), 每個元素分別代表items裡每個元素來於「全體家庭」、「最低20%所得家庭」、「中間60%所得家庭」、「最高20%所得家庭」（「」內為family_type可能level值及它們的排序）


### 1.4 建立子類
建立一個subcategory物件(class factor), 每個元素分別代表items裡每個元素來於「一.食物類」、「二.衣著類」、...、「七.雜項類」、「總指數」（「」內為subcategory可能level值, 無需管排序）


### 1.5 levels排序
將subcategory的levels依「一.食物類」、「二.衣著類」、...、「七.雜項類」、「總指數」排序。（答案物件是subcategory本身）


### 1.6 篩選資料
由cpiByIncome選出元素值的TYPE為"原始值"的元素，存在答案物件cpiValues ( class list, list of 15104 elements)


### 1.7 建立新資料
由cpiValues建立allCPIdata（class list，list of 4 elements）裡面的4個元素分別是
  
  * TIME_PERIOD：cpiValues$TIME_PERIOD, 由原始值加上日期"01"的日期值，且為Date class。
  
  * Item_VALUE：來自cpiValues$Item_VALUE，為class numeric。
  
  * family_type
  
  * subcategory
  
後兩個均源自前面小題。以上每個元素長度均為15104。


### 1.8 日期篩選
留下allCPIdata中介於2011-01-01至2018-12-01的資料存在allCPIdata2（class list，且四個元素的長度只剩3072）



### 1.9 不同家庭面臨的物價上漲率

由allCPIdata2建立cpiGrowth_eachFamily（class list, list of 4 elements），裡面有四個元素其名稱為「全體家庭」、「最低20%所得家庭」、「中間60%所得家庭」、「最高20%所得家庭」，而個別元素值分別為此類家庭2018-12-01與2011-01-01的"總指數"CPI比例。


結語：不知道同學有沒有發現所得越低的家庭，其面臨的物價水準上漲速度較快。希望在資料探索的過程中你有發現社會經濟面的一些問題，找到原因和解決問題的方法。