---
title: JS练习题
date: 2017-11-17 16:48:31
categories:
	- 前端
tags:
	- 前端
	- Javascript
	- 面试题
---

### 1、把数字转换成中文
````
完成将 toChineseNum， 可以将数字转换成中文大写的表示，处理到万级别。
例如 toChineseNum(12345)，返回 一万二千三百四十五。
````

<!--more-->

````
const toChineseNum = (num) => {
    if (num === 0) {
        return '零';
    }
    const bit = ['', '十', '百', '千'];
    const unit = ['零', '一', '二', '三', '四', '五', '六', '七', '八', '九'];
    const section = ['', '万'];
    let sectionPos = 0;
    let resultStr = '';
    let piece, needZero = false;
    function toCNum(n) {
        let bitPos = 0, rs = '', zeroNum = 0;
        while (n > 0) {
            let curNum = n % 10;
            if (curNum === 0) {
                zeroNum++;
                bitPos++;
            } else {
                if (bitPos === zeroNum)
                    zeroNum = 0;
                else if (zeroNum > 0) {
                    rs = '零' + rs;
                    zeroNum = 0;
                }
                rs = unit[curNum] + bit[bitPos++] + rs;
            }
            n = Math.floor(n / 10);
        }
        return rs;
    }
    while (num > 0) {
        piece = num % 10000;
        resultStr = toCNum(piece) + section[sectionPos] + (needZero ? '零' : '') + resultStr;
        needZero = piece < 1000 && piece > 0;
        sectionPos++;
        num = Math.floor(num / 10000);
    }
    return resultStr;
}
或
const toChineseNum = (num) => {
    let str = '零一二三四五六七八九',
    str2 = ['', '十', '百', '千'];
    let Clu = Array.from( [...num.toString()].reverse(),
	(v, i) => str[v] + (i == 4 ? '万' : (v == 0 ? '' : str2[i % 4]))).reverse().join('')
	.replace(/零+/g, '零')
	.replace(/(零+$)/, '')
	.replace(/零+(?=万)/, '');
    return　 Clu;
}
或
const toChineseNum = (num) => {
    let unit = ['', '十', '百', '千', '万']
    let numArr = ['零', '一', '二', '三', '四', '五', '六', '七', '八', '九']
    let arrNum = num.toString().split("").reverse();
    let strArr = arrNum.map((v, i) => {
     if (i === 4 && parseInt(v) === 0) {
        return "万"
      }
      i = i > 4 ? i - 4 : i;
      return parseInt(v) === 0 ? numArr[v] : numArr[v] + unit[i - 0]
    })
    return strArr.reverse().join("").replace(/(零(?=零))|(零$)|(零(?=万))/g, '')
}
````

### 2、循环调节列表
````
页面上有这么一个列表：
<ul id='adjustable-list'>
  <li>
    <span>1</span>
    <button class='up'>UP</button>
    <button class='down'>DOWN</button>
  </li>
  <li>
    <span>2</span>
    <button class='up'>UP</button>
    <button class='down'>DOWN</button>
  </li>
  <li>
    <span>3</span>
    <button class='up'>UP</button>
    <button class='down'>DOWN</button>
  </li>
</ul>
点击 UP 按钮会使得该 li 元素在列表中上升一个位置，点击 DOWN 按钮会使得该 li 元素下降一个位置。点击最后的元素的 DOWN 按钮会使得元素回到第一个位置，点击第一个元素的 UP 按钮会使其回到最后的位置。
页面上已经存在该列表，你只需要完成 initAdjustableList() 函数，给元素添加事件。
````
````
const initAdjustableList = () => {
    var ul = document.getElementById('adjustable-list'),
      btns = ul.getElementsByTagName('button'),
      lis = ul.getElementsByTagName('li'),
      len = lis.length;

    [...btns].forEach(d => {
        d.onclick = e => {
            let text = e.target.innerText;

            [...lis].forEach((d, i) => {
                if (d.isEqualNode(e.target.parentNode)) {
                    if (text == 'UP') {
                        ul.insertBefore(d, lis[i-1])
                    } else {
                        ul.insertBefore(d, lis[i+2 > len ? 0 : i + 2])
                    }
                }
            })
        }
    })
}
````

### 3、操作 Cookie
````
完成 cookieJar 单例，它有三个方法：
set(name, value, days)：设置 cookie 的值，days 为多少天以后过期。
get(name)：获取 cookie 的值。
remove(name)：删除 cookie 的值。
````
````
const cookieJar = {
  set (name, value, days) {
    document.cookie=`${name}=${value};expires=${new Date(Date.now()+days*24*3600*1000)}`
  },
  get (name) {
    let cookie=document.cookie
    let reg=new RegExp(`${name}=([^;]+)`)
   var result=reg.exec(cookie)
   return result[1]
  },
  remove (name) {
     document.cookie=`${name}=outdate;expires=${new Date(Date.now()-36110000)}`
  }
}
或
const cookieJar = {
  set (name, value, days) {
    const d = new Date();
    d.setDate(d.getDate() + days)
    document.cookie = `${name}=${value}; expires=${d}`
  },
  get (name) {
    const obj = {};
    document.cookie.split(';').forEach(s => {
      s = s.trim();
      const key = s.slice(0, s.indexOf('='));
      const value = s.slice(s.indexOf('=') + 1);
      obj[key] = value;
    })
    return obj[name];
  },
  remove (name) {
    this.set(name, '', -1)
  }
}
````

### 4、实现 js 数据类型的判断
````
最新的 Javascript 标准规定了六种基本数据类型(number, null, undefined, string, boolean, symbol) 和基于 Object 衍生的其它原生数据类型
写出 type 函数，它传入一个参数，返回它的数据类型（用小写字母），比如: type(new Date)，返回 date。
````
````
const type = (obj) => {
  let dataType = {
    '[object Null]' : 'null',
    '[object Undefined]' : 'undefined',
    '[object Boolean]' : 'boolean',
    '[object Number]' : 'number',
    '[object String]' : 'string',
    '[object Function]' : 'function',
    '[object Array]' : 'array',
    '[object Date]' : 'date',
    '[object RegExp]' : 'regexp',
    '[object Object]' : 'object',
    '[object Symbol]' : 'symbol',
    '[object Map]' : 'map',
    '[object Set]' : 'set',
    '[object Int8Array]' : 'int8array',
    '[object Error]' : 'error'
  }
  return  dataType[Object.prototype.toString.call(obj)]
}
或
const type = (obj) => {
  return Object.prototype.toString.call(obj).slice(8,-1).toLowerCase();
}
````

### 5、转换驼峰命名
````
小科去了一家新的公司做前端主管，发现里面的前端代码有一部分是 C/C++ 程序员写的，他们喜欢用下划线命名，例如： is_good。小科决定写个脚本来全部替换掉这些变量名。
完成 toCamelCaseVar 函数，它可以接受一个字符串作为参数，可以把类似于 is_good 这样的变量名替换成 isGood。
变量名首尾的下划线不需要做处理，中间的下划线全部删除并且处理成驼峰。
````
````
const toCamelCaseVar = (v) => (/^_+/.exec(v) ? /^_+/.exec(v)[0] : '') + v.replace(/(^_+)|(_+$)/g,'').replace(/_+[\w$]/g,x=>x[x.length-1].toUpperCase())+ (/_+$/.exec(v) ? /_+$/.exec(v)[0] : '')
或
const toCamelCaseVar = (variable) => {
   return variable.replace(/([^_])_+([^_])/g, function (all, b, c) {
        return b+c.toUpperCase()
    })
}
````