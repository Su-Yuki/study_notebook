# エディタをカスタマイズしていく
受託先からPCを貸与してもらった時に自分のプライベートPCの構築どうやったかなってなったこと。自分の環境をカスタマイズしていきたいと思ったことから備忘録を執筆。

## 今回やること
「 iTerm + tmux 」を使ったエディタ環境を作成

## 何が便利なの？（tmux）
受託とかやってるとわかるかもしれないのですが、僕は案件やチケットごとに違うターミナルを複数開いたりすることで、「あれ？今どこいじってたっけ？」みたいに迷子になってしまうことがよくあります。（チケット毎にバージョン切り替えとかよくする）

要は画面が散らかって迷子になることを防止したり（vimでもできる）、セッションを保持してくれたりするので便利。何よりオリジナリティがあってカッコいい。エモい。

## 手順①　iTermのインストール

#### [iTerm2](https://iterm2.com/)
[こちら](https://iterm2.com/)からダウンロードする。（ダウンロードしたものファイルを開くだけ）

## 手順②　tmuxインストール
#### 前提：
homebrewを[こちらから](https://brew.sh/index_ja)からインストールしてください。
#### 本題
```sh
# tmuxインストール
$ brew install tmux
```
これだけ。

## 冒頭の画面を作ってみる
まず、インストールしたiTerm(なんでもいい)を開く。そうしたら
```sh
$ tmux
```
と入力。  

画面で
```sh
$ tmux split-window -v -p 30
$ tmux split-window -h -p 30
```
の順で入力する。

その次に「 プレフィックスキー + t 」で時計が出る。(プレフィクスキーを押した後に「t」なので注意)  
※プレフィックスキーはおそらく初期は「 control + b 」だと思われる。  

画面の移動は「 プレフィックスキー + p 」だったり「 プレフィックスキー + ↑（キーカーソル） 」だったり。  

## おまけ
完全に好みだと思うが「白源」を推したい。インストール方法のみ示しとくので好みで設定してみてください。
```sh
# 白源インストール
$ brew tap homebrew/cask-fonts
$ brew install font-hackgen
$ brew install font-hackgen-nerd
```
## 参照
- 「白源」の参照元  
https://qiita.com/tawara_/items/374f3ca0a386fab8b305