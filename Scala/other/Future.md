# Future
## future
非同期処理を行う時に使う。長い処理などレスポンスが返ってくる時間を非同期にするなどの使い道がある。

futureは未来の値なので処理が終わるまでは値が取得できない。

futureは成功時と失敗時の値を持つ  
・成功時： successful  
・失敗時： failed

## 挙動を確認
非同期処理が始まって3秒後に処理が終わっていることがわかる
```scala
iimport scala.concurrent.Future
import scala.concurrent.ExecutionContext.Implicits.global
import java.util.concurrent.TimeUnit

object Main {
  def main(args: Array[String]): Unit = {
    println("処理開始")

    // 結果を返す非同期処理
    val result = Future {
      TimeUnit.SECONDS.sleep(3)
      println("非同期処理完了")
      "success"
    }
    println("処理完了")
  }
}
```
## 値の取得
方法は  
・for（map, flatMap）  
・apply  
・onComplete メソッド  
などがある。

今回はforでやってみる。
```scala
object Main {
  def main(args: Array[String]): Unit = {
    println("処理開始")

    val v1 = 1
    val v2 = 2

    // 結果を返す非同期処理
    val result1 = Future {v1 + v2}
    val result2 = Future {v1 * v2}

    val fture = for {
      callback1 <- result1
      callback2 <- result2
    } yield {
      println(callback1 + callback2)
      println("非同期中")
    }

    Thread.sleep(3000)
    println("処理完了")
  }
}
```





コールバック（完了処理）、ブロッキング等の言語化は時間を後で



## 
### 
```scala
```