---
title: 期末考 OSINT 解題歷程
date: 2024-01-06 22:39
updated: 2025-12-22 09:20:00
categories: [學習筆記]
tags:
- 全民防衛
---

這是修讀臺北大學沈伯洋老師112學年度第1學期「[民防意識與情報蒐集](https://sea.cc.ntpu.edu.tw/pls/dev_stud/course_query.queryguide?g_year=112&g_term=1&g_serial=U4403&lang=&show_info=all)」通識課程，期末考試（作業）的個人解題過程。

## 第一題（阿彌陀佛姊1）

超難，鄉巴佬沒去過西門町。還好討論時有人說這是西門町，就去比對各路段的路燈顏色。

## 第二題（阿彌陀佛姊2）

我懷疑老師暗戀阿彌陀佛姊了！一直要我們找她行蹤。

這題沒解出來，不過後來 Dcard 大神有幫助我們。

## 第三題（日本小吃店）

**地點：**位於日本靜岡縣三島市的「Pica Pau」

逕行以圖搜圖，可以發現圖片出處是日本的一場  OSINT 競賽。左下角的菜餚照片可能是線索，因此透過修圖軟體將之調整後，把菜單圖片拿去搜尋，但顯然無法找出答案，而以「豚肉のオーブン焼き サラダ、こ飯、ドリンク付き ￥990」限縮亦無答案。

回去查看以圖搜圖結果中，有相同圖片的各個網頁，其中有兩篇是參賽心得文章（網址分別為： [1](https://zenn.dev/ryo_a/articles/7489b4fbf25921) 、 [2](https://qiita.com/kuro3/items/f3967a9fb81827b6cc5f) ），都有從照片中標示的某個菜餚名稱「Sarcinha」作為關鍵字，而以之為關鍵字搜尋後，被搜尋引擎校正為玻利維亞名菜Salteña的經歷。

根據第一篇文章（網域名稱為 zenn.dev ），他以「Salteña」與圖片中的電話號碼區碼，找到這家商店是位於日本靜岡縣三島市的「Pica Pau」[3](https://maps.app.goo.gl/zvoLvsN3EvsCHV2g9)。

## 第四題（街頭宣傳畫）

地點：伊朗德黑蘭 Enghelab Square 旁邊相鄰於「Bahman Cinema」戲院的建築。

由於圖片標示有「IRNA」浮水印，結尾的「NA」通常代表是某通訊社 news agency，所以本圖應該是某傳媒報導的附圖，因此就以圖搜圖，直接把整張圖片放到 Google 搜尋。經查，美國 The Iran Primer 網站的某個網頁（[4](https://iranprimer.usip.org/blog/2022/feb/09/irans-revolution-43-politics) ）上刊有本圖，caption 標示是「a mural in Tehran depicting Ayatollah Ali Khamenei (left) and Ayatollah Ruhollah Khomeini (right)」，至此可以限縮範圍是在德黑蘭。

接下來，我將 Google 智慧鏡頭掃描的範圍框限至該壁畫，搜尋結果出現 History Today 雜誌的文章（[5](https://www.historytoday.com/miscellanies/fear-loathing-and-zulm-iran) ），附圖也有一張照片是相同的壁畫，照片描述寫道：「Billboard on Azadi Street in Tehran. Supreme Leader Ali Khamenei is depicted on the left with his predecessor Ayatollah Khomeini on the right. Photo: Sophie Hay」至此可以限縮範圍是在德黑蘭當地的一條幹道Azadi Street（又稱Azadi Avenue，參英文維基百科 Azadi Avenue 條目）。

由於我是先從第四題開始，後來以圖搜圖解決第三題時，發現第三題的智慧鏡頭搜尋結果中，就有 OSINT 心得。本題為考古題，有人透過Flickr文章、街景地圖，找到第四題的這張圖，地點是Plus Code（附註：這是Google地圖提供的類似座標的功能）「P92V+G25」處，也就是Enghelab Square旁邊「Bahman Cinema」戲院（[Google Maps 連結](https://maps.app.goo.gl/CHsWehHCbQpi7BAz8) ）相鄰的建築。他的推理過程並無瑕疵，因此個人認為就是這棟建築。

附帶一提，Google地圖上顯示該建築是位在 Enghelab St，而非 Azadi St 上。可見雜誌社編輯在標示圖源時，不夠精確。

## 第五題（陰謀論社團聚會餐廳）

餐廳：美國俄勒岡州波特蘭的 Round Table Pizza 

先在 Facebook 搜尋欄上打上「Bill Coones」的名字，發現「貼文」類搜尋結果，第一則是名為「Bill Coones」者在「UFO Inquiring Minds」社團所發布的一則貼文。點入該社團發現「Bill Coones」為該社團管理員，其個人使用者頁面簡介自陳對陰謀論有興趣（[7](https://www.facebook.com/BillCoones/about_details) ），因此題目所詢問的，應該是指這一位Bill Coones（FB上有多位同名人士）。

接著，在「UFO Inquiring Minds」社團中以關鍵字「restaurant」搜尋貼文，發現Coones召集社員2021年10月24日於俄勒岡州波特蘭（Portland）一間名叫「Round Table Pizza」的餐廳聚會。但2023年9月17日則是在同州Clackamas 一帶另外一間名為「Elmer's Restaurant」的餐廳聚會。究竟何者算是經常聚會的餐廳？我改以「meeting」為關鍵字重新搜尋，發現2014年、2015年、2022年，Coones均發布貼文表示要在「Round Table Pizza」聚會，因此本題所要詢問的餐廳應該就是「Round Table Pizza」。其Google Maps地標連結為 [8](https://maps.app.goo.gl/e4HJeSQS7R33k9b27) 。

完。
