
# Laravel命名規則メモ
Laravelでの開発時に迷う時があるので、個人ではとりあえず次のようにして統一しようと考えたのでメモ
---

|種類|規則|複数or単数|Example|
----|----|----|---- 
メソッド|ローワーキャメル|----|userCreate|
モデル|アッパーキャメル|----|UserData|
コントローラ|アッパーキャメル|----|UserDataController|
テーブル|スネークケース|複数|users_table|
マイグレーションファイル|スネークケース|単数|xxx_crate_users_table|
Bladeファイル|スネークケース|----|user_admin.blade.php|
変数|スネークケース|----|$user_data|

