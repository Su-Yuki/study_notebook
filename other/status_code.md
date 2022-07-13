# APIのHTTPステータスコードメモ
api 作ってる時に忘れがちなのでメモ
## 表
#### 正常系
||||
----|----|----|
200 | OK | 例：OK |
201 | Created | 例：新規作成の場合 |
202 | Accepted | 例：バッチ処理 |

#### リダイレクト系
||||
----|----|----|
301 | Moved Permanently | 例：恒久的にURLが変更 |
302 | Found | 例： |

#### クライアントエラー系
||||
----|----|----|
400 | Bad Request | 例：リクエストが不正 |
401 | Unauthorized | 例：認証エラー |
402 | Payment Required | 例：決済情報 |
403 | Forbidden | 例：アクセス権限がない |
404 | Not Found | 例：リソースが存在しない |
405 | Method Not Allowed | 例：HTTPメソッドが許可されていない |
406 | Not Acceptable | 例：リクエストヘッダー情報が間違っている |

#### システムエラー系
||||
----|----|----|
500 | Internal Server Error | 例：例外エラー |
501 | Bad Gateway | 例：サバ落ち |
502 | Service Unavailable | 例：システムエラー |
