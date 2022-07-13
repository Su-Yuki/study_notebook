# APIのHTTPステータスコードメモ
api 作ってる時に忘れがちなのでメモ
## 表
#### 正常系
|Status|Contents|Example|
----|----|----|
200 | OK | OK |
201 | Created | 新規作成の場合 |
202 | Accepted | バッチ処理 |

#### リダイレクト系
|Status|Contents|Example|
----|----|----|
301 | Moved Permanently | 恒久的にURLが変更 |
302 | Found |  |

#### クライアントエラー系
|Status|Contents|Example|
----|----|----|
400 | Bad Request | リクエストが不正 |
401 | Unauthorized | 認証エラー |
402 | Payment Required | 決済情報 |
403 | Forbidden | アクセス権限がない |
404 | Not Found | リソースが存在しない |
405 | Method Not Allowed | HTTPメソッドが許可されていない |
406 | Not Acceptable | リクエストヘッダー情報が間違っている |

#### システムエラー系
|Status|Contents|Example|
----|----|----|
500 | Internal Server Error | 例外エラー |
501 | Bad Gateway | サバ落ち |
502 | Service Unavailable | システムエラー |
