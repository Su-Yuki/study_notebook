# RESTfull開発メモ
---
## CRUD
全て同じアドレスで、アクセスに使うHTTPメソッドの違いによって処理を分けるのが一般的。

|HTTP|CRUD|
----|----|
GET|Read。レコードの取得|
POST|Create。レコードの新規作成|
PUT|Update。レコードの更新|
DELETE|Delete。レコードの削除|

## RESTfullに必要なもの
/コントローラ|index|
/コントローラ|store(POST送信)|
/コントローラ/番号|show（番号=ID）|
/コントローラ/番号|update（番号=ID、PUT/PATCH送信）|
/コントローラ/番号|delete（番号=ID、DERETE送信）|

## いらないもの
/コントローラ/create|create（新規作成フォーム）|
/コントローラ/番号/edit|edit(番号=ID、更新のフォーム)|