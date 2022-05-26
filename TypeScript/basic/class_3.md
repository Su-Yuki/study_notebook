# クラスの基本3
---
## 総称型
どんな値でも使えるようなメソッドやプロパティを作成したい時など
``` ts
class 名前 <T> {...}
```

``` ts
class Data<T> {
  data?: T[]

  constructor(...item:T[]) {
    this.data = item
  }

  print(): void {
    if(this.data) {
      for(let item of this.data){
        console.log(item)
      }
    }else{
      console.log('no data....')
    }
  }
}

const data1 = new Data<string>('one', 'two', 'three')
const data2 = new Data<number>(1, 2, 3)
data1.print()
data2.print()
```