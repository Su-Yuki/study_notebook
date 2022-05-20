# 関数の基本
---

## 変数の宣言

#### 基本
```
function 名前(引数) {
  処理
}
```
変数のスコープ
|||
----|----|
var|関数の外で宣言したら場合は、ソースコード全体で参照可能。関数中で宣言したものは関数内でのみ参照可能。|
let|その変数を宣言した構文内で使える。|

#### 戻り値
戻り値
```
function 名前(引数): 型 {...}
```
何も返さない場合は「void」を指定。

複数の値を返す
```
function 名前(引数): [ タプル ] {...}
```

#### 無名関数
```
(引数): 戻り値 => 実行処理
```

関数を戻り値にしたい
```
例
(n:number, f: Function): void => {...}
```

例外を発生させる
```
const f = (n: number) => {
  if (n < 0) {
    throw  Error("負の数字です。")
  }
  console.log(n)
}
```

※tryで例外を捕捉
```
const f = (n: number) => {
  if (n < 0) {
    throw  Error("負の数字です。")
  }
  console.log(n)
}

try {
  let rel1 = f(100)
  let rel2 = f(-100)

  console.log(rel1)
  console.log(rel2)
} catch(e) {
  console.log(e.message)
}
```

#### ジェネリクス
```
function 関数<T>( 変数:T ): T
```

#### 遅延評価
ジェネレータはnextが呼び出されるまでyieldで待ち続ける。
```
yield 値
~
next()
```
```
例
function * fibo(n: number) {
  let n1 = 0
  let n2 = 1
  for(let i = 0; i <= n; i++) {
    yield n1
    let n3 = n1 + n2
    n1 = n2
    n2 = n3
  }
}

const n = 10
let fb  = fibo(n)
for (let i = 0; i <= n + 3; i++) {
  let ob = fb.next()
  console.log(ob.value)
} 
```

#### 非同期処理 Promis
実行結果が得られるまで時間がかかるので呼び出した側が待たないといけない場合（非同期処理）
```
function 関数名(引数): Promise {
  return new Promis( (関数) => {
    ~時間のかかる処理~
    関数()
  })
}
```
呼びだし
```
関数 (引数).then(関数)
```

```
例
const f = (n: number, d:number): Promise<number> => {
  console.log("start:" + n)
  return new Promise((f) =>{
    let total = 0
    for(let i = 1; i <= n; i++){
      total += i
      setTimeout(() => {
        f(total)
      }, d);
    }
  })
}

const cb = (n:number) => {
  console.log("result: " + n)
}

f(10, 30).then(cb)
f(100, 20).then(cb)
f(1000, 100).then(cb)

console.log("do something...")
```