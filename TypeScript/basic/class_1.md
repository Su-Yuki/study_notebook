# クラスの基本
---
基本
```
class 名前 {
  プロパティ: 値
  プロパティ: 値
  ~
  メソッド(引数): 戻り値 {...処理...}  
  ~
}

変数 = new クラス()
```

変数のスコープ
|||
----|----|
public|外部から自由にアクセスできる。アクセス修飾子がなければデフォルト|
protected|クラスmクラスを継承したクラスからは利用できる。|
private|クラス内のみで使用可能。クラス外全ての者もからアクセスを拒否する。|

## インスタンスのクラスを調べる
特定のクラスインスタンス化を確認する
```
インスタンス instanceof クラス名
```
インスタンスのクラスを得る
```
インスタンス.constructor.name
```
クラスの名前を得る
```
クラス.name
```

## クラスの継承
```
class 新しいクラス extends 継承するクラス {...}
```

## setter/getter
```
get メソッド(): 戻り値 {...}
set メソッド( 引数 ) {...}
```
実装するメソッド
```
get abc(): string {...}
get abc(value: string) {...}
```
利用
```
this.abc = 値
変数 = this.abc
```
## super
コンストラクタの呼び出し（スーパークラスの）

## ここまででの例まとめ
```
class Person {
  protected name: string = 'no-name'
  private   mail: string
  public    age:  number

  constructor(name: string, mail: string = 'no-mail', age: number = -1) {
    this.name = name
    this.mail = mail
    this.age  = age
  }

  print(): void {
    console.log(this.name + '(' + this.mail + ',' + this.age + ')')
  }
}

enum School {
  junior     = 'junior',
  juniorHigh = 'juniorHigh',
  high       = 'high',
  other      = 'other'
}

class Student extends Person {
  school?: School
  private grade_num: number = -1

  get gradeN(): number {
    return this.grade_num
  }
  set gradeN(n: number) {
    this.grade_num = n
    this.grade     = String(n)
  }
  private gr_str: string = ''
  get grade(): string {
    return this.gr_str
  }
  private set grade(pr: string) {
    let gd = pr
    switch(this.gradeN){
      case 1:
        gd += 'st';
        break
      case 2:
        gd += 'nd';
        break
      case 3:
        gd += 'rd';
        break
      default:
        gd += 'th'
    }
    this.gr_str = gd
  }

  constructor(name: string, school: School, grade: number) {
    super(name)
    this.school = school
    this.gradeN = grade
  }
  
  print(): void {
    let gd: string = this.grade ? String(this.grade) : '-'

    console.log(this.name + '(' + this.school + '-school: ' + gd + ' grade)')
  }
}


const taro = new Person('taro', 'taro@email.com', 30)
const hana = new Person('hana', 'hana@email.com', 20)
taro.print()
hana.print()

const saki = new Student('saki', School.junior, 3)
const kana = new Student('kana', School.high, 2)
saki.print()
kana.print()
```