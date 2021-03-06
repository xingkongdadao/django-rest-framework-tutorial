# 認識 RESTful API 📝

這篇文章將會簡單介紹 RESTful API ，希望大家會對 RESTful API 有更深入的了解 :blush:

如果有介紹不清楚或有錯誤的地方，歡迎大家 issuse 給我 :stuck_out_tongue_winking_eye:

* [Youtube Tutorial](https://youtu.be/gHCB0sd47Is)

## 介紹

先給大家一個觀念，

***RESTful 是一種設計風格，或者說是一種設計規範***

**為什麼我們要使用 **RESTful API** ？ 用一般的 API 不行嗎？**

一般的 API 可能長得像這樣

* ***/api/get_file/ ( 得到檔案 )***

* ***/api/upload_file/ ( 新增檔案 )***

* ***/api/update/ ( 更新檔案 )***

* ***/api/delete_file/ ( 刪除檔案 )***

**RESTful API** 則長得像這樣

* ***/api/file/ ( GET -> 得到檔案 )***

* ***/api/file/ ( POST -> 新增檔案 )***

* ***/api/file/ ( PUT -> 更新檔案)***

* ***/api/file/ ( DELETE -> 刪除檔案 )***

從上面的比較可以發現，使用 **RESTful API** 我們只需要一個接口就可以完成 :open_mouth:，

並且我們透過 HTTP 不同的 method 達到相對應的功能。

**RESTful API** 讓我們以很優雅的方式顯示 Resource ( 資源 )，

Resource ( 資源 ) 是由 URI 來指定，

( URI 是什麼，這邊不詳細介紹，就麻煩大家 Google，可以先簡單想為 URL 是一種 URI 就好 :smile: )

對 Resource ( 資源 ) 的操作，包含取得、新增、修改和刪除資源，

這些操作剛好對應 HTTP 協定提供的 GET、POST、PUT 和 DELETE 方法 。

**RESTful API** 擁有清楚又簡短的 URI，可讀性非常強，舉個例子

```url
- GET /api/files/  得到所有檔案
- GET /api/files/1/  得到檔案 ID 為 1 的檔案
- POST /api/files/  新增一個檔案
- PUT /api/files/1/  更新 ID 為 1 的檔案
- PATCH /api/files/1/  更新 ID 為 1 的部分檔案內容
- DELETE /api/files/1/  刪除 ID 為 1 的檔案
```

上面做的事情就是 CRUD，那什麼是 CRUD ，也就是

Create（ 新增 ）、 Read（ 讀取 ）、 Update（ 更新 ）、 Delete（刪除）

或是我想搜尋檔案名稱為 hello 的檔案，**RESTful API** 可能為

```url
GET /api/file/search?key=hello/
```

看到這邊，可以把 **RESTful** 想成是一種建立在 HTTP 協定之上的設計模式，充分的利用出 HTTP 協定的特定，

使用 URI 來表示資源，用各個不同的 HTTP 動詞（ GET、POST、PUT 和 DELETE 方法 ）來表示對資源的各種

行為，這樣做的好處就是資源和操作分離，讓對資源的管理有更好的規範以及前端（串接 API 或使用 API 的人）

可以很快速的了解你的 API ，省去很多不必要的溝通，如果熟悉 HTTP Method 的開發者，甚至可以不用看 API

文件就開始串接資料，當然，如果是更複雜的 API ，可能還是需要搭配文件，文件的撰寫可參考我之前寫的

[aglio_tutorial](https://github.com/twtrubiks/aglio_tutorial) 以及 [django_rest_framework_swagger_tutorial](https://github.com/twtrubiks/django_rest_framework_swagger_tutorial)。

這樣你現在是不是在想，**RESTful** 太神啦 :heart_eyes:

但是，記住，世界上沒有完美的東西，一定有他的缺點，

**RESTful** 很方便沒錯，但只要用戶了解了您的網站 URL 結構，就會開始產生 **安全性** 的問題

思考一個問題，一個用戶任意對你的 Database ( 資料庫 ) 操作 CRUD 是一件很可怕的事情

所以我們一定要再處理對用戶進行身份驗證和授權（可參考之前在 [django-rest-framework-tutorial](https://github.com/twtrubiks/django-rest-framework-tutorial#授權-authentications- ) 裡介紹的授權），

然後使用 HTTPS。

### 狀態碼

操作 API 的用戶，可以透過 HTTP 狀態碼了解一定的意思

HTTP status code 的常用情境如下 （ 通常，但不是絕對 ）

* 200 OK 用於請求成功 。GET 檔案成功，PUT， PATCH 更新成功

* 201 Created 用於請求 POST 成功建立資料。

* 204 No Content 用於請求 DELETE  成功。

* 400 Bad Request 用於請求 API 參數不正確的情況，例如傳入的 JSON 格式錯誤。

* 401 Unauthorized 用於表示請求的 API 缺少身份驗證資訊。

* 403 Forbidden 用於表示該資源不允許特定用戶訪問。

* 404 Not Found 用於表示請求一個不存在的資源。

更多詳細的可以參考 [HTTP Status Codes](http://www.restapitutorial.com/httpstatuscodes.html)

如果你的 API 比較複雜，還是要有文件記錄你的 error code 。

依據不同的 API 操作，定義適合的 HTTP 狀態碼和必要的錯誤資訊

（ 回傳一個 JSON 並且包含 error 屬性，error 這個屬性記錄錯誤訊息）。

## 結論

這次和大家簡單介紹了 **RESTful API** 的概念，基本上，還有很多可以研究，像是避免

API 被攻擊，可以考慮啟用 API 調用速率限制（ Rate limiting），又或是  HTTP Cache

的機制，最後，歡迎大家進入 **RESTful** 的世界 :laughing: