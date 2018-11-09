---
title: JS常见面试题
date: 2018-08-16 09:20:12
categories:
	- 前端
tags:
	- 前端
	- Javascript
	- Jquery
	- Zepto
	- Ajax
	- Json
	- Nodejs
	- Requirejs
	- 面试题
---

## JS基础

### 1、javascript 的 typeof 返回哪些数据类型
```
object, number, function, boolean, underfind, string
typeof null;//object
typeof isNaN;//
typeof isNaN(123)
typeof [];//object
Array.isARRAY(); es5
toString.call([]);//”[object Array]” var arr=[];
arr.constructor;//Array
```

<!--more-->

### 2、例举 3 种强制类型转换和 2 种隐式类型转换?
```
强制（parseInt,parseFloat,Number()）
隐式（==）
1==”1”//true
null==undefined//true
```

### 3、split() join() 的区别
```
split()是切割成数组的形式，
join()是将数组转换成字符串
```

### 4、数组方法 pop() push() unshift() shift()
```
pop()尾部删除
push()尾部添加
unshift()头部添加
shift()头部删除
```

### 5、事件绑定和普通事件的区别
```
事件绑定是指把事件注册到具体的元素之上，普通事件指的是可以用来注册的事件
如果说给同一个元素绑定了两次或者多次相同类型的事件，那么后面的绑定会覆盖前面的绑定
不支持 DOM 事件流 事件捕获阶段目标元素阶段=>事件冒泡阶段
addEventListener
如果说给同一个元素绑定了两次或者多次相同类型的事件，所有的绑定将会依次触发
支持 DOM 事件流的
进行事件绑定传参不需要 on 前缀
ie9 开始，ie11 edge：addEventListener
ie9 以前：attachEvent/detachEvent
进行事件类型传参需要带上 on 前缀
这种方式只支持事件冒泡，不支持事件捕获
```

### 6、IE 和 DOM 事件流的区别
```
执行顺序不一样、
参数不一样
事件加不加 on
this 指向问题
IE9 以前：attachEvent(“onclick”)、detachEvent(“onclick”)
IE9 开始跟 DOM 事件流是一样的，都是 addEventListener
```

### 7、IE 和标准下有哪些兼容性的写法
```
var ev = ev || window.event
document.documentElement.clientWidth || document.body.clientWidth
var target = ev.srcElement||ev.target
```

### 8、call 和 apply 的区别
```
call 和 apply 相同点：都是为了用一个本不属于一个对象的方法，让这个对象去执行
toString.call([],1,2,3)
toString.apply([],[1,2,3])
Object.call(this,obj1,obj2,obj3)
Object.apply(this,arguments)
```

### 9、b 继承 a 的方法
```
考点：继承的多种方式
function b(){}
b.protoototype=new a;
```

### 10、指针、闭包、作用域
```
this：指向调用上下文
闭包：内层作用域可以访问外层作用域的变量
作用域：定义一个函数就开辟了一个局部作用域，整个 js 执行环境有一个全局作用域
闭包的缺点：滥用闭包函数会造成内存泄露，因为闭包中引用到的包裹函数中定义的变量都永远不会被释放，所以我们应该在必要的时候，及时释放这个闭包函数
```

### 11、事件委托是什么
```
符合 W3C 标准的事件绑定 addEventLisntener /attachEvent
让利用事件冒泡的原理，让自己的所触发的事件，让他的父元素代替执行！
```

### 12、如何阻止事件冒泡和默认事件
```
e. stopPropagation();//标准浏览器
event.canceBubble=true;//ie9 之前
阻止默认事件：为了不让 a 点击之后跳转，我们就要给他的点击事件进行阻止
return false
e.preventDefault();
```

### 13、document load 和 document ready 的区别
```
Document.onload 是在结构和样式加载完才执行 js
window.onload：不仅仅要在结构和样式加载完，还要执行完所有的样式、图片这些资源文件，全部加载完才会触发 window.onload 事件
Document.ready 原生中没有这个方法，jquery 中有 $().ready(function)
```

### 14、编写一个数组去重的方法
```
var arr=[1,1,3,4,2,4,7]; =>[1,3,4,2,7] 一个比较简单的实现就是：
先创建一个空数组，用来保存最终的结果
循环原数组中的每个元素
再对每个元素进行二次循环，判断是否有与之相同的元素，如果没有，将把这个元素放到新数组中
返回这个新数组
function oSort(arr) {
var result ={};
var newArr=[];
for(var i=0;i<arr.length;i++){
if(!result[arr]) {
newArr.push(arr)
result[arr]=1
}
}
return newArr
}</arr.length;i++)
```

### 15、foo = foo||bar ，这行代码是什么意思？
```
这种写法称之为短路表达式
if(!foo) foo = bar; //如果 foo 存在，值不变，否则把 bar 的值赋给 foo。
短路表达式：作为”&&”和”||”操作符的操作数表达式，这些表达式在进行求值时，只要最终的结果已经可以确定是真或假，求值过程便告终止，这称之为短路求值。
注意 if 条件的真假判定，记住以下是 false 的情况：空字符串、false、undefined、null、0
```

### 16、随机选取 10–100 之间的 10 个数字，存入一个数组，并排序。
```
var iArray = [];
funtion getRandom(istart, iend){
var iChoice = istart - iend +1;
return Math.floor(Math.random() * iChoice + istart;
}
Math.random()就是获取 0-1 之间的随机数（永远获取不到 1）
for(var i=0; i<10; i++){
var result= getRandom(10,100);
iArray.push(result);
}
iArray.sort();
```

### 17、把两个数组合并，并删除第二个元素。
```
var array1 = ['a','b','c'];
var bArray = ['d','e','f'];
var cArray = array1.concat(bArray);
cArray.splice(1,1);
```

### 18、写一个 function，清除字符串前后的空格。（兼容所有浏览器）
```
使用自带接口 trim()，考虑兼容性：
if (!String.prototype.trim) {
String.prototype.trim = function() {
return this.replace(/^\s+/, "").replace(/\s+$/,"");
//\s 匹配空白字符：回车、换行、制表符 tab 空格
}
}
// test the function
var str = " \t\n test string ".trim();
alert(str == "test string"); // alerts "true"
```

### 19、列举浏览器对象模型 BOM 里常用的至少 4 个对象，并列举 window 对象的常用方法至少 5 个
```
对象：Window document location screen history navigator
方法：Alert() confirm() prompt() open() close()
```

### 20、文档对象模型 DOM 里 document 的常用的查找访问节点的方法
```
Document.getElementById 根据元素 id 查找元素
Document.getElementByName 根据元素 name 查找元素
Document.getElementTagName 根据指定的元素名查找元素
```

### 21、iframe 的优缺点？
```
优点：解决加载缓慢的第三方内容如图标和广告等的加载问题,Security sandbox,并行加载脚本
缺点：iframe 会阻塞主页面的 Onload 事件,即时内容为空，加载也需要时间,没有语意
```

### 22、谈谈 Cookie 的弊端？
```
`Cookie`数量和长度的限制。每个 domain 最多只能有 20 条 cookie，每个 cookie 长度不能超过 4KB，否则会被截掉。
安全性问题。如果 cookie 被人拦截了，那人就可以取得所有的 session 信息。即使加密也与事无补，因为拦截者并不需要知道 cookie 的意义，他只要原样转发 cookie 就可以达到目的了。
有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用
```

### 23、DOM 操作——怎样添加、移除、移动、复制、创建和查找节点。
```
1. 创建新节点
createDocumentFragment() // 创建一个 DOM 片段
createElement() // 创建一个具体的元素
createTextNode() // 创建一个文本节点
2. 添加、移除、替换、插入
appendChild()
removeChild()
replaceChild()
insertBefore() // 在已有的子节点前插入一个新的子节点
3. 查找
getElementsByTagName() // 通过标签名称
getElementsByName() // 通过元素的 Name 属性的值(IE 容错能力较强，会得到一个数组，其中包括 id 等于 name 值的)
getElementById() // 通过元素 Id，唯一性
```

### 24、js 延迟加载的方式有哪些？
```
defer 和 async
动态创建 DOM 方式（创建 script，插入到 DOM 中，加载完毕后 callBack）
按需异步载入 js
```

### 25、documen.write 和 innerHTML 的区别？
```
document.write 只能重绘整个页面
innerHTML 可以重绘页面的一部分
```

### 26、哪些操作会造成内存泄漏？
```
内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。
垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量。如果一个对象的引用数量为 0（没有其他对象引用过该对象），或对该对象的惟一引用是循环的，那么该对象的内存即可回收。
setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。
闭包
控制台日志
循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）
```

### 27、IE 和 DOM 事件流的区别
```
执行顺序不一样、
参数不一样
事件加不加 on
this 指向问题
```

### 28、什么是闭包？ 写一个简单的闭包？
```
闭包就是能够读取其他函数内部变量的函数。在本质上，闭包就是将函数内部和函数外部连接起来的一座桥梁。
function outer(){
var num = 1;
function inner(){
var n = 2;
alert(n + num);
}
return inner;
}
outer()();
```

### 29、javascript 中的垃圾回收机制？
```
在 Javascript 中，如果一个对象不再被引用，那么这个对象就会被 GC回收。如果两个对象互相引用，而不再 被第 3 者所引用，那么这两个互相引用的对象也会被回收。因为函数 a 被 b 引用，b 又被 a 外的 c 引用，这就是为什么 函数 a 执行后不会被回收的原因。
```

### 30、什么是同源策略？
```
同协议、端口、域名的安全策略，由网景(Netscape)公司提出来的安全协议！
```

### 31、BOM 对象有哪些，列举 window 对象？
```
window 对象 ，是 JS 的最顶层对象，其他的 BOM 对象都是 window 对象的属性；
document 对象，文档对象；
location 对象，浏览器当前 URL 信息；
navigator 对象，浏览器本身信息；
screen 对象，客户端屏幕信息；
history 对象，浏览器访问历史信息；
```

### 32、bind(), live(), delegate()的区别
```
bind： 绑定事件，对新添加的事件不起作用，方法用于将一个处理程序附加到每个匹配元素的事件上并返回 jQuery 对象。
live： 方法将一个事件处理程序附加到与当前选择器匹配的所有元素（包含现有的或将来添加的）的指定事件上并返回 jQuery 对象。
delegate： 方法基于一组特定的根元素将处理程序附加到匹配选择器的所有元素（现有的或将来的）的一个或多个事件上。
```

### 33、你如何优化自己的代码？
```
代码重用
避免全局变量（命名空间，封闭空间，模块化 mvc..）
拆分函数避免函数过于臃肿：单一职责原则
适当的注释，尤其是一些复杂的业务逻辑或者是计算逻辑，都应该写出这个业务逻辑的具体过程
内存管理，尤其是闭包中的变量释放
```

### 34、列举常用的 js 框架以及分别适用的领域
```
jquery：简化了 js 的一些操作，并且提供了一些非常好用的 API
jquery ui、jquery-easyui：在 jqeury 的基础上提供了一些常用的组件 日期，下拉框，表格这些组件
require.js、sea.js（阿里的玉帛）+》模块化开发使用的
zepto：精简版的 jquery，常用于手机 web 前端开发 提供了一些手机页面实用功能,touch
ext.js：跟 jquery 差不多，但是不开源，也没有 jquery 轻量
angular、knockoutjs、avalon(去哪儿前端总监)：MV*框架，适合用于单页应用开发(SPA)
```

### 35、列出 3 条以上 ff 和 IE 的脚本兼容问题
```
在 IE 下可通过 document.frames["id"];得到该 IFRAME 对象，而在火狐下则是通过 document.getElementById("content_panel_if").contentWindow;
IE 的写法： _tbody=_table.childNodes[0]
在 FF 中，firefox 会在子节点中包含空白则第一个子节点为空白""， 而 ie 不会返回空白,可以通过 if("" != node.nodeName)过滤掉空白子对象
模拟点击事件
if(document.all){ //ie 下
document.getElementById("a3").click();
}
else{ //非 IE
var evt = document.createEvent("MouseEvents");
evt.initEvent("click", true, true);
document.getElementById("a3").dispatchEvent(evt);
}
事件注册
if (isIE){window.attachEvent("onload", init);}else{window.addEventListener("load", init, false);}
```

## JS高级

### 1、什么是 webkit 么? 怎么用浏览器的各种工具来调试和 debug 代码?
```
Webkit 是浏览器引擎，包括 html 渲染和 js 解析功能，手机浏览器的主流内核，与之相对应的引擎有 Gecko（Mozilla Firefox 等使用）和 Trident（也称 MSHTML，IE 使用）。
对于浏览器的调试工具要熟练使用，主要是页面结构分析，后台请求信息查看，js 调试工具使用，熟练使用这些工具可以快速提高解决问题的效率
```

### 2、如何测试前端代码? 知道 BDD, TDD, Unit Test 么? 怎么测试你的前端工程(mocha, sinon, jasmin, qUnit..)?
```
了解 BDD 行为驱动开发与 TDD 测试驱动开发已经单元测试相关概念
```

### 3、前端 templating(Mustache, underscore, handlebars)是干嘛的, 怎么用?
```
Web 模板引擎是为了使用户界面与业务数据（内容）分离而产生的，Mustache 是一个 logic-less （轻逻辑）模板解析引擎，它的优势在于可以应用在Javascript、PHP、Python、Perl 等多种编程语言中。
Underscore 封装了常用的 JavaScript 对象操作方法，用于提高开发效率。
Handlebars 是 JavaScript 一个语义模板库，通过对 view 和 data 的分离来快速构建Web 模板。
```

### 4、 Javascript 作用域链?
```
理解变量和函数的访问范围和生命周期，全局作用域与局部作用域的区别，JavaScript中没有块作用域，函数的嵌套形成不同层次的作用域，嵌套的层次形成链式形式，通过作用域链查找属性的规则需要深入理解。
```

### 5、 谈谈 this 对象的理解。
```
理解不同形式的函数调用方式下的 this 指向，理解事件函数、定时函数中的 this 指向，函数的调用形式决定了 this 的指向。
```

### 6、 eval 是做什么的？
```
它的功能是把对应的字符串解析成 JS 代码并运行；应该避免使用 eval，不安全，非常耗性能（2 个步骤，一次解析成 js 语句，一次执行）

```

### 7、 关于事件，IE 与火狐的事件机制有什么区别？ 如何阻止冒泡？
```
[1].在 IE 中,事件对象是作为一个全局变量来保存和维护的.所有的浏览器事件,不管是用
户触发的，还是其他事件,都会更新 window.event 对象.所以在代码中，只要调用
window.event 就可以获取事件对象， 再 event.srcElement 就可以取得触发事件的元素进
行进一步处理.
[2].在 FireFox 中，事件对象却不是全局对象，一般情况下，是现场发生，现场使用，FireFox
把事件对象自动传给事件处理程序. 关于事件的兼容性处理要熟练掌握，事件对象具体哪些属性存在兼容性问题，IE 与标准事
件模型事件冒泡与事件捕获的支持要理解
```

### 8、 什么是闭包（closure），为什么要用它？
```
简单的理解是函数的嵌套形成闭包，闭包包括函数本身已经它的外部作用域
使用闭包可以形成独立的空间，延长变量的生命周期，报存中间状态值
```

### 9、new 操作符具体干了什么呢?
```
1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
2、属性和方法被加入到 this 引用的对象中。
3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。
```

### 10、js 延迟加载的方式有哪些？
```
方案一：<script>标签的 async="async"属性（详细参见：script 标签的 async 属性）
方案二：<script>标签的 defer=defer属性
方案三：动态创建<script>标签
方案四：AJAX eval（使用 AJAX 得到脚本内容，然后通过 eval_r(xmlhttp.responseText)
来运行脚本）
方案五：iframe 方式
```

### 11、模块化开发怎么做？
```
理解模块化开发模式：浏览器端 requirejs，seajs；服务器端 nodejs；ES6 模块化；fis、
webpack 等前端整体模块化解决方案；grunt、gulp 等前端工作流的使用
```

### 12、requireJS 的核心原理是什么？（如何动态加载的？如何避免多次加载的？如何 缓存的？）
```
核心是 js 的加载模块，通过正则匹配模块以及模块的依赖关系，保证文件加载的先后顺序，根据文件的路径对加载过的文件做了缓存
```

### 13、数组和对象有哪些原生方法，列举一下？
```
Array.concat( ) 连接数组
Array.join( ) 将数组元素连接起来以构建一个字符串
Array.length 数组的大小
Array.pop( ) 删除并返回数组的最后一个元素
Array.push( ) 给数组添加元素
Array.reverse( ) 颠倒数组中元素的顺序
Array.shift( ) 将元素移出数组
Array.slice( ) 返回数组的一部分
Array.sort( ) 对数组元素进行排序
Array.splice( ) 插入、删除或替换数组的元素
Array.toLocaleString( ) 把数组转换成局部字符串
Array.toString( ) 将数组转换成一个字符串
Array.unshift( ) 在数组头部插入一个元素
Object 对象的常用方法
Object.hasOwnProperty( ) 检查属性是否被继承
Object.isPrototypeOf( ) 一个对象是否是另一个对象的原型
Object.propertyIsEnumerable( ) 是否可以通过 for/in 循环看到属性
Object.toLocaleString( ) 返回对象的本地字符串表示
Object.toString( ) 定义一个对象的字符串表示
Object.valueOf( ) 指定对象的原始值
```

### 14、如何编写高性能的 Javascript？
```
使用 DocumentFragment 优化多次 append
通过模板元素 clone ，替代 createElement
使用一次 innerHTML 赋值代替构建 dom 元素
使用 firstChild 和 nextSibling 代替 childNodes 遍历 dom 元素
使用 Array 做为 StringBuffer ，代替字符串拼接的操作
将循环控制量保存到局部变量
顺序无关的遍历时，用 while 替代 for
将条件分支，按可能性顺序从高到低排列
在同一条件子的多（ >2 ）条件分支时，使用 switch 优于 if
使用三目运算符替代条件分支
需要不断执行的时候，优先考虑使用 setInterval
```

### 15、javascript 对象的几种创建方式？
```
1. 工厂模式
2. 构造函数模式
3. 原型模式
4. 混合构造函数和原型模式
5. 动态原型模式
6. 寄生构造函数模式
7. 稳妥构造函数模式
```

### 16、javascript 继承的 6 种方法？
```
1. 原型链继承
2. 借用构造函数继承
3. 组合继承(原型+借用构造)
4. 原型式继承
5. 寄生式继承
6. 寄生组合式继承
```

### 17、eval 是做什么的？
```
1. 它的功能是把对应的字符串解析成 JS 代码并运行
2. 应该避免使用 eval，不安全，非常耗性能（2 次，一次解析成 js 语句，一次执行）
```

### 18、JavaScript 原型，原型链 ? 有什么特点？
```
1. 原型对象也是普通的对象，是对象一个自带隐式的 __proto__ 属性，原型也有可能有自己的原型，如果一个原型对象的原型不为 null 的话，我们就称之为原型链
2. 原型链是由一些用来继承和共享属性的对象组成的（有限的）对象链
```

### 19、分别阐述 split(),slice(),splice(),join()？
```
join()用于把数组中的所有元素拼接起来放入一个字符串。所带的参数为分割字符串的分隔符，默认是以逗号分开。归属于 Array
split()即把字符串分离开，以数组方式存储。归属于 Stringstring
slice()方法可从已有的数组中返回选定的元素。该方法并不会修改数组，而是返回一个子数组。如果想删除数组中的一段元素，应该使用方法 Array.splice()
splice() 方法向/从数组中添加/删除项目，然后返回被删除的项目。返回的是含有被删除的元素的数组。
```

### 20、http 状态码有那些？分别代表是什么意思？
```
100-199 用于指定客户端应相应的某些动作。
200-299 用于表示请求成功。
300-399 用于已经移动的文件并且常被包含在定位头信息中指定新的地址信息。
400-499 用于指出客户端的错误。
400 语义有误，当前请求无法被服务器理解。
401 当前请求需要用户验证
403 服务器已经理解请求，但是拒绝执行它。
500-599 用于支持服务器错误。
503 – 服务不可用
```

### 21、针对 jQuery 的优化方法？
```
优先使用 ID 选择器
jquery 获取到的 DOM 元素如果需要多次使用，建议使用一个变量将其保存起来，因为操作 DOM 的过程是非常耗费性能的
在 class 前使用 tag(标签名)
给选择器一个上下文
慎用 .live()方法（应该说尽量不要使用）
使用 data()方法存储临时变量
```

### 22、Zepto 的点透问题如何解决？
```
点透主要是由于两个 div 重合，例如：一个 div 调用 show()，一个 div 调用 hide()；
这个时候当点击上面的 div 的时候就会影响到下面的那个 div；
解决办法主要有 2 种：
github 上有一个叫做 fastclick 的库，它也能规避移动设备上 click 事件的延迟响
应，https://github.com/ftlabs/fastclick
将它用 script 标签引入页面（该库支持 AMD，于是你也可以按照 AMD 规范，用诸如
require.js 的模块加载器引入），并且在 dom ready 时初始化在 body 上，
根据分析，如果不引入其它类库，也不想自己按照上述 fastclcik 的思路再开发一套
东西，需要 1.一个优先于下面的“divClickUnder”捕获的事件；2.并且通过这个事件
阻止掉默认行为（下面的“divClickUnder”对 click 事件的捕获，在 ios 的 safari，
click 的捕获被认为和滚屏、点击输入框弹起键盘等一样，是一种浏览器默认行为，即
可以被 event.preventDefault()阻止的行为）。
```

### 23、知道各种 JS 框架(Angular, Backbone, Ember, React, Meteor, Knockout...)么? 能讲出他们各自的优点和缺点么?
```
知识面的宽度，流行框架要多多熟悉
angular、backbone、knockout 都是完整的 MV*框架
angular 是双向数据绑定的，backbone、knockout 是单向数据绑定的
React 只是单纯地 View 层
```

### 24、对前端界面工程师这个职位是怎么样理解的？它的前景会怎么样？
```
前端是最贴近用户的程序员，比后端、数据库、产品经理、运营、安全都近。
实现界面交互
提升用户体验
有了 Node.js，前端可以实现服务端的一些事情
前端是最贴近用户的程序员，前端的能力就是能让产品从 90 分进化到 100 分，甚至更好，
参与项目，快速高质量完成实现效果图，精确到 1px；
与团队成员，UI 设计，产品经理的沟通；
做好的页面结构，页面重构和用户体验；
处理 hack，兼容、写出优美的代码格式；
针对服务器的优化、拥抱最新前端技术。
其它相关的加分项：
都使用和了解过哪些编辑器?都使用和了解过哪些日常工具?
都知道有哪些浏览器内核?开发过的项目都兼容哪些浏览器?
瀑布流布局或者流式布局是否有了解
HTML5 都有哪些新的 API?
都用过什么代码调试工具?
是否有接触过或者了解过重构。
你遇到过比较难的技术问题是？你是如何解决的？
```

## NodeJs

### 1、对 Node 的优点和缺点提出了自己的看法：
```
（优点）因为 Node 是基于事件驱动和无阻塞的，所以非常适合处理并发请求，因此构建在 Node 上的代理服务器相比其他技术实现（如 Ruby）的服务器表现要好得多。此外，与 Node 代理服务器交互的客户端代码是由 javascript 语言编写的，因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情。
（缺点）Node 是一个相对新的开源项目，所以不太稳定，它总是一直在变，而且缺少足够多的第三方库支持。看起来，就像是 Ruby/Rails 当年的样子。
```

### 2、需求：实现一个页面操作不会整页刷新的网站，并且能在浏览器前进、后退时正确响应。给出你的技术实现方案？
```
至少给出自己的思路（url-hash,可以使用已有的一些框架 history.js 等）
```

### 3、Node.js 的适用场景？
```
实时应用：如在线聊天，实时通知推送等等（如 socket.io）
分布式应用：通过高效的并行 I/O 使用已有的数据
工具类应用：海量的工具，小到前端压缩部署（如 grunt），大到桌面图形界面应用程序
游戏类应用：游戏领域对实时和并发有很高的要求（如网易的 pomelo 框架）
利用稳定接口提升 Web 渲染能力
前后端编程语言环境统一：前端开发人员可以非常快速地切入到服务器端的开发（如著名的纯 Javascript 全栈式 MEAN 架构）
```

###  4、(如果会用 node)知道 route, middleware, cluster, nodemon, pm2, server-side rendering 么?
```
Nodejs 相关概念的理解程度
```

### 5、解释一下 Backbone 的 MVC 实现方式
```
流行的 MVC 架构模式
```

### 6、什么是“前端路由”?什么时候适合使用“前端路由”? “前端路由”有哪些优点和缺点?
```
熟悉前后端通信相关知识
前端路由就是在不进行后端请求的情况下对页面进行跳转
```

### 7、对 Node 的优点和缺点提出了自己的看法？
```
优点：
因为 Node 是基于事件驱动和无阻塞的，所以非常适合处理并发请求，因此构建在 Node上的代理服务器相比其他技术实现（如 Ruby）的服务器表现要好得多。
与 Node 代理服务器交互的客户端代码是由 javascript 语言编写的，因此客户端和服务
器端都用同一种语言编写，这是非常美妙的事情。
缺点：
Node 是一个相对新的开源项目，所以不太稳定，它总是一直在变。
缺少足够多的第三方库支持。看起来，就像是 Ruby/Rails 当年的样子（第三方库现在已经很丰富了，所以这个缺点可以说不存在了）。
```


## AJAX

### 1、如何解决跨域问题?
```
理解跨域的概念：协议、域名、端口都相同才同域，否则都是跨域
出于安全考虑，服务器不允许 ajax 跨域获取数据，但是可以跨域获取文件内容，所以基于这一点，可以动态创建 script 标签，使用标签的 src 属性访问 js 文件的形式获取 js脚本，并且这个 js 脚本中的内容是函数调用，该函数调用的参数是服务器返回的数据，为了获取这里的参数数据，需要事先在页面中定义回调函数，在回调函数中处理服务器返回的数据，这就是解决跨域问题的主流解决方案
```

### 2、页面编码和被请求的资源编码如果不一致如何处理？
```
对于 ajax 请求传递的参数，如果是 get 请求方式，参数如果传递中文，在有些浏览器会乱码，不同的浏览器对参数编码的处理方式不同，所以对于 get 请求的参数需要使用encodeURIComponent 函数对参数进行编码处理，后台开发语言都有相应的解码 api。对于 post 请求不需要进行编码
```

### 3、简述 ajax 的过程。
```
创建 XMLHttpRequest 对象,也就是创建一个异步调用对象
创建一个新的 HTTP 请求,并指定该 HTTP 请求的方法、URL 及验证信息
设置响应 HTTP 请求状态变化的函数
发送 HTTP 请求
获取异步调用返回的数据
使用 JavaScript 和 DOM 实现局部刷新
```

### 4、阐述一下异步加载。
```
异步加载的方案： 动态插入 script 标签
通过 ajax 去获取 js 代码，然后通过 eval 执行
script 标签上添加 defer 或者 async 属性
创建并插入 iframe，让它异步执行 js
```

### 5、解释 jsonp 的原理，以及为什么不是真正的 ajax
```
Jsonp 并不是一种数据格式，而 json 是一种数据格式，jsonp 是用来解决跨域获取数据的一种解决方案，具体是通过动态创建 script 标签，然后通过标签的 src 属性获取 js 文件中的 js 脚本，该脚本的内容是一个函数调用，参数就是服务器返回的数据，为了处理这些返回的数据，需要事先在页面定义好回调函数，本质上使用的并不是 ajax 技术
```

### 6、什么是 Ajax 和 JSON，它们的优缺点。
```
Ajax 是全称是 asynchronous JavaScript andXML，即异步 JavaScript 和 xml，用于在Web 页面中实现异步数据交互，实现页面局部刷新。
优点：可以使得页面不重载全部内容的情况下加载局部内容，降低数据传输量，避免用户不断刷新或者跳转页面，提高用户体验
缺点：对搜索引擎不友好；要实现 ajax 下的前后退功能成本较大；可能造成请求数的增加跨域问题限制；JSON 是一种轻量级的数据交换格式，ECMA 的一个子集
优点：轻量级、易于人的阅读和编写，便于机器（JavaScript）解析，支持复合数据类型（数组、对象、字符串、数字）
```

### 7、一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？
```
分为 4 个步骤：
当发送一个 URL 请求时，不管这个 URL 是 Web 页面的 URL 还是 Web 页面上每个资源的 URL，浏览器都会开启一个线程来处理这个请求，同时在远程 DNS 服务器上启动一个 DNS查询。这能使浏览器获得请求对应的 IP 地址。
浏览器与远程 Web 服务器通过 TCP 三次握手协商来建立一个 TCP/IP 连接。该握手包括一个同步报文，一个同步-应答报文和一个应答报文，这三个报文在 浏览器和服务器之间传递。该握手首先由客户端尝试建立起通信，而后服务器应答并接受客户端的请求，最后由客户端发出该请求已经被接受的报文。
一旦 TCP/IP 连接建立，浏览器会通过该连接向远程服务器发送 HTTP 的 GET 请求。远程服务器找到资源并使用 HTTP 响应返回该资源，值为 200 的 HTTP 响应状态表示一个正确的响应。
此时，Web 服务器提供资源服务，客户端开始下载资源。
 ```

### 8、ajax 请求的时候 get 和 post 方式的区别
```
get 一般用来进行查询操作，url 地址有长度限制，请求的参数都暴露在 url 地址当中，如果传递中文参数，需要自己进行编码操作，安全性较低。
post 请求方式主要用来提交数据，没有数据长度的限制，提交的数据内容存在于 http请求体中，数据不会暴漏在 url 地址中。
```

9、ajax 请求时，如何解释 json 数据
```
使用 eval() 或者 JSON.parse() 鉴于安全性考虑，推荐使用 JSON.parse()更靠谱，对数据的安全性更好。
```

9、两个数组的差集
```
方法一：
function arrChange( a, b ){
	var resultData = [];
	for(var i = 0; i < a.length; i++){
	    var flag = false;
	    for(var j = 0; j < b.length; j++){
	        if(b[j].id == a[i].id){
	            flag = true;
	            break;
	        }
	    }
	    if(!flag){
	        resultData.push(a[i]);
	    }
	}
}

方法二：
function arrChange( a, b ){
    for (var i = 0; i < b.length; i++) {
        for (var j = 0; j < a.length; j++) {
            if (a[j].id == b[i].id) {
                a.splice(j, 1);
                j = j - 1;
            }
        }
    }
    return a;
}
```
