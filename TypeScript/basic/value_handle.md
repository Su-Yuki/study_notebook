# 値の扱い
---

## 変数の宣言
定数
```
const name = value
```

変数
```
var name = value
let name = value
```

## 型宣言
```
var varName: 型
```
タプル
```
変数 :[型1, 型2]
```
```
例
let me:[string, number]
```

enum
```
enum 型名{ 項目1, 項目2}
```
```
例
enum janken { goo, choki, paa}

const rec = janken.goo
```

型エイリアス
```
type 新型名 = 型名
```
```
例
type name = string
type age  = number

let person: [name, age]
```

nullがあるかもしれない時の型
```
type = date = [name: string, age?: number]
```
※null許容なしは「!」を「?」にする
