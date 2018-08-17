---
title: CSS常见面试题
date: 2016-06-16 13:01:41
categories:
	- 前端
tags:
	- 前端
	- Div+css
	- Html5+css3
	- 面试题
	- Web前端
---

## HTML和CSS

### 1、常用浏览器的内核分别是什么?
```
IE: trident 内核
Firefox：gecko 内核
Safari:webkit 内核
Opera:以前是 presto 内核，Opera 现已改用 Google Chrome 的 Blink 内核
Chrome:Blink(基于 webkit，Google 与 Opera Software 共同开发)
```

<!--more-->

### 2、HTML文件里Doctype是干什么的？
```
<!DOCTYPE> 声明位于文档中的最前面的位置，处于 <html> 标签之前。
此标签可告知浏览器文档使用哪种 HTML 或 XHTML 规范。（重点：告诉浏览器按照何种规范解析页面）
```

### 3、Quirks模式是什么？它和 tandards 模式有什么区别？
```
从 IE6 开始，引入了 Standards 模式，标准模式中，浏览器尝试给符合标准的文档在规范上的正确处理达到在指定浏览器中的程度。
在 IE6 之前 CSS 还不够成熟，所以 IE5 等之前的浏览器对 CSS 的支持很差， IE6 将对 CSS提供更好的支持，
然而这时的问题就来了，因为有很多页面是基于旧的布局方式写的，而如果 IE6 支持 CSS 则将令这些页面显示不正常，如何在即保证不破坏现有页面，又提供新的渲染机制呢？
在写程序时我们也会经常遇到这样的问题，如何保证原来的接口不变，又提供更强大的功能，尤其是新功能不兼容旧功能时。遇到这种问题时的一个常见做法是增加参数和分支，即当某个参数为真时，我们就使用新功能，而如果这个参数 不为真时，就使用旧功能，这样就能不破坏原有的程序，又提供新功能。IE6 也是类似这样做的，它将 DTD 当成了这个“参数”，因为以前的页面大家都不会去写 DTD，所以 IE6 就假定 如果写了 DTD，就意味着这个页面将采用对 CSS 支持更好的布局，而如果没有，则采用兼容之前的布局方式。这就是 Quirks模式（怪癖模式，诡异模式，怪异模式）。
区别：总体会有布局、样式解析和脚本执行三个方面的区别。
盒模型：在 W3C 标准中，如果设置一个元素的宽度和高度，指的是元素内容的宽度和高度，而在 Quirks 模式下，IE 的宽度和高度还包含了 padding 和 border。
设置行内元素的高宽：在 Standards 模式下，给<span>等行内元素设置 wdith 和 height 都不会生效，而在 quirks 模式下，则会生效。
设置百分比的高度：在 standards 模式下，一个元素的高度是由其包含的内容来决定的，如果父元素没有设置百分比的高度，子元素设置一个百分比的高度是无效的用
margin:0 auto 设置水平居中：使用 margin:0 auto 在 standards 模式下可以使元素水平
居中，但在 quirks 模式下却会失效。（还有很多，答出什么不重要，关键是看他答出的这些是不是自己经验遇到的，还是说都是看文章看的，甚至完全不知道。）
```

### 4、div+css 的布局较 table 布局有什么优点？
```
改版的时候更方便 只要改 css 文件。
页面加载速度更快、结构化清晰、页面显示简洁。
表现与结构相分离。
易于优化（seo）搜索引擎更友好，排名更容易靠前。
```

### 5、img的alt与title 有何异同？strong与em的异同？
```
a:alt(alt text):为不能显示图像、窗体或 applets 的用户代理（UA），alt 属性用来指定替换文字。替换文字的语言由 lang 属性指定。(在 IE 浏览器下会在没有 title 时把 alt当成 tool tip 显示)
title(tool tip):该属性为设置该属性的元素提供建议性的信息。
strong:粗体强调标签，强调，表示内容的重要性
em:斜体强调标签，更强烈强调，表示内容的强调点
```

### 6、渐进增强和优雅降级之间有什么不同？
```
enhancement：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。
优雅降级 graceful degradation：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。
区别：优雅降级是从复杂的现状开始，并试图减少用户体验的供给，而渐进增强则是从一个非常基础的，能够起作用的版本开始，并不断扩充，以适应未来环境的需要。降级（功能衰减）意味着往回看；而渐进增强则意味着朝前看，同时保证其根基处于安全地带。
“优雅降级”观点认为应该针对那些最高级、最完善的浏览器来设计网站。而将那些被认为“过时”或有功能缺失的浏览器下的测试工作安排在开发周期的最后阶段，并把测试对象限定为主流浏览器（如 IE、Mozilla 等）的前一个版本。
在这种设计范例下，旧版的浏览器被认为仅能提供“简陋却无妨 (poor, but passable)” 的浏览体验。你可以做一些小的调整来适应某个特定的浏
览器。但由于它们并非我们所关注的焦点，因此除了修复较大的错误之外，其它的差异将被直接忽略。
“渐进增强”观点则认为应关注于内容本身。内容是我们建立网站的诱因。有的网站展示它，有的则收集它，有的寻求，有的操作，还有的网站甚至会包含以上的种种，但相同点是它们全都涉及到内容。这使得“渐进增强”成为一种更为合理的设计范例。这也是它立即被 Yahoo! 所采纳并用以构建其“分级式浏览器支持 (Graded Browser Support)”策略的原因所在。那么问题来了。现在产品经理看到 IE6,7,8 网页效果相对高版本现代浏览器少了很多圆角，阴影（CSS3），要求兼容（使用图片背景，放弃 CSS3）
```

### 7、为什么利用多个域名来存储网站资源会更有效？
```
CDN 缓存更方便
突破浏览器并发限制
节约 cookie 带宽
节约主域名的连接数，优化页面响应速度
防止不必要的安全问题
```

### 8、网页标准和标准制定机构重要性的理解。
```
网页标准和标准制定机构都是为了能让 web 发展的更‘健康’，开发者遵循统一的标准，降低开发难度，开发成本，SEO 也会更好做，也不会因为滥用代码导致各种 BUG、安全问题，最终提高网站易用性。
```

### 9、cookies，sessionStorage 和 localStorage 的区别
```
sessionStorage （session）中的数据，这些数据只有在同一个会话中的页面才能访问并且当会话结束后数据也随之销毁。因此 sessionStorage 不是一种持久化的本地存储，仅仅是会话级别的存储。
而 localStorage 用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。
Web Storage 的概念和 cookie 相似，区别是它是为了更大容量存储设计的。
Cookie 的大小是受限的，并且每次你请求一个新的页面的时候 Cookie 都会被发送过去，这样无形中浪费了带宽，另外 cookie 还需要指定作用域，不可以跨域调用。
除此之外，Web Storage 拥有 setItem,getItem,removeItem,clear 等方法，不像 cookie需要前端开发者自己封装 setCookie，getCookie。但是 Cookie 也是不可以或缺的：Cookie的作用是与服务器进行交互，作为 HTTP 规范的一部分而存在 ，而 Web Storage 仅仅是为了在本地“存储”数据而生。
```

### 10、src 与 href 的区别
```
src 用于替换当前元素，href 用于在当前文档和引用资源之间确立联系。
src 是 source 的缩写，指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求 src 资源时会将其指向的资源下载并应用到文档内，例如 js 脚本，img 图片和 frame 等元素。
当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js 脚本放在底部而不是头部。
href 是 Hypertext Reference 的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，如果我们在文档中添加那么浏览器会识别该文档为 css 文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用 link 方式来加载 css，而不是使用@import 方式。
```

### 11、网页制作会用到的图片格式有哪些？
```
png-8，png-24，jpeg，gif，svg。
但是上面的那些都不是面试官想要的最后答案。面试官希望听到是 Webp。（是否有关注新技术，新鲜事物）
科普一下 Webp：WebP 格式，谷歌（google）开发的一种旨在加快图片加载速度的图片格式。图片压缩体积大约只有 JPEG 的 2/3，并能节省大量的服务器带宽资源和数据空间。Facebook Ebay 等知名网站已经开始测试并使用 WebP 格式。在质量相同的情况下，WebP 格式图像的体积要比 JPEG 格式图像小 40%
```

### 12、什么是微格式吗？在前端构建中应该考虑微格式吗？
```
微格式（Microformats）是一种让机器可读的语义化 XHTML 词汇的集合，是结构化数据的开放标准。是为特殊应用而制定的特殊格式。
优点：将智能数据添加到网页上，让网站内容在搜索引擎结果界面可以显示额外的提示。（应用范例：豆瓣，有兴趣自行 google）
```

### 13、一次js请求一般情况下有哪些地方会有缓存处理？
```
答案：dns 缓存，cdn 缓存，浏览器缓存，服务器缓存。
```

### 14、一个页面上有大量的图片，加载很慢，怎么优化这些图片的加载给用户更好的体验。
```
图片懒加载，在页面上的未可视区域可以添加一个滚动条事件，判断图片位置与浏览器顶端的距离与页面的距离，如果前者小于后者，优先加载。
如果为幻灯片、相册等，可以使用图片预加载技术，将当前展示图片的前一张和后一张优先下载。
如果图片为 css 图片，可以使用 CSSsprite，SVGsprite，Iconfont、Base64 等技术。
如果图片过大，可以使用特殊编码的图片，加载时会先加载一张压缩的特别厉害的缩略图，以提高用户体验。
如果图片展示区域小于图片的真实大小，则因在服务器端根据业务需要先行进行图片压缩，图片压缩后大小与展示一致。
```

### 15、你如何理解 HTML 结构的语义化？
```
当页面样式加载失败的时候能够让页面呈现出清晰的结构
有利于 seo 优化，利于被搜索引擎收录（更便于搜索引擎的爬虫程序来识别）
便于项目的开发及维护，使 html 代码更具有可读性，便于其他设备解析。
```

### 16、做好 SEO 需要考虑什么？
```
Meta 标签优化:主要包括主题（Title)，网站描述(Description)，和关键词（Keywords）。还有一些其它的隐藏文字比如 Author（作者），Category（目录），Language（编码语种）等。
放置关键词:关键词分析和选择是 SEO 最重要的工作之一。首先要给网站确定主关键词（一般在 5 个上下），然后针对这些关键词进行优化，包括关键词密度（Density），相关度（Relavancy），突出性（Prominency）等等。
虽然搜索引擎有很多，但是对网站流量起决定作用的就那么几个。比如英文的主要有Google，Yahoo，Bing 等；中文的有百度，搜狗，有道等。不同的搜索引擎对页面的抓取和索引、排序的规则都不一样。还要了解各搜索门户和搜索引擎之间的关系，比如 AOL 网页搜
索用的是 Google 的搜索技术，MSN 用的是 Bing 的技术。
Open Directory 自身不是搜索引擎，而是一个大型的网站目录，他和搜索引擎的主要区别是网站内容的收集方式不同。目录是人工编辑的，主要收录网站主页；搜索引擎是自动收集的，除了主页外还抓取大量的内容页面。
搜索引擎也需要生存，随着互联网商务的越来越成熟，收费的搜索引擎也开始大行其道。最典型的有 Overture 和百度，当然也包括 Google 的广告项目 Google Adwords。越来越多的人通过搜索引擎的点击广告来定位商业网站，这里面也大有优化和排名的学问，你得学会用最少的广告投入获得最多的点击。
网站做完了以后，别躺在那里等着客人从天而降。要让别人找到你，最简单的办法就是将网站提交（submit）到搜索引擎。如果你的是商业网站，主要的搜索引擎和目录都会要求你付费来获得收录（比如 Yahoo 要 299 美元），但是好消息是（至少到目前为止）最大的搜索引
擎 Google 目前还是免费，而且它主宰着 60％以上的搜索市场。链接交换和链接广泛度（Link Popularity）
网页内容都是以超文本（Hypertext）的方式来互相链接的，网站之间也是如此。除了搜索引擎以外，人们也每天通过不同网站之间的链接来 Surfing（“冲浪”）。其它网站到你的网站的链接越多，你也就会获得更多的访问量。更重要的是，你的网站的外部链接数越多，会被搜索引擎认为它的重要性越大，从而给你更高的排名。
合理的标签使用
```

### 17、怎么对一个 DOM 设置它的 CSS 样式？
```
外部样式表，引入一个外部 css 文件
内部样式表，将 css 代码放在 <head> 标签内部
内联样式，将 css 样式直接定义在 HTML 元素内部
```

### 18、CSS 都有哪些选择器？
```
派生选择器（用 HTML 标签申明）
id 选择器（用 DOM 的 ID 申明）
类选择器（用一个样式类名申明）
属性选择器（用 DOM 的属性申明，属于 CSS2，IE6 不支持，不常用，不知道就算了）
除了前 3 种基本选择器，还有一些扩展选择器，包括
后代选择器（利用空格间隔，比如 div .a{ }）
群组选择器（利用逗号间隔，比如 p,div,#a{ }）
那么问题来了，CSS 选择器的优先级是怎么样定义的？
基本原则：一般而言，选择器越特殊，它的优先级越高。也就是选择器指向的越准确，它的优先级就越高。
```

### 19、定义一个 DOM 元素不显示在浏览器可视范围内？
```
基本的：设置 display 属性为 none，或者设置 visibility 属性为 hidden
技巧性：设置宽高为 0，设置透明度为 0，设置 z-index 位置在-1000
```

### 20、超链接访问过后 hover 样式就不出现的问题是什么？
```
被点击访问过的超链接样式不在具有 hover 和 active 了,解决方法是改变 CSS 属性的
排列顺序: L-V-H-A（link,visited,hover,active）
```

### 21、什么是 Css Hack？ie6,7,8 的 hack 分别是什么？
```
针对不同的浏览器写不同的 CSS code 的过程，就是 CSS hack。示例如下：
#test {
width:300px;
height:300px;
background-color:blue; /*firefox*/
background-color:red\9; /*all ie*/
background-color:yellow; /*ie8*/
+background-color:pink; /*ie7*/
_background-color:orange; /*ie6*/ }
:root #test { background-color:purple\9; } /*ie9*/
@media all and (min-width:0px){ #test {background-color:black;} } /*opera*/
@media screen and (-webkit-min-device-pixel-ratio:0){ #test {background-color:gray;} } /*chrome
and safari*/
```

### 23、行内元素和块级元素的区别是什么？行内元素的 padding 和 margin 可设置吗？
```
块级元素(block)特性：总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示;宽度(width)、高度(height)、内边距(padding)和外边距(margin)都可控制;
内联元素(inline)特性：和相邻的内联元素在同一行;宽度(width)、高度(height)、内边距的 top/bottom(padding-top/padding-bottom)和外边
距的 top/bottom(margin-top/margin-bottom)都不可改变（也就是 padding 和 margin 的left 和 right 是可以设置的），就是里面文字或图片的大小。
那么问题来了，浏览器还有默认的天生 inline-block 元素（拥有内在尺寸，可设置高宽，但不会自动换行）：<input> 、<img> 、<button> 、<texterea> 、<label>。
```

### 24、什么是外边距重叠？重叠的结果是什么？
```
外边距重叠就是 margin-collapse。
在 CSS 当中，相邻的两个盒子（可能是兄弟关系也可能是祖先关系）的外边距可以结合成一个单独的外边距。这种合并外边距的方式被称为折叠，并且因而所结合成的外边距称为折叠外边距。
折叠结果遵循下列计算规则：
两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。
两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。
两个外边距一正一负时，折叠结果是两者的相加的和。
```

### 26、rgba()和 opacity 的透明效果有什么不同？
```
rgba()和 opacity 都能实现透明效果，但最大的不同是 opacity 作用于元素，以及元素内的所有内容的透明度，
而 rgba()只作用于元素的颜色或其背景色。（设置 rgba 透明的元素的子元素不会继承透明效果！）
```

### 27、让文字在垂直和水平方向上重叠的两个属性是什么？
```
垂直方向：line-height
水平方向：letter-spacing
关于 letter-spacing 的妙用可以用于消除 inline-block 元素间的换行符空格间隙问题。
```

### 28、如何垂直居中一个浮动元素？
方法一：已知元素的高宽
```
.div1{
background-color:#6699FF;
width:200px;
height:200px;
position: absolute; //父元素需要相对定位
top: 50%;
left: 50%;
margin-top:-100px ; //二分之一的 height，width
margin-left: -100px;
}
```
方法二:未知元素的高宽
```
.div1{
width: 200px;
height: 200px;
background-color: #6699FF;
margin:auto;
position: absolute; //父元素需要相对定位
left: 0;
top: 0;
right: 0;
bottom: 0;
}
```
如何垂直居中一个img?（用更简便的方法。）
```
.container //img的容器设置如下
{
display:table-cell;
text-align:center;
vertical-align:middle;
}
```

### 29、px 和 em 的区别
```
px 和 em 都是长度单位，区别是，px 的值是固定的，指定是多少就是多少，计算比较容易。
em 得值不是固定的，并且 em 会继承父级元素的字体大小。
浏览器的默认字体高都是16px。所以未经调整的浏览器都符合: 1em=16px。那么12px=0.75em,10px=0.625em。
```

### 30、”reset”的 CSS 文件如何使用？和 normalize.css 的不同之处？
```
重置样式非常多，凡是一个前端开发人员肯定有一个常用的重置 CSS 文件并知道如何使用它们。原因是不同的浏览器对一些元素有不同的
默认样式，如果你不处理，在不同的浏览器下会存在必要的风险，或者更有戏剧性的性发生。
你可能会用 Normalize 来代替你的重置样式文件。它没有重置所有的样式风格，但仅提供了一套合理的默认样式值。既能让众多浏览器达到一致和合理，但又不扰乱其他的东西（如粗
体的标题）。
在这一方面，无法做每一个复位重置。它也确实有些超过一个重置，它处理了你永远都不用考虑的怪癖，像 HTML 的 audio 元素不一致或 line-height 不一致。
```

### 31、Sass、LESS 是什么？为什么要使用他们？
```
他们是 CSS 预处理器。他是 CSS 上的一种抽象层。他们是一种特殊的语法/语言编译成 CSS。
例如 Less 是一种动态样式语言. 将 CSS 结构清晰，便于扩展。
可以方便地屏蔽浏览器私有语法差异。这个不用多说，封装对浏览器语法差异的重复处理，减少无意义的机械劳动。
可以轻松实现多重继承。
完全兼容 CSS 代码，可以方便地应用到老项目中。LESS 只是在 CSS 语法上做了扩展，所以老的 CSS 代码也可以与 LESS 代码一同编译。
```

### 32、display:none 与 visibility:hidden 的区别是什么？
```
display : 隐藏对应的元素但不挤占该元素原来的空间。
visibility: 隐藏对应的元素并且挤占该元素原来的空间。
```

### 33、CSS 中 link 和@import 的区别是：
```
Link 属于 html 标签，而@import 是 CSS 中提供的在页面加载的时候，link 会同时被加载，而@import 引用的 CSS 会在页面加载完成后才会加
载引用的 CSS
@import 只有在 ie5 以上才可以被识别，而 link 是 html 标签，不存在浏览器兼容性问题
Link 引入样式的权重大于@import 的引用（@import 是将引用的样式导入到当前的页面中）
```

### 34、BFC 是什么?
```
BFC（块级格式化上下文），一个创建了新的 BFC 的盒子是独立布局的，盒子内元素的布局不会影响盒子外面的元素。在同一个 BFC 中的两个相邻的盒子在垂直方向发生 margin 重叠的问题
BFC 是指浏览器中创建了一个独立的渲染区域，该区域内所有元素的布局不会影响到区域外元素的布局，这个渲染区域只对块级元素起作用
```

### 35、HTML 与 XHTML——二者有什么区别？
```
1. 所有的标记都必须要有一个相应的结束标记
2. 所有标签的元素和属性的名字都必须使用小写
3. 所有的 XML 标记都必须合理嵌套
4. 所有的属性必须用引号 "" 括起来
5. 把所有 < 和 & 特殊符号用编码表示
6. 给所有属性赋一个值
7. 不要在注释内容中使用 "--"
8. 图片必须有说明文字
```

### 36、html 常见兼容性问题？
```
双边距 BUG float 引起的 加入_display：inline
3像素问题 使用 float 引起的 使用 dislpay:inline -3px
超链接 hover 点击后失效 使用正确的书写顺序 link visited hover active
Ie z-index 问题 给父级添加 position:relative
Png 透明 使用 js 代码 改
Min-height 最小高度 ！Important 解决’
select 在 ie6 下遮盖 使用 iframe 嵌套
没有办法定义1px左右的宽度容器（IE6默认的行高造成的，使用over:hidden,zoom:0.08 line-height:1px）
IE5-8 不支持 opacity，解决办法：
.opacity {
opacity: 0.4
filter: alpha(opacity=60); /* for IE5-7 */
-ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=60)"; /* for IE8*/
}
IE6 不支持 PNG 透明背景，解决办法: IE6 下使用 gif 图片,或是做成 PNG8.
```

### 37、对 WEB 标准以及 W3C 的理解与认识
```
答：标签闭合、标签小写、不乱嵌套、提高搜索机器人搜索几率、使用外 链 css 和 js 脚本、结构行为表现的分离、文件下载与页面速度更快、内容能被更多的用户所访问、内容能被更广泛的设备所访问、更少的代码和组件，容易维 护、改版方便，不需要变动页面内容、提供打印版本而不需要复制内容、提高网站易用性。
```

### 38、行内元素、块级元素、空(void)元素有哪些?CSS 的盒模型?
```
块级元素：div p h1 h2 h3 h4 form ul
行内元素: a b br i span input select
Css盒模型:内容，border ,margin，padding
知名的空元素：<br><hr><img><input><link><meta>
鲜为人知的是： <area><base><col><command><embed><keygen><param><source><track><wbr>
```

### 39、前端页面有哪三层构成，分别是什么?作用是什么?
```
结构层 Html 表示层 CSS 行为层 js。
```

### 40、Doctype 作用? 严格模式与混杂模式区分它们有何意义?
```
<!DOCTYPE> 声明位于文档中的最前面，处于 <html> 标签之前。告知浏览器的解析器，用什么文档类型 规范来解析这个文档。
严格模式的排版和 JS 运作模式是 以该浏览器支持的最高标准运行。
在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。
DOCTYPE 不存在或格式不正确会导致文档以混杂模式呈现。
```

### 41、b 标签和 strong 标签,i 标签和 em 标签的区别？
```
后者有语义，前者则无。
```


### 42、CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？
```
* 1.id 选择器（ # myid）
2.类选择器（.myclassname）
3.标签选择器（div, h1, p）
4.相邻选择器（h1 + p）
5.子选择器（ul < li）
6.后代选择器（li a）
7.通配符选择器（ * ）
8.属性选择器（a[rel = "external"]）
9.伪类选择器（a: hover, li: nth - child）
* 可继承： font-size font-family color, UL LI DL DD DT;
* 不可继承 ：border padding margin width height ;
* 优先级就近原则，样式定义最近者为准;
* 载入样式以最后载入的定位为准;
优先级为:!important > id > class > tag
important 比 内联优先级高
```

## HTML5和CSS3

### 1、CSS3 有哪些新特性？
```
CSS3 实现圆角（border-radius），阴影（box-shadow），
对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）
transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px)skew(-9deg,0deg);// 旋转,缩放,定位,倾斜
增加了更多的 CSS 选择器 多背景 rgba
在 CSS3 中唯一引入的伪元素是 ::selection.
媒体查询, 多栏布局, border-image
```

### 2、html5 有哪些新特性、移除了那些元素？如何区分 HTML 和 HTML5？
```
新特性：HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，地理定位等功能的增加
拖拽释放(Drag and drop) API
语义化更好的内容标签（header,nav,footer,aside,article,section）
音频、视频 API(audio,video)
画布(Canvas) API
地理(Geolocation) API
本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
sessionStorage 的数据在浏览器关闭后自动删除
表单控件，calendar、date、time、email、url、search
新的技术 webworker, websocket, Geolocation
移除的元素：
纯表现的元素：basefont，big，center，font, s，strike，tt，u；
对可用性产生负面影响的元素：frame，frameset，noframes；
支持 HTML5 新标签：
1. IE8/IE7/IE6 支持通过 document.createElement 方法产生的标签，可以利用这一特性让这些浏览器支持 HTML5 新标签，浏览器支持新标签后，还需要添加标签默认的样式（当然最好的方式是直接使用成熟的框架、使用最多的是 html5shim 框架）：
<!--[if lt IE 9]>
<script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>
<![endif]-->
```
```
DOCTYPE 声明新增的结构元素、功能元素本地存储（Local Storage ）和 cookies（储存在用户本地终端上的数据）
Cookies:服务器和客户端都可以访问；大小只有 4KB 左右；有有效期，过期后将会删除；
本地存储：只有本地浏览器端可访问数据，服务器不能访问本地存储直到故意通过 POST 或者 GET 的通道发送到服务器；每个域 5MB；没有过期数据，它将保留知道用户从浏览器清除或者使用 Javascript 代码移除
```
### 4、如何实现浏览器内多个标签页之间的通信?
```
调用 localstorge、cookies 等本地存储方式
```

### 5、你如何对网站的文件和资源进行优化？
```
文件合并
文件最小化/文件压缩
使用 CDN 托管
缓存的使用
```

### 6、什么是响应式设计？
```
它是关于网页制作的过程中让不同的设备有不同的尺寸和不同的功能。响应式设计是让所有的人能在这些设备上让网站运行正常
```

### 7、新的 HTML5 文档类型和字符集是？
```
HTML5 文档类型：<!doctype html>
HTML5 使用的编码<meta charset=”UTF-8”>
```

### 8、HTML5 Canvas 元素有什么用？
```
Canvas 元素用于在网页上绘制图形，该元素标签强大之处在于可以直接在 HTML 上进行图形操作。
```

### 9、HTML5 存储类型有什么区别？
```
Media API、Text Track API、Application Cache API、User Interaction、Data TransferAPI、Command API、Constraint Validation API、History API
```

### 10、CSS3 新增伪类有那些？
```
p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
p:last-of-type 选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
p:only-of-type 选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
p:only-child 选择属于其父元素的唯一子元素的每个 <p> 元素。
p:nth-child(2) 选择属于其父元素的第二个子元素的每个 <p> 元素。
:enabled、:disabled 控制表单控件的禁用状态。
:checked，单选框或复选框被选中。
```

### 11、前端应该如何高质量完成工作?
```
首先划分成头部、body、脚部；
实现效果图是最基本的工作，精确到 2px；
与设计师，产品经理的沟通和项目的参与
做好的页面结构，页面重构和用户体验
处理 hack，兼容、写出优美的代码格式
针对服务器的优化、拥抱 HTML5。
```

### 12、css中content属性的作用
```
css 的 content 属性专门应用在 before/after 伪元素上，用来插入生成内容。最常见的应用是利用伪类清除浮动。
//一种常见利用伪类清除浮动的代码
.clearfix:after {
content:"."; //这里利用到了 content 属性
display:block;
height:0;
visibility:hidden;
clear:both; }
.clearfix {
*zoom:1;
}
after 伪元素通过 content 在元素的后面生成了内容为一个点的块级素，再利用clear:both 清除浮动。
那么问题继续还有，知道 css 计数器（序列数字字符自动递增）吗？如何通过css content 属性实现 css 计数器？
css 计数器是通过设置 counter-reset 、counter-increment 两个属性 、及counter()/counters()一个方法配合 after / before 伪类实现。
```

### 13、在HTML5页面中嵌入音频
```
HTML 5 包含嵌入音频文件的标准方式，支持的格式包括 MP3、Wav 和 Ogg：
<audio controls>
<source src="jamshed.mp3" type="audio/mpeg">
Your browser does'nt support audio embedding feature.
</audio>
```

### 14、在HTML5页面中嵌入视频
```
和音频一样，HTML5 定义了嵌入视频的标准方法，支持的格式包括：MP4、WebM 和 Ogg：
<video width="450" height="340" controls>
<source src="jamshed.mp4" type="video/mp4">
Your browser does'nt support video embedding feature.
</video>
```

### 15、写一个css3幻灯片效果页面
```
.ani{
width:480px;
height:320px;
margin:50px auto;
overflow: hidden;
box-shadow:0 0 5px rgba(0,0,0,1);
background-size: cover;
background-position: center;
-webkit-animation-name: "loops";
-webkit-animation-duration: 20s;
-webkit-animation-iteration-count: infinite;
}
@-webkit-keyframes "loops" {
0%
{ background:url('') no-repeat;
}
50% {
background:url('') no-repeat;
}
100% {
background:url('') no-repeat;
}
}
```


