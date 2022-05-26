# クラスの基本2
---
### インターフェース
構造の定義に使用。オブジェクトは作れない。
``` tscript
interface  名前 {
  プロパティ: 値
  メソッド'( 引数 ): 型
}
```

### 実装
``` tscript
class 名前 implements インターフェース {...}
```
実装クラスは継承関係にない

### インターフェースの継承
extends インターフェース

### 抽象クラス
抽象クラス
``` tscript
abstract class クラス名 {
  abstract メソッド(): 型
}
```

### 静的クラス
``` tscript
static プロパティ: 型
static メソッド(引数): 型
```

### ここまでの例
``` ts
enum School {
  junior     = 'junior',
  juniorHigh = 'juniorHigh',
  high       = 'high',
  other      = 'other'
}

interface Human {
  name: string
  print(): void
}

class Person implements Human {
  name: string = 'no-name'
  mail: string
  age:  number

  constructor(name: string, mail: string = 'no-mail', age: number = -1) {
    this.name = name
    this.mail = mail
    this.age  = age
  }

  print(): void {
    console.log(this.name + '(' + this.mail + ',' + this.age + ')')
  }
}

class Student implements Human {
  name:    string = 'no-name'
  school?: School
  grade?:  number

  constructor(name: string, school?: School, grade?: number) {
    this.name   = name
    this.school = school
    this.grade  = grade
  }

  print(): void {
    let gd: string = this.grade ? String(this.grade) : '-'
    console.log(this.name + '(' + this.school + '-school: ' + gd + ' grade)')
  }
}

const taro: Person  = new Person('taro', 'taro@example.com', 39)
const hana: Student = new Student('hana', School.high, 39)
const saki: Person  = new Person('saki')
const kana: Student = new Student('kana')

const data: Human[] = [taro, hana, saki, kana]

for(let item of data){
  item.print()
}

interface People extends Human {
  birth: Date
}

class Employee implements People {
  name:    string = 'no-name'
  company: string = ''
  birth:   Date   = new Date()

  constructor(nm: string, cm: string, bth: Date) {
    this.name    = nm
    this.company = cm
    this.birth   = bth
  }

  print(): void {
    console.log(this.name + '[' + this.company + ']')
  }
}

const ichiro = new Employee(
  'ichiro',
  'Sample Inc',
  new Date()
)
ichiro.print()

class StaticHuman {
  static fullname: string
  static age: number

  static set(nm: string, ag:number): void {
    this.fullname = nm
    this.age      = ag
  }

  static print(): void {
    console.log(this.fullname + '(' + this.age + ')')
  }
}
StaticHuman.set('taro', 39)
StaticHuman.print()
StaticHuman.set('hana', 28)
StaticHuman.print()
```