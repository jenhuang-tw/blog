---
title: 《法學期刊引註格式凡例》的 BibLaTeX 語法片段
date: 2025-12-01 16:12:54
updated:
categories: 技術
tags:
- LaTex
---


這篇文章列出搭配[《法學期刊引註格式凡例》 CSL](https://github.com/jenhuang-tw/csl-nstc-law) 使用的 BibLaTex 格式語法。

如果因為刊物仍要求輸出參考文獻，需要填寫 CSL number-of-pages 變數值作為作者姓氏筆畫數以排序，請自行增加一個 pagetotal 值。例如，作者姓陳，姓氏筆畫數為 10，則請增列 `pagetotal={10},`（建議填寫在最後）。

以下片段並非採用《凡例》的刊物所提供，並不擔保輸出正確。

## 2.7 有具體篇名之論文

### 2.7.1 收錄於期刊之論文

```
@article{ChenCW2023,
  language = {zh},
  author = {{陳淳文}},
  title = {參與行政之法制架構初探},
  journal = {東吳法律學報},
  volume = {34},
  number = {4},
  year = {2023},
  month = {4},
  pages = {63--117},
}
```

### 2.7.2 收錄於專書之論文

編者非作者

```
@incollection{ChenAE2000,
  language = {zh},
  author = {{陳愛娥}},
  title = {基本權作為客觀法規範─以「組織與程序保障功能」為例，檢討其衍生的問題},
  editor={{李建良} and {簡資修}},
  booktitle = {憲法解釋之理論與實務（第二輯）},
  address = {臺北市},
  publisher = {中央研究院中山人文社會科學研究所},
  year = {2000},
  pages = {235--272},
}

如果「編者同作者」，不填寫 editor 參數即可。

@incollection{ChenCS2007a,
  language = {zh},
  author = {{陳春生}},
  title = {行政法上之參與及合作},
  booktitle = {行政法之學理與體系(二)},
    address = {臺北市},
  publisher = {元照},
  year = {2007},
  pages = {63--90},
}
```

## 2.8 書籍等

### 2.8.1 由個人獨立著作之書籍

```
@book{DengYS2023,
  language = {zh},
  author = {{鄧衍森}},
  title = {國際人權法理論與實務},
  publisher = {元照},
  year = {2023},
  edition = {3},
}
```

（按：出版社並非《凡例》要求註明的項目）

### 2.8.2 由多人共同著作之書籍

<!-- #### 2.8.2.1 有編者但無篇名(如教科書、專論等)
【格式】編者,書名,版次(初版無須註明),頁碼(作者執筆),出版年。
【例】臺灣勞動法學會,勞動基準法釋義──施行 40 年之回顧與展望,頁 642-657
(林佳和執筆),2024 年。

#### 2.8.2.2 一位作者,並有續著/修訂/校訂者時 -->

#### 2.8.2.3 多人列為作者時

```
@book{ChenCW_WuG_2025,
  language = {zh},
  author = {{吳庚} and {陳淳文}},
  title = {憲法理論與政府體制},
  publisher = {三民},
  year = {2025},
  edition = {9},
}
```

（按：出版社並非國科會要求註明的項目）

## 2.10 碩博士論文

```
@phdthesis{MaRC2014,
  language = {zh},
  author = {{馬若慈}},
  title = {論兒童陳述意見之權利：以兒童權利公約為核心},
  school = {國立臺灣大學法律學系},
  type = {碩士論文},
  year = {2014},
}
```

## 2.11 翻譯著作

```

@book{Schlaich_Korioth,
  language = {zh},
  author = {{Klaus Schlaich} and {Stefan Korioth}},
  translator = {{吳信華}},
  title = {聯邦憲法法院：地位、程序、裁判},
  year = {2017},
  edition = {1},
  publisher = {元照},
  pagetotal={02},
}
```

## 2.12 報紙

### 2.12.2 網路報紙

各參數的說明請見「網路文獻」一節。

```
@online{udn20230529,
	language = {zh},
	author = {{鄭媁}},
	title = {國民教育法修正案三讀通過 中小學生代表列席校務會議},
	journal = {聯合新聞網},
	date={2023-05-29},
	urldate={2025-03-18},
	url = {https://udn.com/news/story/6885/7197760},
```

## 2.13 公報

```
@report{LYGazette2024,
  language = {zh},
  author = {立法院公報},
  title = {113卷87期，2冊},
  year = {2024},
}
```

政府文件（僅供參考。《凡例》未列入）
```
@misc{National_Span_Plan,
  language = {zh},
  author = {內政部},
  title = {全國國土計畫},
  year={2018},
}
```

## 2.15 網路文獻
### 2.15.1 無提供 Archive URL 者
```
@online{DaiXX2024,
	language = {zh},
	author = {{戴秀雄}},
	title = {【投書】盡快為土地利用失序止血，國土計畫不應因人為風雨延宕實施},
	url = {https://www.twreporter.org/a/opinion-spatial-planning-act-should-come-into-effect-on-time},
	journal = {報導者},
	date = {2024-09-26},
	urldate = {2025-10-12},
} 
```

【說明】 `date` 為原網頁日期， `urldate` 為最後瀏覽日。