# CaseClass
---
## 概要
修飾子。  
・基本コンストラクタにvalを付加  
・equals, hashcode, toStrintgメソッドを実装  
・canEqual, copy メソッドを実装  
・コンパニオンオブジェクトを生成し、applyメソッド,unapplyメソッドを実装  

## 使ってみる
```scala 
case class Var(name: String, age: Int)
```
生成
```scala 
scala> val test = Var("testName", 23)
val test: Var = Var(testName,23)

// 確認
scala> println(test)
Var(testName,23)
```
各メソッドは時間があれば追記

## 問題に使用
## copyメソッド
変更を加えたコピーを作るためのメソッド
```scala 
scala> val copyTest = test.copy("hogeName")
val copyTest: Var = Var(hogeName,23)
```
ここで錯覚しないようにしなきゃいけないのが元とコピーは別物だということ（当然か）