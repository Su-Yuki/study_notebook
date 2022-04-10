# Class
---
## 前提として抑えるポイント
### 関数定義
最低限の関数定義の基本をここで...
```scala
def max(x: Int, y: Int): Int = {
  if (x > y)
    x
  else
    y
}
```
def: 関数定義のお約束として先頭におく  
max: 関数名（任意名）  
x, y: 関数で使用する引数  
Int: それぞれの引数（引数の後ろ「: Int」は戻り値の型）  
= {}: 関数の処理を{}内にかく。ちなみに{}は省略可能  
大体は型推論してくれるけど、コンパイルなどで想定外が怖いのでちゃんと型を指定してあげると良いというイメージ。頭の中で型推論するのもアレだからしっかりやる

### タプル
要素に異なる型を持たせることができる。ちなみにimmutableな型。
```scala
// こんな感じ
val  user1: (Int, String) = (1, "generic name")
// 別名で作成
val  user2: (Int, String) = hoge(2, "nickname")
```
値を取得してみる
```scala
scala> val  user1: (Int, String) = (1, "generic name")
val user1: (Int, String) = (1,generic name)

scala> val id: Int = user1._1
val id: Int = 1
scala> val name: String = user1._2
val name: String = generic name
```


## クラス(Class)
```scala
class ChecksumAccumulator {
  // クラス定義
}
```
オブジェクト生成
```scala
new ChecksumAccumulator
```
※引数がない場合は()を省略できる

クラスの中にはフィールド(field)とメソッド(method)を配置し、まとめてメンバーと(member)と呼ばれる。  
field :オブジェクトを参照する変数(var, valで定義)
method:お馴染み。実行可能なコードを格納するもの。

実際にオブジェクトを生成してみる
```scala
class ChecksumAccumulator {
  var sum = 0
}
val acc = new ChecksumAccumulator
val csa = new ChecksumAccumulator
```

## シングルトンを定義
Scalaでは、全ての値がオブジェクトなため、クラスに属するstaticフィールドやstaticメソッドといったものを作成することができないため、objectキーワードによって定義したシングルトンオブジェクトには、そのオブジェクト固有のメソッドやフィールドを定義することができる。

シングルトンはobjectキーワードを使って定義することができる。
```scala
object Format {
  def format(imput: String): Unit = {
    println(imput)
  }
}
```
シングルトンのインスタンスは自動的に生成される。  
※コンストラクタに引数を指定できず、補助コンストラクタの利用もできない。

シングルトンインスタンスには、オブジェクト名でアクセスできる。
```scala
scala> Format.format("aaa")
aaa
```

## コンパニオンオブジェクト
同じ名前のクラスとシングルトンを一つのソースファイルに定義した場合、シングルトンはコンパニオンオブジェクトになる。クラスとコンパニオンオブジェクトはお互いのprivateメンバにアクセス可能という特徴がある。  
※主にクラスのファクトリとして利用される。

### 抽象子
unapplyメソッドを定義したオブジェクトのこと。applyとは逆を行う。  
apply　:インスタンスを生成  
unapply　:インスタンスから値を抽出

## 参照
- 実践Scala入門
- Scala スケーラブルプログラミング 第4版