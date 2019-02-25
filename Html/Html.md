# Html 知识总结

本部分主要是笔者在学习 Html 相关知识和一些相关面试题所做的笔记，如果出现错误，希望大家指出！

## 知识点总结

1. Doctype 的作用
   ```
   <!DOCTYPE>声明位于 HTML 文档中的第一行，处于 <html> 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。
   DOCTYPE 不存在或格式不正确会导致文档以兼容模式呈现。
   ```

2. 标准模式与兼容模式各有什么区别？
   ``` 
   标准模式的排版 和 JS 运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式
   浏览器的行为以防止站点无法工作。
   ```

3. HTML5 为什么只需要写 <!DOCTYPE HTML>？
   ```
   HTML5 不基于 SGML，因此不需要对 DTD 进行引用，但是需要 doctype 来规范浏览器的行为（让浏览器按照它们应该的方式来运行）。
   
   而 HTML4.01基于 SGML ,所以需要对 DTD 进行引用，才能告知浏览器文档所使用的文档类型。
   ```

4. SGML 、 HTML 、XML 和 XHTML
   ```
   SGML 是标准通用标记语言，是一种定义电子文档结构和   描述其内容的国际标准语言，是所有电子文档标记语言的起源。
   
   HTML是超文本标记语言，主要是用于规定怎么显示网页。
   
   XML是可扩展标记语言是未来网页语言的发展方向，XML 和 HTML 的最大区别就在于 XML 的标签是可以自己创建的，数量无限多，而 
   HTML 的标签都是固定的而且数量有限。
   
   XHTML 也是现在基本上所有网页都在用的标记语言，他其实和 HTML 没什么本质的区别标签都一样，用法也都一样，就是比 HTML 更严格，
   比如标签必须都用小写，标签都必须有闭合标签等。
   ```

5. DTD 介绍
   ```
   DTD（Document Type Definition文档类型定义）是一组机器可读的规则，它们定义 XML 或 HTML 的特定版本中允许有什么，不允许
   有什么。在解析网页时，浏览器将使用这些规则检查页面的有效性并且采取相应的措施。
   
   DTD 是对 HTML 文档声明，还会影响浏览器的渲染模式（工作模式）。
   ```

6. 行内元素
   ```
   HTML4中，元素被分成两大类: inline (内联元素)与 block (块级元素)。一个行内元素只占据它对应标签的边框所包含的空间。
   
   常见的行内元素有 a b span img strong sub sup button input label select textarea
   ```
   

7. 块级元素
   ```
   块级元素占据其父元素（容器）的整个空间，因此创建了一个“块”。

   常见的块级元素有  div ul ol li dl dt dd h1 h2 h3 h4 h5 h6 p 
   ```


8. 行内元素与块级元素的区别
   ```
   HTML4中，元素被分成两大类: inline (内联元素)与 block (块级元素)。
   
   （1） 格式上，默认情况下，行内元素不会以新行开始，而块级元素会新起一行。
   （2） 内容上，默认情况下，行内元素只能包含文本和其他行内元素。而块级元素可以包含行内元素和其他块级元素。
   （3） 行内元素与块级元素属性的不同，主要是盒模型属性上：行内元素设置 width 无效，height 无效(可以设置  line-height)，
         margin 上下无效，padding 上下无效
   ```

9. HTML5 元素的分类
   ```
   HTML4中，元素被分成两大类: inline(内联元素)与block(块级元素)。但在实际的开发过程中，因为页面表现的需要，前端工程师经
   常把 inline 元素的 display 值设定为 block (比如a标签)，也经常把 block 元素的 display 值设定为 inline；之后更是
   出现了 inline-block 这一对外呈现 inline 、对内呈现 block 的属性。因此，简单地把 HTML 元素划分为 inline 与 block 
   已经不再符合实际需求。

   HTML5中，元素主要分为7类：Metadata Flow Sectioning Heading Phrasing Embedded Interactive
   ```

10. 空元素
    ```
    标签内没有内容的 HTML 内容被称为空元素。空元素是在开始标签中关闭的。

    常见的空元素有：br hr img input link meta
    ```

11. link 标签
    ```
    link 标签定义文档与外部资源的关系。

    link 元素是空元素，它仅包含属性。 此元素只能存在于 head 部分，不过它可出现任何次数。

    link 标签中的 rel 属性定义了当前文档与被链接文档之间的关系。常见的 stylesheet 指的是定义一个外部加载的样式表。
    ```

12. 页面导入样式时，使用 link 和 @import 有什么区别？
    ```
    （1） 从属关系区别。 @import 是 CSS 提供的语法规则，只有导入样式表的作用；link 是 HTML 提供的标签，不仅可以加载 CSS 文
         件，还可以定义 RSS、rel 连接属性、引入网站图标等。

    （2） 加载顺序区别。加载页面时，link 标签引入的 CSS 被同时加载；@import 引入的 CSS 将在页面加载完毕后被加载。

    （3）兼容性区别。@import 是 CSS2.1 才有的语法，故只可在 IE5+ 才能识别；link 标签作为 HTML 元素，不存在兼容性问题。

    （4） DOM可控性区别。可以通过 JS 操作 DOM ，插入 link 标签来改变样式；由于 DOM 方法是基于文档的，无法使用@import 的方式
         插入样式。
    ```

13. 浏览器的理解
    ```
    简单来说浏览器可以分为两部分，shell +内核。

    其中 shell 的种类相对比较多，内核则比较少。shell 是指浏览器的外壳：例如菜单，工具栏 等。主要是提供给用户界面操作，参数设置
    等等。它是调用内核来实现各种功能的。内核才是浏览器的核心。内核是基于标记语言显示内容的程序或模块。也有一些 浏览器并不区分外壳
    和内核。从 Mozilla 将 Gecko 独立出来后，才有了外壳和内核的明确划分。
    ```


14. 介绍一下你对浏览器内核的理解？
    ```
    主要分成两部分：渲染引擎(layout engineer或 Rendering Engine) 和 JS 引擎。

    渲染引擎：负责取得网页的内容（HTML、 XML 、图像等等）、整理讯息（例如加入 CSS 等），以及计算网页的显示方式， 然后会输出至
    显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它
    需要编辑、显示网络内容的应用程序都需要内核。

    JS引擎：解析和执行 javascript 来实现网页的动态效果。

    最开始渲染引擎和JS引擎并没有区分的很明确，后来 JS 引擎越来越独立，内核就倾向于只指渲染引擎。
    ```

15. 常见的浏览器内核比较
    ```
    Trident：这种浏览器内核是 IE 浏览器用的内核，因为在早期 IE 占有大量的市场份额，所以这种内核比较流行，以前有很多网页也是
    根据这个内核的标准来编写的，但是实际上这个内核对真正的网页标准 支持不是很好。但是由于 IE 的高市场 占有率，微软也很长时间没
    有更新 Trident 内核，就导致了 Trident 内核和 W3C 标准脱节。还有就是 Trident 内核的大量 Bug 等安全问题没有得到解决，
    加上一些专家学者公开自己认为 IE 浏览器不安全的观点，使很多用户开始转向其他浏览器。

    Gecko：这是 Firefox 和 Flock 所采用内核，这个内核的优点就是功能强大、丰富，可以支持很多复杂网页效果和浏览  器扩展接口，
    但是代价是也显而易见就是要消耗很多的资源，比如内存。

    Presto：Opera 曾经采用的就是 Presto 内核，Presto 内核被称为公认的浏览网页速度最快的内核，这得益于它在开发时的天生优势，
    在处理 JS 脚本等脚本语言时，会比其他的内核快3倍左右，缺点就是为了达到很快的速度而丢掉了一部分网页兼容性。

    Webkit：Webkit 是 Safari 采用的内核，它的优点就是网页浏览速度较快，虽然不及 Presto 但是也胜于 Gecko 和 Trident，缺
    点是对于网页代码的容错性不高，也就是说对网页代码的兼容性较低，会使一些编写不标准的网页无法正确显示。WebKit 前身是 KDE 小
    组的 KHTML 引擎，可以说 WebKit 是 KHTML 的一个开源的分支。

    Blink：谷歌在 Chromium Blog 上发表 博客，称将与苹果的开源浏览器核心 Webkit 分道扬镳，在 Chromium 项目中研发 Blink 
    渲染引擎（即浏览器核心），内置于 Chrome 浏览器之中。其实 Blink 引擎就是也就是 Webkit 的分支，就像Webkit 是 KHTML 的
    分支一样。Blink 引擎现在是谷歌公司与 Opera Software 共同研发，上面提到过的，Opera 弃用了自己的 Presto 内核，加入
     Google 阵营，跟随谷歌一起研发 Blink。

    ```
    详细的资料可以参考：

    [浏览器内核的解析和对比](http://www.cnblogs.com/fullhouse/archive/2011/12/19/2293455.html)

    [五大主流浏览器内核的源起以及国内各大浏览器内核总结](https://blog.csdn.net/Summer_15/article/details/71249203)


16. 常见浏览器所用内核
    ```
    （1） IE 浏览器内核：Trident 内核，也是俗称的 IE 内核；

    （2） Chrome 浏览器内核：统称为 Chromium 内核或 Chrome 内核，以前是 Webkit 内核，现在是 Blink 内核；

    （3） Firefox 浏览器内核：Gecko 内核，俗称 Firefox 内核；

    （4） Safari 浏览器内核：Webkit 内核；

    （5） Opera 浏览器内核：最初是自己的 Presto 内核，后来加入谷歌大军，从 Webkit 又到了 Blink 内核；

    （6） 360浏览器、猎豹浏览器内核：IE + Chrome 双内核；

    （7） 搜狗、遨游、QQ 浏览器内核：Trident（兼容模式）+ Webkit（高速模式）；

    （8） 百度浏览器、世界之窗内核：IE 内核；

    （9） 2345浏览器内核：好像以前是 IE 内核，现在也是 IE + Chrome 双内核了；

    （10） UC 浏览器内核：这个众口不一，UC 说是他们自己研发的 U3 内核，但好像还是基于 Webkit 和 Trident ，还有说是基于火狐内核。
    ```

17. HTML5 有哪些新特性、移除了那些元素？
    ```
    HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。

    新增的有：
     
    绘画 canvas;
    用于媒介回放的 video 和 audio 元素;
    本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失;
    sessionStorage 的数据在浏览器关闭后自动删除;
    语意化更好的内容元素，比如 article、footer、header、nav、section;
    表单控件，calendar、date、time、email、url、search;
    新的技术 webworker, websocket, Geolocation;

    移除的元素有：

    纯表现的元素：basefont，big，center，font, s，strike，tt，u;
    对可用性产生负面影响的元素：frame，frameset，noframes；
    ```

18. 如何处理 HTML5 新标签的浏览器兼容问题？
    ```
    （1） IE8/IE7/IE6支持通过 document.createElement 方法产生的标签，可以利用这一特性让这些浏览器支持 HTML5 新标签，浏览器
        支持新标签后，还需要添加标签默认的样式。

    （2） 当然也可以直接使用成熟的框架，比如 html5shim ;
        `<!--[if lt IE 9]>
        <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>
        <![endif]-->`

       [if lte IE 9]……[endif] 判断 IE 的版本，限定只有 IE9 以下浏览器版本需要执行的语句。
    ```

19. 简述一下你对 HTML 语义化的理解？
    ```
    （1） 用正确的标签做正确的事情。
    （2） html 语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;
    （3） 即使在没有样式 CSS 情况下也以一种文档格式显示，并且是容易阅读的;
    （4） 搜索引擎的爬虫也依赖于 HTML 标记来确定上下文和各个关键字的权重，利于 SEO ;
    （5） 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。
    ```

20. HTML5 的离线储存怎么使用，工作原理能不能解释一下？
    ```
    在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。

    原理：HTML5 的离线存储是基于一个新建的 .appcache 文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，
    这些资源就会像 cookie 一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。

    如何使用：

    （1）页面头部像下面一样加入一个manifest的属性。

    （2）在如下 cache.manifest 文件的编写离线存储的资源。
      	CACHE MANIFEST
      	#v0.11
      	CACHE:
      	js/app.js
      	css/style.css
      	NETWORK:
      	resourse/logo.png
      	FALLBACK:
      	/ /offline.html

        CACHE: 表示需要离线存储的资源列表，由于包含 manifest 文件的页面将被自动离线存储，所以不需要把页面自身也列出来。

        NETWORK: 表示在它下面列出来的资源只有在在线的情况下才能访问，他们不会被离线存储，所以在离线情况下无法使用这些资源。
        不过，如果在 CACHE 和 NETWORK 中有一个相同的资源，那么这个资源还是会被离线存储，也就是说 CACHE 的优先级更高。

        FALLBACK :表示如果访问第一个资源失败，那么就使用第二个资源来替换他，比如上面这个文件表示的就是如果访问根目录下任何
        一个资源失败了，那么就去访问 offline.html 。

    （3）在离线状态时，操作window.applicationCache进行需求实现。
    ```

    详细的使用可以参考：
    [HTML5 离线缓存-manifest简介](https://yanhaijing.com/html/2014/12/28/html5-manifest/)
    [有趣的HTML5：离线存储](https://segmentfault.com/a/1190000000732617)


21. 浏览器是怎么对 HTML5 的离线储存资源进行管理和加载的呢？
    ```
    在线的情况下，浏览器发现 html 头部有 manifest 属性，它会请求 manifest 文件，如果是第一次访问 app ，那么浏览器就会根
    据 manifest 文件的内容下载相应的资源并且进行离线存储。如果已经访问过 app 并且资源已经离线存储了，那么浏览器就会使用离线
    的资源加载页面，然后浏览器会对比新的 manifest 文件与旧的 manifest 文件，如果文件没有发生改变，就不做任何操作，如果文件
    改变了，那么就会重新下载文件中的资源并进行离线存储。

    离线的情况下，浏览器就直接使用离线存储的资源。
    ```

22. 请描述一下 cookies，sessionStorage 和 localStorage 的区别？
    ```
    cookie 是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。
    cookie 数据始终在同源（协议、主机、端口相同）的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。
    
    sessionStorage 和 localStorage 是 HTML5 Web Storage API 提供的，可以方便的在 web 请求之间保存数据。有了
    本地数据，就可以避免数据在浏览器和服务器间不必要地来回传递。不会自动把数据发给服务器，仅在本地保存。
    
    存储大小：
      	cookie 数据大小不能超过4 k 。
      	sessionStorage 和 localStorage 虽然也有存储大小的限制，但比 cookie 大得多，可以达到 5M 或更大。

    有期时间：
      	localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据。
      	sessionStorage  数据在当前浏览器窗口关闭后自动删除。也就是说只要这个浏览器窗口没有关闭，即使刷新页面或进入同源另一
                        页面，数据仍然存在。
      	cookie          设置的 cookie 过期时间之前一直有效，即使窗口或浏览器关闭。
     
    作用域：
        sessionStorage  只在同源的同窗口（或tab）中共享数据，不在不同的浏览器窗口中共享，即使是同一个页面。
        localStorage    在所有同源窗口中都是共享的。
        cookie          在所有同源窗口中都是共享的。
    ```

    详细的资料可以参考：
    [请描述一下cookies，sessionStorage和localStorage的区别？](https://segmentfault.com/a/1190000017423117)

23. iframe 有那些缺点？
    ```
    iframe 元素会创建包含另外一个文档的内联框架（即行内框架）。

    主要缺点有：

    （1） iframe 会阻塞主页面的 onload 事件。window 的 onload 事件需要在所有 iframe 加载完毕后(包含里
         面的元素)才会触发。在 Safari 和 Chrome 里，通过 JavaScript 动态设置 iframe 的 src 可以避免这
         种阻塞情况。
    （2） 搜索引擎的检索程序无法解读这种页面，不利于 SEO 。
    （3） iframe 和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
    （4） 浏览器的后退按钮失效。
    （5） 小型的移动设备无法完全显示框架。
    ```
    详细的资料可以参考：
    [使用iframe的优缺点](https://blog.csdn.net/yintianqin/article/details/72625785)

24. Label 的作用是什么？是怎么用的？
    ```
    label 标签来定义表单控制间的关系，当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。

    <label for="Name">Number:</label>
    <input type=“text“name="Name" id="Name"/>
    ```
25. HTML5 的 form 的自动完成功能是什么？
    ```
    autocomplete 属性规定输入字段是否应该启用自动完成功能。默认为启用，设置为 autocomplete=off 可以关
    闭该功能。

    自动完成允许浏览器预测对字段的输入。当用户在字段开始键入时，浏览器基于之前键入过的值，应该显示出在字段
    中填写的选项。

    autocomplete 属性适用于 <form>，以及下面的 <input> 类型：text, search, url, telephone, email, password, datepickers, range 以及 color。
    ```

26. 如何实现浏览器内多个标签页之间的通信? (阿里)
    ```
    （1） WebSocket
    （2） SharedWorker (只在 chrome 浏览器实现了)
    （3） 可以调用 localstorge、cookies 等本地存储方式，localstorge另一个浏览上下文里被添加、修改或
         删除时，它都会触发一个事件，我们通过监听事件，控制它的值来进行页面信息通信；
    ```
    详细的资料可以参考：

    [WebSocket 教程](http://www.ruanyifeng.com/blog/2017/05/websocket.html)
    [使用 Web Storage API](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
    [JavaScript 的多线程，Worker 和 SharedWorker](https://www.zhuwenlong.com/blog/article/590ea64fe55f0f385f9a12e5)
  

27. webSocket如何兼容低浏览器？(阿里)
    ```
    Adobe Flash Socket 、
    ActiveX HTMLFile (IE) 、
    基于 multipart 编码发送 XHR 、
    基于长轮询的 XHR
    ```

28. 页面可见性（Page Visibility API） 可以有哪些用途？
    ```
    通过 visibilityState 的值检测页面当前是否可见，以及打开网页的时间等;
    在页面被切换到其他后台进程的时候，自动暂停音乐或视频的播放；
    ```

    详细资料可以参考：
    [Page Visibility API 教程](http://www.ruanyifeng.com/blog/2018/10/page_visibility_api.html)

29. 如何在页面上实现一个圆形的可点击区域？
    ```
    （1）纯 html 实现 map + area
    （2）纯 css 实现 border-radius
    （3）纯 js 实现 需要求一个点在不在圆上简单算法、获取鼠标坐标等等
    ```
    详细资料可以参考：
    [如何在页面上实现一个圆形的可点击区域？](https://maizi93.github.io/2017/08/29/%E5%A6%82%E4%BD%95%E5%9C%A8%E9%A1%B5%E9%9D%A2%E4%B8%8A%E5%AE%9E%E7%8E%B0%E4%B8%80%E4%B8%AA%E5%9C%86%E5%BD%A2%E7%9A%84%E5%8F%AF%E7%82%B9%E5%87%BB%E5%8C%BA%E5%9F%9F%EF%BC%9F/)


30. 实现不使用 border 画出1 px 高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。
    
    ```html
     <div style="height:1px;overflow:hidden;background:red"></div>
    ```

31. title 与 h1 的区别
    ```
    title 属性没有明确意义只表示是个标题，h1 则表示层次明确的标题，对页面信息的抓取也有很大的影响。
    ```

32. b 与 strong 的区别和 i 与 em 的区别？
    ```
    从页面显示效果来看，被 <b> 和 <strong> 包围的文字将会被加粗，而被 <i> 和 <em> 包围的文字将以斜体
    的形式呈现。

    但是 <b> <i> 是自然样式标签，分别表示无意义的加粗，无意义的斜体，表现样式为 { font-weight: bolder }，
    仅仅表示「这里应该用粗体显示」或者「这里应该用斜体显示」，此两个标签在HTML4.01中并不被推荐使用。

    而 <em> 和 <strong> 是语义样式标签。 <em> 表示一般的强调文本，而 <strong>表示比 <em> 语义更强的的强调文本。
    
    使用阅读设备阅读网络时：<strong> 会重读，而 <b> 是展示强调内容。
    ``` 
    
    详细资料可以参考：
    [HTML5 中的 b/strong，i/em 有什么区别？](https://www.zhihu.com/question/19551271)


33. 前端需要注意哪些SEO
    ```
    （1）合理的title、description、keywords：搜索对着三项的权重逐个减小，title值强调重点即可，重要关键
        词出现不要超过2次，而且要靠前，不同页面title要有所不同；description把页面内容高度概括，长度合适，
        不可过分堆砌关键词，不同页面description有所不同；keywords列举出重要关键词即可

    （2）语义化的HTML代码，符合W3C规范：语义化代码让搜索引擎容易理解网页

    （3）重要内容HTML代码放在最前：搜索引擎抓取HTML顺序是从上到下，有的搜索引擎对抓取长度有限制，保证重要内
        容一定会被抓取

    （4）重要内容不要用js输出：爬虫不会执行js获取内容

    （5）少用iframe：搜索引擎不会抓取iframe中的内容

    （6）非装饰性图片必须加alt

    （7）提高网站速度：网站速度是搜索引擎排序的一个重要指标
    ```

34. <img> 的 title 和 alt 有什么区别
    ```
    title 通常当鼠标滑动到元素上的时候显示

    alt 是<img>的特有属性，是图片内容的等价描述，用于图片无法加载时显示、读屏器阅读图片。可提图片高可访问
    性，除了纯装饰图片外都必须设置有意义的值，搜索引擎会重点分析。
    ```

35. 语义化的理解
    ```
    （1）用正确的标签做正确的事情！
    （2）html 语义化就是让页面的内容结构化，便于对浏览器、搜索引擎解析；
    （3）在没有样式 CSS 情况下也以一种文档格式显示，并且是容易阅读的。
    （4）搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，利于 SEO。
    （5）使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解
    ```
36. Canvas 和 SVG 有什么区别？
    ```
    （1）svg 绘制出来的每一个图形的元素都是独立的 DOM 节点，能够方便的绑定事件或用来修改。canvas 输出的是
        一整幅画布。
    （2）svg 输出的图形是矢量图形，后期可以修改参数来自由放大缩小，不会是真和锯齿。而 canvas 输出标量画布，
        就像一张图片一样，放大会失真或者锯齿。
    ```

37. 网页验证码是干嘛的，是为了解决什么安全问题
    ```
    （1）区分用户是计算机还是人的公共全自动程序。可以防止恶意破解密码、刷票、论坛灌水
    （2）有效防止黑客对某一个特定注册用户用特定程序暴力破解方式进行不断的登陆尝试
    ```  

38. 渐进增强和优雅降级
    ```
    渐进增强 ：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

    优雅降级 ：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容
    ```
   
39. attribute 和 property 的区别是什么？
    ```
    attribute 是 dom 元素在文档中作为 html 标签拥有的属性；
    property 就是 dom 元素在 js 中作为对象拥有的属性。
    对于 html 的标准属性来说，attribute 和 property 是同步的，是会自动更新的
    但是对于自定义的属性来说，他们是不同步的
    ```

40. 对 web 标准、可用性、可访问性的理解
    ```
    可用性（Usability）：产品是否容易上手，用户能否完成任务，效率如何，以及这过程中用户的主观感受可好，
    是从用户的角度来看产品的质量。可用性好意味着产品质量高，是企业的核心竞争力

    可访问性（Accessibility）：Web 内容对于残障用户的可阅读和可理解性
    
    可维护性（Maintainability）：一般包含两个层次，一是当系统出现问题时，快速定位并解决问题的成本，成
    本低则可维护性好。二是代码是否容易被人理解，是否容易修改和增强功能。
    ```

41. ie 各版本和 chrome 可以并行下载多少个资源？
    ```
    （1）  IE6 2 个并发
    （2）  iE7 升级之后的 6 个并发，之后版本也是 6 个
    （3）  Firefox，chrome 也是6个
    ```

42. Flash、Ajax 各自的优缺点，在使用中如何取舍？
    ```
    Flash：
    （1） Flash适合处理多媒体、矢量图形、访问机器
    （2） 对CSS、处理文本上不足，不容易被搜索

    Ajax：
    （1） Ajax对CSS、文本支持很好，支持搜索
    （2） 多媒体、矢量图形、机器访问不足

    共同点：
    （1） 与服务器的无刷新传递消息
    （2） 可以检测用户离线和在线状态
    （3） 操作DOM
    ```

43. 哪些地方会出现 css 阻塞，哪些地方会出现 js 阻塞？
    ```
    js 的阻塞特性：所有浏览器在下载 JS 的时候，会阻止一切其他活动，比如其他资源的下载，内容的呈现等等。直
    到 JS 下载、解析、执行完毕后才开始继续并行下载其他资源并呈现内容。为了提高用户体验，新一代浏览器都支持
    并行下载 JS，但是 JS 下载仍然会阻塞其它资源的下载（例如.图片，css文件等）。
    由于浏览器为了防止出现 JS 修改 DOM 树，需要重新构建 DOM 树的情况，所以就会阻塞其他的下载和呈现。
    嵌入 JS 会阻塞所有内容的呈现，而外部 JS 只会阻塞其后内容的显示，2 种方式都会阻塞其后资源的下载。也就是
    说外部样式不会阻塞外部脚本的加载，但会阻塞外部脚本的执行。

    CSS 怎么会阻塞加载了？CSS 本来是可以并行下载的，在什么情况下会出现阻塞加载了(在测试观察中，IE6 下 CSS
     都是阻塞加载）
    当 CSS 后面跟着嵌入的 JS 的时候，该 CSS 就会出现阻塞后面资源下载的情况。而当把嵌入 JS 放到 CSS 前面，
    就不会出现阻塞的情况了。
    根本原因：因为浏览器会维持 html 中 css 和 js 的顺序，样式表必须在嵌入的 JS 执行前先加载、解析完。而嵌
    入的 JS 会阻塞后面的资源加载，所以就会出现上面 CSS 阻塞下载的情况。

    ```

44. 怎么重构页面？
    ```
    （1） 编写 CSS
    （2） 让页面结构更合理化，提升用户体验
    （3） 实现良好的页面效果和提升性能
    ```

45. 浏览器架构
    ```
    * 用户界面
      * 主进程
      * 内核
          * 渲染引擎
          * JS 引擎
              * 执行栈
          * 事件触发线程
              * 消息队列
                  * 微任务
                  * 宏任务
          * 网络异步线程
          * 定时器线程
    ```

46. meta 标签
    ```
    <!DOCTYPE html>  H5标准声明，使用 HTML5 doctype，不区分大小写
    <head lang=”en”> 标准的 lang 属性写法
    <meta charset=’utf-8′>    声明文档使用的字符编码
    <meta http-equiv=”X-UA-Compatible” content=”IE=edge,chrome=1″/>   优先使用 IE 最新版本和 Chrome
    <meta name=”description” content=”不超过150个字符”/>       页面描述
    <meta name=”keywords” content=””/>      页面关键词
    <meta name=”author” content=”name, email@gmail.com”/>    网页作者
    <meta name=”robots” content=”index,follow”/>      搜索引擎抓取
    <meta name=”viewport” content=”initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no”> 为移动设备添加 viewport
    <meta name=”apple-mobile-web-app-title” content=”标题”> iOS 设备 begin
    <meta name=”apple-mobile-web-app-capable” content=”yes”/>  添加到主屏后的标题（iOS 6 新增）
    是否启用 WebApp 全屏模式，删除苹果默认的工具栏和菜单栏
    <meta name=”apple-itunes-app” content=”app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL”>
    添加智能 App 广告条 Smart App Banner（iOS 6+ Safari）
    <meta name=”apple-mobile-web-app-status-bar-style” content=”black”/>
    <meta name=”format-detection” content=”telphone=no, email=no”/>  设置苹果工具栏颜色
    <meta name=”renderer” content=”webkit”>  启用360浏览器的极速模式(webkit)
    <meta http-equiv=”X-UA-Compatible” content=”IE=edge”>     避免IE使用兼容模式
    <meta http-equiv=”Cache-Control” content=”no-siteapp” />    不让百度转码
    <meta name=”HandheldFriendly” content=”true”>     针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓
    <meta name=”MobileOptimized” content=”320″>   微软的老式浏览器
    <meta name=”screen-orientation” content=”portrait”>   uc强制竖屏
    <meta name=”x5-orientation” content=”portrait”>    QQ强制竖屏
    <meta name=”full-screen” content=”yes”>              UC强制全屏
    <meta name=”x5-fullscreen” content=”true”>       QQ强制全屏
    <meta name=”browsermode” content=”application”>   UC应用模式
    <meta name=”x5-page-mode” content=”app”>    QQ应用模式
    <meta name=”msapplication-tap-highlight” content=”no”>    windows phone 点击无高光
    设置页面不缓存
    <meta http-equiv=”pragma” content=”no-cache”>
    <meta http-equiv=”cache-control” content=”no-cache”>
    <meta http-equiv=”expires” content=”0″>
    ```
    详细资料可以参考：
    [Meta标签用法大全](http://www.cnblogs.com/qiumohanyu/p/5431859.html)

47. css reset 和 normalize.css 有什么区别
    ```
    （1）两者都是通过重置样式，保持浏览器样式的一致性
    （2）前者几乎为所有标签添加了样式，后者保持了许多浏览器样式，保持尽可能的一致
    （3）后者修复了常见的桌面端和移动端浏览器的 bug：包含了 HTML5 元素的显示设置、预格式化文字的 font-size
        问题、在 IE9 中 SVG 的溢出、许多出现在各浏览器和操作系统中的与表单相关的 bug。
    （4）前者中含有大段的继承链
    （5）后者模块化，文档较前者来说丰富

    ```
