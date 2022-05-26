# オブジェクトの基本
---

基本
```
変数 = Object()
```
```
例
const person = Object()
person.name  = "taro"
person.age   = 39
person.print = function(): void {
  console.log(this.name + '(' + this.age + ')')
}
```

## ファクトリ関数を作る
基本
```
function 名前 ( 引数 ): 戻り値 {
  return { ...オブジェクト... }
}
```
```
例
function Person(n: string, a: number):
  { 
    name: string,
    age: number,
    print: ()=> void 
  } {
  return{
    name:  n,
    age:   a,
    print: function() {
      console.log(this.name + '(' + this.age + ')')
    }
  }
}
```
※jsだとコンストラクタ（this.〇〇）関数を使うけど、TSだと扱いが変わっているらしく動かない？


## オブジェクトを引数に
```
type Person = {name: string, age:number} 

function setData(ob: Person, n: string, a:number): Person {
  ob.name = n
  ob.age  = a
  return ob
}

const ob1: Person = {name: 'taro', age: 39}
const ob2: Person = setData(ob1, 'hana', 20)

console.log(ob1)
console.log(ob2)
```
※参照が渡される点に注意