# nodebrewを使ってサクッとnodeを切り替える
受託の案件でチケット毎にバージョンを切り替えることが1日に何度もある。しんどい！！  
と思ってた時の備忘録を執筆。

## 今回やること
nodeの切り替えをサクッと15秒で終わらせる
#### 前提
nodeが入っていればアンインストールする。
#### Nodebrewをインストールする
```sh
# インスコ
$ brew install nodebrew
# 確認
$ nodebrew -v
```
## バージョン管理
```sh
# 使用確認の一覧
nodebrew ls-remote

# インストール方法
nodebrew install-binary バージョン

# 例
nodebrew install-binary v8.16.0 
nodebrew install-binary v10.0.0
```

では早速、ささっと切り替えてみる
```sh
# インスコ済み一覧
$ nodebrew ls

# 切り替え
$ nodebrew use v10.0.0

# 確認
$ node -v
```
まじ感謝。

## 参照
https://qiita.com/mame_daifuku/items/373daf5f49ee585ea498