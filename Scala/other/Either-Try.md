# Either / Try 
---
- [Either]
  - [Eitherって何それ美味しいの？]
  - [値を取得する]

- [参照]

## Either
---
### Eitherって何それ美味しいの？
Eitherは、Either[Left, Right]といったようにLeftとRightの2つの値（型）を、どちらかを表現することができる入れ物です。

だいたいですが  
・Leftには失敗時の値  
・Rightには成功時の値  
を返す処理を書くことが多いようです（ソースはない）

Optionと比べると失敗時に値としてその理由を入れておけば、理由が返ってきて便利だなって場面もあるらしく
、想像すると便利そうですよね〜〜（小並感）

### Eitherに値を入れてみる
なるほど。理屈はわかった。で？実際にどう動くの？

```scala
sealed abstract class Either[+A, +B]

final case class RightProjection[+A, +B](e: Either[A, B])

final case class LeftProjection[+A, +B](e: Either[A, B])
```

なるほどわからん。 

よし、まずは動きを確かめてイメージをつけるために値を入れてみよう。  
実際の処理をイメージしやすいようにLeftにはエラー文字を、Rightには数値を入れてみる。

```scala

scala> val right: Either[String, Int] = Right(123)
val right: Either[String,Int] = Right(123)

scala> val left: Either[String, Int] = Left("error")
left: Either[String,Int] = Left(error)

// クラスでやるならこんな感じにして確認してください
object Main {
  def main(res: Array[String]): Unit = {
    val right: Either[String, Int] = Right(123)
    val left:  Either[String, Int] = Left("error")
    println("result--------------------")
    println("Right : " + right)
    println("--------------------------")
    println("Left  : "  + left)
    println("--------------------------")
  }
}

```

ふむ、なるほどわかった。エラー処理したい時は関数の方にEither指定してパターンマッチングで返却できそうやな。  
でもこれどうやって中身とるん？せっかく値を入れてもアクセスできなきゃ困るで。

### 値を取得する

まあ焦るな。Eitherでも他のメソッドと同じようにgetなどのメソッドを使えるみたいだ。  
挙動を確認してみよう。

※コピペしokですが理屈説明できないコードは自分のクビをしめるで。  
 定義リンクするから動き確認したら見てください.....（自戒）
### [get](https://github.com/scala/scala/blob/2.13.x/src/library/scala/util/Either.scala#L535)
まずはど定番（実際には中身ない時にエラー吐くからあんまり使わないというイメージ）

```scala
val left: Either[String, Int] = Left("error")
println("result--------------------")
println("Left : " + left.left.get)
println("--------------------------")

// result--------------------
// Left : error
// --------------------------

```

### [getOrElse](https://github.com/scala/scala/blob/2.13.x/src/library/scala/util/Either.scala#L279)
これ調べててちょっと驚きだったのが、EitherでgetOrElseをイメージだけで使うとちょっとハマる。 

事象はよくよく調べれば、もしくは考えれば当然なのかもしれないが、right2を見ていただきたい。  
値はright2（Either型）にleft値が存在しているが、getOrElseの引数を返している。left2に至っては値がそのまま返されている。  
ここからわかるのは、Rightの値にgetOrElseは評価を返している。

何が入っているか確認して、メソッドは評価を行うのか同志諸君には注意していただきたい（お前だけだ）

```scala
val right:  Either[String, Int] = Right(123)
val right2: Either[String, Int] = Left("error")
val left:   Either[String, Int] = Left("error")
val left2:  Either[String, Int] = Right(123)
println("result--------------------")
println("Right  : " + right.right.getOrElse("321"))
println("Right2 : " + right2.right.getOrElse("321"))
println("--------------------------")
println("Left   : " + left.left.getOrElse("getOrElse_error"))
println("Left   : " + left.left.getOrElse("getOrElse_error"))
println("--------------------------")

// result--------------------
// Right  : 123
// Right2 : 321
// --------------------------
// Left   : error
// Left2  : error
// --------------------------
```

### match
うちの息子（プログラム）がいつもお世話になっております。。。やたら使ってしまうヤツ、便利ですよね〜

```scala
val right: Either[String, Int] = Right(123)
val left:  Either[String, Int] = Left("error")
println("result--------------------")
right match {
  case Right(rval)  => println("結果は、" + rval)
  case Left(lval)   => println("結果は、" + lval)
}
println("--------------------------")
left match {
  case Right(rval)  => println("結果は、" + rval)
  case Left(lval)   => println("結果は、" + lval)
}
println("--------------------------")

// result--------------------
// 結果は、123
// --------------------------
// 結果は、error
// --------------------------
```

### [map](https://github.com/scala/scala/blob/2.13.x/src/library/scala/util/Either.scala#L381)
...ひぃひぃ....定義元のメソッドを見てくれ..(瀕死)

```scala
val right: Either[Int, Int] = Right(1)
val left:  Either[Int, Int] = Left(10)
println("result--------------------")
println("結果は、" + right.map(v => v + 5))
println("--------------------------")
println("結果は、" + left.map(v => v + 5))
println("--------------------------")

// result--------------------
// 結果は、Right(6)
// --------------------------
// 結果は、Left(10)
// --------------------------
```

お・わ・か・り・だろうか。  
Leftは値をそのまま返されていることを....マジで雰囲気で触ったらい余計な時間と工数踏むから[定義](https://github.com/scala/scala/blob/2.13.x/src/library/scala/util/Either.scala#L381)みよう（自戒）
```scala
def map[B1](f: B => B1): Either[A, B1] = this match {
  case Right(b) => Right(f(b))
  case _        => this.asInstanceOf[Either[A, B1]]
}
```
ちなみにちゃんと指定してあげるとできる
```scala
println("結果は、" + left.left.map(v => v + 5))
// 結果は、Left(15)
```

今まで使ったメソッドでこんなこともできる
```scala
val right: Either[Int, Int] = Right(10)
// val right: Either[Int, Int] = Right(15)
val result = right.map({
  case r if r % 2 == 0 => 123
  case _               => 321
})
println("result--------------------")
println("結果は、" + result)
println("--------------------------")

// result--------------------
// 結果は、Right(123) or Right(321)
// --------------------------
```

お腹いっぱいだけどもう一歩頑張ろう....

## Try
---
この際だからもう一歩、同じパターンマッチで使われるクラスを扱ってみる。

TryはEitherと同様、成功時と失敗時の型を表現することができます。
