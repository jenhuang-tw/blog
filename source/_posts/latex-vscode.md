---
title: LaTex 在法學寫作的運用 
date: 2025-09-07 20:00:00
updated: 
categories: 技術
tags:
- LaTex
- VS Code
---

申請大專生計畫時，被引註格式搞得很痛苦（用 Word 的交互參照手刻中研院法學期刊格式），後來寫成果報告，決定升級使用 LaTex。

## VS Code 設定

原本打算用 Overleaf 就好了，但法學引註格式出了名地繁瑣，單純的 BibLaTeX 根本無法處理；雖然在網路上找到 Zeping Lee 開發的 [citation-style-language](https://ctan.org/pkg/citation-style-language) 模組，但無法在 Overleaf 完成編譯。最後只好在本地寫，再配合 Git + GitHub 做版本控制。所以，也和寫其他程式時一樣，我就用 Visual Studio Code 來寫 LaTex。

最近換筆電，全部設定又得重來，就順便記錄在這裡。主要的參考文獻是這一篇：[使用 VSCode 上撰寫中文 LaTex 文件](https://kaibaoom.tw/posts/notes/vscode-latex/)。

編譯工具通常會推薦 MikTex 或 TexLive 二選一。我的研究方法基本上是傳統法釋義學，並沒有用到社會科學的研究方法，也就不太需要數學公式、圖片之類的套件。由於後者會一次安裝非常多種套件，我選擇的是前者，在編譯時發現所需套件尚未安裝，才會詢問使用者是否需要安裝。MikTex 可以到[官方網站](https://miktex.org/)下載、安裝。Install 封裝檔有點大（138.07 MB），要等一段時間。

安裝完後，由於 LaTex 運行還需要 Perl，可安裝 [StrawberryPerl](https://strawberryperl.com/)，並將之加入系統環境變數。還有設定 VS Code 與安裝 LaTex Workshop 的步驟，這部分都可以參考上述〈使用 VSCode 上撰寫中文 LaTex 文件〉文章。

與文中不同的是，為了配合引註使用 citation-style-language 模組，Recipe 第一順位請選擇 LuaLatex 。

完成上述步驟後，應該就具備了基本需要的軟體，可以打開 VS Code ，來寫文章了。這部分前引文章也有教學，接下來有所不同的是，為了配合中文排版與法學引註格式需求，所更改的設定。

## LaTex 設定

### 繁體中文排版支援

首先，該文的 LaTex 文件設定是 `\documentclass{article}`，我們改為使用 `\documentclass{ctexart}`。但因 cTex 主要開發者是簡體中文社群，必須要特別設定繁體中文支持，這部分請參考[在 LaTeX 建立中文文件](https://kuaz.info/posts/2023/01/latex-tutorial-part-ctex/)一文的教學。

### CSL 支援

LaTex 較常使用的參考文獻、引註模組是 BibTeX 或 BibLaTeX，但因現有方法無法滿足法學引註的需求，我個人使用的是 Zeping Lee 開發的 [citation-style-language](https://ctan.org/pkg/citation-style-language) 模組。有關該模組的使用，可以自行參閱說明文件。

基於個人需求，我也改寫了 Zeping Lee 開發的「[法学引注手册（多语言）](https://zotero-chinese.com/styles/%E6%B3%95%E5%AD%A6%E5%BC%95%E6%B3%A8%E6%89%8B%E5%86%8C%EF%BC%88%E5%A4%9A%E8%AF%AD%E8%A8%80%EF%BC%89/)」引註格式，依國科會人文處法律學門 2025 年 7 月 10 日版《法學期刊引註格式》（目前只支援中文版常見文獻類型，英、日、德、法文獻都還是原本中國大陸的《法学引注手册》格式），製作 [csl-nstc-law](https://github.com/jenhuang-tw/csl-nstc-law) CSL 格式。

以下，就以這個格式為例，展示使用結果。

1、文件設定

```tex
\usepackage{citation-style-language}
\cslsetup{style = nstc-law-journal} % nstc-law-journal public-law
\addbibresource{ref.bib} %Imports bibliography file
```

2、參考文獻來源

```tex
@article{QiuWY2025,
	language = {zh},
	author = {{邱文彥}},
	title = {國土計畫法：回顧與展望},
	journal = {當代法律},
	number = {38},
	pages = {6--14},
	year = {2025},
	month = {2},
}
```

3、內文引註

```tex
邱文彥教授〈國土計畫法：回顧與展望〉一文，略述……挑戰\cite[page={6-14}]{QiuWY2025}。
```

4、呈現成果

![](/img/screenshot-of-csl-nstc-law.webp)

## 關於參考文獻排序

原先找不到較常見需求（先依文獻語言別排，中文再按姓氏筆畫、英文按字母序）排序參考文獻的調整方式，只好參考文獻前強制換頁，然後將 LaTex 產生的參考文獻複製到另外一個 Word 檔案，手動調整順序，再合併兩個 PDF 檔。

更新：在僅參考中文文獻的前提下（不需要區分不同語言別文獻），以下的方法應該可以撐得過去。

1、區分類型輸出參考文獻

```tex
\addcontentsline{toc}{section}{參考文獻}
\section*{參考文獻}

\printbibliography[type=book, title={專書}]
\printbibliography[type=article-journal, title={期刊論文}]
\printbibliography[nottype=article-journal, nottype=book, title={其他類型}]
```

2、按照作者姓氏筆劃數排序

法學引註上似乎不常要求總頁數，因此 CSL `number-of-pages` 欄位基本上不會填寫。因此，就拿這個欄位來儲存作者姓氏筆劃數（必須手動填寫，國教院國語小字典可查詢漢字的筆劃數）。如果是使用 BibLaTex，則可以填入 `pagetotal` 中，即可自動對映至 `number-of-pages`。假設作者姓李，姓氏筆劃數為 7，使用 BibLaTex 即應寫成 `pagetotal = {07},`。

在 CSL 檔案中，設定輸出參考文獻時的排序為：

```tex
    <sort>
      <key variable="number-of-pages" />
      <key variable="author" />
      <key variable="issued" />
	</sort>
```

若 `<key>` 僅設定 `variable="author"`, locale zh 的情況下，不會自動使用筆畫排序，但個人不太確定是以拼音還是 Unicode 編碼排序。