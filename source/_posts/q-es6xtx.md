---
title: ES6 新增特性练习题
date: 2018-08-20 15:47:25
categories:
	- 前端
tags:
	- 前端
	- Javascript
	- 面试题
    - ES6
---

### 1、判断两个 Set 是否相同
```
完成 isSameSet 函数，它接受了两个 Set 对象作为参数，请你返回 true/false 来表明这两个 set 的内容是否完全一致，例如：
const a = {}
const b = 1
const c = 'ScriptOJ'
const set1 = new Set([a, b, c])
const set2 = new Set([a, c, b])
isSameSet(set1, set2) // => true
```
```
const isSameSet = (set1, set2) => [...set1].every((o) => set2.has(o)) && [...set2].every((o) => set1.has(o))
```
<!--more-->

### 2、数组去重
```
编写一个函数 unique(arr)，返回一个去除数组内重复的元素的数组。例如：
unique([0, 1, 2, 2, 3, 3, 4]) // => [0, 1, 2, 3, 4]
unique([0, 1, '1', '1', 2]) // => [0, 1, '1', 2]
```
```
const unique = (arr) => [...new Set(arr)]
或
const unique = (arr)  => Array.from(new Set(arr))
```

### 3、判断美元符号格式
```
完成一个函数 isUSDFormat 返回 true/false 来判断一个字符串是否符合美元格式：
以 $ 开头
如果是小数，保留两位小数；如果不是小数则不显示小数部分
整数部分从小数点上一位开始每隔三位用 , 分割开来
如果整数部分从数字 0 开始，则只会显示一位 0
例如：
isUSDFormat('$1') // => true
isUSDFormat('$1.0') // => false
isUSDFormat('$100,000.00') // => true
isUSDFormat('$0,000.00') // => false
isUSDFormat('$0.00') // => true
isUSDFormat('$11,23,345.33') // => false
isUSDFormat('$1,123,345.33') // => true
```
```
const isUSDFormat = str => (/^\$([1-9]\d{0,2}(,\d{3})*|0)(\.\d{2})?$/).test(str)
```

### 4、filter map
```
const m = new Map([['Jerry', 12], ['Jimmy', 13], ['Tomy', 14]])
m.filterKeys((key) => key.startsWith('J')) // => Map { Jerry => 12, Jimmy => 13 }
m.filterValues((val) => val >= 13) // => Map { Jimmy => 13, Tomy => 14  }
原有的 map 保持不变
console.log(m) // => Map { Jerry => 12 , Jimmy => 13, Tomy => 14 }
```
```
Map.prototype.filterKeys = function(fn) {
  return new Map([...this].filter(([k, v]) => fn(k)));
}
Map.prototype.filterValues = function(fn) {
  return new Map([...this].filter(([k, v]) => fn(v)));
}
```

### 5、数组的空位填充
```
JavaScript 数组有空位的概念，也就数组的一个位置上没有任何的值。例如：
[ , , 'Hello'] // => 0, 1 都是空位, 3 不是空位
空位并不等于 undefined 或者 null。一个位置上如果是 undefined 那么它依然有值，例如 [, , undefined]，0 和 1 都是空位，而 2 不是空位。
请你完成一个函数 fillEmpty，它接受一个数组作为参数，可以把数组里面的所有空位都设置为 'Hello'，例如：
const a = [, , null, undefined, 'OK', ,]
fillEmpty(a)
a 变成 ['Hello', 'Hello', null, undefined, 'OK', 'Hello']
注意，你要原地修改原先的数组，而不是返回一个新的数组。
```
```
const fillEmpty = arr => {
  for(let i=0;i<arr.length;i++) {
    if(!(i in arr)) arr[i] = 'Hello';
  }
}
或
const fillEmpty = (arr) => {
  Array.from(arr).map((v,i)=>{if(!(i in arr)) arr[i]='Hello' })
}
```

### 6、不重复数字
```
编写一个 JavaScript 函数 uniqueNums，该函数有一个参数 n（一个不大 31 的整数），其返回值是一个数组，该数组内是 n 个随机且不重复的整数，且整数取值范围是 [2, 32]。
```
```
const uniqueNums = (n) => {
  let set = new Set()
  while(set.size < n) {
    set.add(Math.floor(2 + Math.random()*31))
  }
  return [...set]
}
或
const uniqueNums = (n) => {
  let arr = [];
  while(arr.length !== n) {
    let randomNum = Math.round(Math.random() * 30 + 2);
    if(arr.indexOf(randomNum) === -1) {
      arr.push(randomNum);
    }
  }
  return arr;
}
```

### 7、监听数组变化
```
在前端的 MVVM 框架当中，我们经常需要监听数据的变化，而数组是需要监听的重要对象。请你完成 ObserverableArray，它的实例和普通的数组实例功能相同，但是当调用：
push
pop
shift
unshift
splice
sort
reverse
这些方法的时候，除了执行相同的操作，还会把方法名打印出来。 例如：
const arr = new ObserverableArray()
arr.push('Good') // => 打印 'push'，a 变成了 ['Good']
注意，你不能修改 Array 的 prototype。还有函数 return 的值和原生的操作保持一致。
```
```
function ObserverableArray() {
  return new Proxy([], {
    get(target, propKey) {
      const matArr = ['push', 'pop', 'shift', 'unshift', 'splice', 'sort', 'reverse'];
      matArr.indexOf(propKey) > -1 && console.log(propKey);
      return target[propKey]
    }
  })
}

```

### 8、不用循环生成数组
```
完成 arrWithoutLoop 函数，它会被传入一个整数 n 作为参数，返回一个长度为 n 的数组，数组中每个元素的值等于它的下标。arrWithoutLoop 中不能使用循环控制结构。
```
```
const arrWithoutLoop = (n) => [...Array(n)].map((x, i) => i)
或
const arrWithoutLoop = (n) => Array.apply(null,{length:n}).map((item,i)=>i)
或
const arrWithoutLoop = n => [...Array(n).keys()]
或
const arrWithoutLoop = (n, arr = []) => n ? arr.unshift(n-1) && arrWithoutLoop(n-1, arr) : arr
```