# Css 知识总结

本部分主要是笔者在学习 Css 相关知识和一些相关面试题所做的笔记，如果出现错误，希望大家指出！

## 知识点总结

1. 介绍一下标准的 CSS 的盒子模型？低版本 IE 的盒子模型有什么不同的？
   
   ```
   （1）有两种盒子模型： IE 盒模型（border-box）、W3C 标准盒模型（content-box）。
   （2）盒模型： 分为 内容(content)、填充(padding)、边界(margin)、 边框(border) 四个部分
    
    IE盒模型和W3C标准盒模型的区别：

   （1）W3C 标准盒模型： 属性 width , height 只包含内容 content ，不包含 border 和 padding 。
   （2）IE 盒模型：     属性 width , height 包含 border 和 padding ，指的是 content + padding + border。

    在 ie8+ 浏览器中使用哪个盒模型可以由 box-sizing ( CSS 新增的属性)控制，默认值为 content-box ，即
    标准盒模型；如果将 box-sizing 设为 border-box 则用的是 IE 盒模型。如果在 ie6,7,8 中 DOCTYPE 缺
    失会将盒子模型解释为IE盒子模型。若在页面中声明了 DOCTYPE 类型，所有的浏览器都会把盒模型解释为 W3C 盒
    模型。
   ```
   
   详细的资料可以参考：
   [CSS盒模型详解](https://juejin.im/post/59ef72f5f265da4320026f76)


2. CSS选择符有哪些？
   ```
    （1）id 选择器（ # myid）
  	（2）类选择器（.myclassname）
  	（3）标签选择器（div, h1, p）
  	（4）后代选择器（h1 p）
  	（5）相邻后代选择器（子）选择器（ul > li）
  	（6）兄弟选择器（li ~ a）
    （7）相邻兄弟选择器（li + a）
  	（8）属性选择器（a[rel = "external"]）
  	（9）伪类选择器（a:hover, li:nth-child）
    （10）伪类选择器（::before、::after）
    （11）通配符选择器（ * ）
   ```

3. CSS 中哪些属性可以继承？
   ```
   每个 CSS 属性定义的概述都指出了这个属性是默认继承的，还是默认不继承的。这决定了当你没有为元素的属性指定
   值时该如何计算值。

   当元素的一个继承属性没有指定值时，则取父元素的同属性的计算值。只有文档根元素取该属性的概述中给定的初始值
   （这里的意思应该是在该属性本身的定义中的默认值）。

   当元素的一个非继承属性(在 Mozilla code 里有时称之为 reset property )没有指定值时，则取属性的初始值 initial value（该值在该属性的概述里被指定）。

   有继承性的属性：

   （1）字体系列属性
       font、font-family、font-weight、font-size、font-style、font-variant、font-stretch、font-size-adjust
    
   （2）文本系列属性
       text-indent、text-align、text-shadow、line-height、word-spacing、letter-spacing、text-transform、direction、color
    
   （3）表格布局属性
       caption-side border-collapse empty-cells
    
   （4）列表属性
       list-style-type、list-style-image、list-style-position、list-style

   （5）光标属性
       cursor
    
   （6）元素可见性
       visibility

   （7）还有一些不常用的；speak，page，设置嵌套引用的引号类型 quotes 等属性


   注意：当一个属性不是继承属性时，可以使用 inherit 关键字指定一个属性应从父元素继承它的值，inherit 
   关键字用于显式地指定继承性，可用于任何继承性/非继承性属性。


   ```

   详细的资料可以参考：
   [继承属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/inheritance)
   [CSS有哪些属性可以继承？](https://www.jianshu.com/p/34044e3c9317)


4. CSS 优先级算法如何计算？
   ```
   CSS 的优先级是根据样式声明的特殊性值来判断的。

   选择器的特殊性值分为四个等级，如下：

   （1） 标签内选择符                           x,0,0,0
   （2） ID 选择符                             0,x,0,0
   （3） class 选择符/属性选择符/伪类选择符 	    0,0,x,0
   （4） 元素和伪元素选择符                      0,0,0,x

   计算方法：

   （1） 每个等级的初始值为0
   （2） 每个等级的叠加为选择器出现的次数相加
   （3） 不可进位，比如 0,99,99,99
   （4） 依次表示为：0,0,0,0
   （5） 每个等级计数之间没关联
   （6） 等级判断从左向右，如果某一位数值相同，则判断下一位数值
   （7） 如果两个优先级相同，则最后出现的优先级高，!important 也适用
   （8） 通配符选择器的特殊性值为：0,0,0,0
   （9） 继承样式优先级最低，通配符样式优先级高于继承样式
   （10）!important（权重），它没有特殊性值，但它的优先级是最高的，为了方便记忆，可以认为它的特殊
        性值为1,0,0,0,0。

   计算实例：

   （1） #demo a{color: orange;}    /*特殊性值：0,1,0,1*/
   （2） div#demo a{color: red;}    /*特殊性值：0,1,0,2*/


   注意：

   （1）样式应用时，css 会先查看规则的权重（!important），加了权重的优先级最高，当权重相同的时候，
       会比较规则的特殊性。

   （2）特殊性值越大的声明优先级越高。

   （3）相同特殊性值的声明，根据样式引入的顺序，后声明的规则优先级高（距离元素出现最近的）。

   ```
   对于组合声明的特殊性值计算可以参考：
   [CSS优先级计算及应用](https://www.jianshu.com/p/1c4e639ff7d5)
   [css优先级计算规则](http://www.cnblogs.com/wangmeijian/p/4207433.html)


5. 关于伪类 LVHA 的解释
   ```
   a 标签有四种状态：链接访问前、链接访问后、鼠标滑过、激活，分别对应四种伪类:link、:visited、:hover、:active；

   当链接未访问过时：

   （1）当鼠标滑过 a 链接时，满足 :link 和 :hover 两个伪类，要改变 a 标签的颜色，就必须将 :hover 
       伪类在 :link 伪类后面声明；
   （2）当鼠标点击激活 a 链接时，同时满足 :link、:hover、:active 三种状态，要显示 a 标签激活时的
       样式（:active），必须将 :active 声明放到 :link 和 :hover 之后。因此得出 LVHA 这个顺序。

   当链接访问过时，情况基本同上，只不过需要将 :link 换成 :visited。

   这个顺序能不能变？可以，但也只有:link 和 :visited 可以交换位置，因为一个链接要么访问过要么没访问过，不
   可能同时满足，也就不存在覆盖的问题。
   ```

6. CSS3 新增伪类有那些？
   ```
   （1）elem:nth-child(n)        选中父元素下的第 n 个子元素，并且这个子元素的标签名为 elem ， n 可以
                                接受具体的数值，也可以接受函数。

   （2）elem:nth-last-child(n)   作用同上，不过是从后开始查找。

   （3）elem:last-child          选中最后一个子元素。

   （4）elem:only-child          如果 elem 是父元素下唯一的子元素，则选中之。

   （5）elem:nth-of-type(n)      选中父元素下第 n 个 elem 类型元素，n 可以接受具体的数值，也可以接受函数。

   （6）elem:first-of-type       选中父元素下第一个 elem 类型元素。

   （7）elem:last-of-type        选中父元素下最后一个 elem 类型元素。

   （8）elem:only-of-type        如果父元素下的子元素只有一个 elem 类型元素，则选中该元素。

   （9）elem:empty               选中不包含子元素和内容的 elem 类型元素。

   （10）elem:target             选择当前活动的 elem 元素。

   （11）:not(elem)              选择非 elem 元素的每个元素。
    
   （12）:enabled  	             控制表单控件的禁用状态。	

   （13）:disabled 		           控制表单控件的禁用状态。

    (14) :checked               单选框或复选框被选中。
 
   ```
   详细的资料可以参考：
   [css3新特性总结(伪类)](https://www.cnblogs.com/SKLthegoodman/p/css3.html)
   [浅谈CSS伪类和伪元素及CSS3新增伪类](https://blog.csdn.net/zhouziyu2011/article/details/58605705)
   
  
7. 如何居中 div ？
     * 水平居中：给 div 设置一个宽度，然后添加 margin:0 auto 属性
        ```css
          div{
          	 width:200px;
          	 margin:0 auto;
           }
        ```
      
      * 水平居中，利用 text-align: center 实现
        ```css
        .container {
          background: rgba(0, 0, 0, 0.5);
          text-align: center;
          font-size: 0;
        }

        .box {
          display: inline-block;
          width: 500px;
          height: 400px;
          background-color: pink;
        }
        ``` 
        
      * 让绝对定位的 div 居中
        ```css
         div{
            position: absolute;
            width: 300px;
            height: 300px;
            margin: auto;
            top: 0;
            left: 0;
            bottom: 0;
            right: 0;
            background-color: pink;	/* 方便看效果 */
          }
        ```

      * 水平垂直居中一
        ```css
         确定容器的宽高 宽500 高 300 的层
         设置层的外边距

         div {
           	position: absolute;	           	/* 绝对定位 */
           	width:500px;
           	height:300px;
           	top: 50%;
           	left: 50%;
           	margin: -150px 0 0 -250px;     	/* 外边距为自身宽高的一半 */
           	background-color: pink;	 	      /* 方便看效果 */
          }
        ```

      * 水平垂直居中二
        ```css
        未知容器的宽高，利用 `transform` 属性

        div {
           position: absolute;	      	/* 相对定位或绝对定位均可 */
           width:500px;
           height:300px;
           top: 50%;
           left: 50%;
           transform: translate(-50%, -50%);
           background-color: pink;	 	  /* 方便看效果 */

        }
        ```

      * 水平垂直居中三
        ```css
        利用 flex 布局
        实际使用时应考虑兼容性

        .container {
         	display: flex;
         	align-items: center; 		     /* 垂直居中 */
         	justify-content: center;	   /* 水平居中 */

        }
        .container div {
         	width: 100px;
         	height: 100px;
         	background-color: pink;		  /* 方便看效果 */
        }  
        ```

      * 水平垂直居中四
          ```css

           利用  text-align: center 和 vertical-align: middle 属性
              .container {
               position: fixed;
               top: 0;
               right: 0;
               bottom: 0;
               left: 0;
               background: rgba(0, 0, 0, 0.5);
               text-align: center;
               font-size: 0;
               white-space: nowrap;
               overflow: auto;
             }

             .container::after {
               content: "";
               display: inline-block;
               height: 100%;
               vertical-align: middle;
             }

             .box {
               display: inline-block;
               width: 500px;
               height: 400px;
               background-color: pink;
               white-space: normal;
               vertical-align: middle;
             }
          ```
  
8. display 有哪些值？说明他们的作用。
   ```
    block       	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
    none        	元素不显示，并从文档流中移除。
    inline      	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
    inline-block  默认宽度为内容宽度，可以设置宽高，同行显示。
    list-item   	象块类型元素一样显示，并添加样式列表标记。
    table       	此元素会作为块级表格来显示。
    inherit     	规定应该从父元素继承 display 属性的值。
   ```
   详细资料可以参考：
   [CSS display 属性](http://www.w3school.com.cn/css/pr_class_display.asp)

9. position 的值 relative 和 absolute 定位原点是？
   ```
   absolute
   生成绝对定位的元素，相对于值不为 static 的第一个父元素的 padding box进行定位，也可以理解为离自己这
   一级元素最近的一级 position 设置为 absolute 或者 relative 的父元素的 padding box 的左上角为原
   点的。

   fixed （老IE不支持）
   生成绝对定位的元素，相对于浏览器窗口进行定位。

   relative
   生成相对定位的元素，相对于其元素本身所在正常位置进行定位。

   static
   默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。
   
   inherit
   规定从父元素继承 position 属性的值。
   ```

10. CSS3 有哪些新特性？（根据项目回答，未掌握）
    ```
    新增各种CSS选择器	（: not(.input)：所有 class 不是“input”的节点）
    圆角		    （border-radius:8px）
    多列布局	    （multi-column layout）
    阴影和反射	（Shadow\Reflect）
    文字特效		（text-shadow）
    文字渲染		（Text-decoration）
    线性渐变		（gradient）
    旋转		 	（transform）
    缩放,定位,倾斜,动画,多背景
    例如:transform:\scale(0.85,0.90)\ translate(0px,-30px)\ skew(-9deg,0deg)\Animation:
    ```

11. 请解释一下 CSS3 的 Flexbox（弹性盒布局模型），以及适用场景？
    ```
    Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。

    任何一个容器都可以指定为 Flex 布局。行内元素也可以使用 Flex 布局。注意，设为 Flex 布局以后，子元
    素的 float、clear 和 vertical-align 属性将失效。

    采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。它的所有子元素自动成为容器
    成员，称为 Flex 项目（flex item），简称"项目"。

    容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。
    ```
    详细资料可以参考：
    [Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
    [Flex 布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)


12. 用纯 CSS 创建一个三角形的原理是什么？
    ```
    采用的是相邻边框连接处的均分原理。

    把上、左、右三条边隐藏掉（颜色设为 transparent）

    #demo {
    width: 0;
    height: 0;
    border-width: 20px;
    border-style: solid;
    border-color: transparent transparent red transparent;
    }
    ```

13. 一个满屏品字布局如何设计?
    ```
    简单的方式：
      	上面的 div 宽100%，
      	下面的两个 div 分别宽50%，
      	然后用 float 或者 inline 使其不换行即可
    ```

14. CSS 多列等高如何实现？
    ```
    （1）利用 padding-bottom|margin-bottom 正负值相抵。
        设置父容器设置超出隐藏（overflow:hidden），这样父容器的高度就还是它里面的列没有设定 
        padding-bottom 时的高度，当它里面的任一列高度增加了，则父容器的高度被撑到里面最高那
        列的高度，其他比这列矮的列会用它们的 padding-bottom 补偿这部分高度差。

    （2）利用 table-cell 所有单元格高度都相等的特性，来实现多列等高。

    （3）利用 flex 布局中项目 align-items 属性默认为 stretch，如果项目未设置高度或设为auto，
        将占满整个容器的高度的特性，来实现多列等高。

    ```

    详细资料可以参考：
    [前端应该掌握的CSS实现多列等高布局](https://juejin.im/post/5b0fb34151882515662238fd)
    [CSS：多列等高布局](https://codepen.io/yangbo5207/post/equh)

15. 经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用 hack 的技巧 ？
    ```
    （1） png24 位的图片在 iE6 浏览器上出现背景
         解决方案：做成 PNG8 ，也可以引用一段脚本处理。

    （2） 浏览器默认的 margin 和 padding 不同
         解决方案：加一个全局的 *{ margin:0; padding:0;} 来统一。

    （3） IE6 双边距 bug ：在 IE6 下，如果对元素设置了浮动，同时又设置了 margin-left 或      
         margin-right，margin 值会加倍。

         #box{ float:left; width:10px; margin:0 0 0 10px;} 

         这种情况之下 IE 会产生20 px 的距离
         解决方案：在 float 的标签样式控制中加入 _display:inline; 将其转化为行内属性。( _ 这个
         符号只有 ie6 会识别)

    （4） 渐进识别的方式，从总体中逐渐排除局部。
         首先，巧妙的使用"\9"这一标记，将 IE 游览器从所有情况中分离出来。 
         接着，再次使用 "+" 将 IE8 和 IE7 、IE6 分离开来，这样 IE8 已经独立识别。
        .bb{
           background-color:#f1ee18;      /*所有识别*/
           .background-color:#00deff\9;   /*IE6、7、8识别*/
           +background-color:#a200ff;     /*IE6、7识别*/
           _background-color:#1e0bd1;     /*IE6识别*/ 
        } 

    （5） IE下，可以使用获取常规属性的方法来获取自定义属性，也可以使用 getAttribute() 获取自定义
         属性；Firefox下,只能使用 getAttribute() 获取自定义属性
         解决方法：统一通过 getAttribute() 获取自定义属性。

    （6） IE下，event 对象有 x、y 属性，但是没有 pageX、pageY 属性; Firefox下，event 对象有 
         pageX、pageY 属性，但是没有 x、y 属性。
         解决方法：（条件注释）缺点是在 IE 浏览器下可能会增加额外的 HTTP 请求数。

    （7） Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示
         解决方法：
         
         
         1. 可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决。但是，在 chrome
            更新到27版本之后就不可以用了。

         2. 还可以使用 -webkit-transform: scale(0.5);注意-webkit-transform: scale(0.75); 
            收缩的是整个 span 的大小，这时候，必须要将 span 转换成块元素，可以使用 display：block/inline-block/...；

    （8） 超链接访问过后 hover 样式就不出现了，被点击访问过的超链接样式不再具有 hover 和 active 了
         解决方法：改变 CSS 属性的排列顺序 L-V-H-A

    （9） 怪异模式问题：漏写 DTD 声明，Firefox 仍然会按照标准模式来解析网页，但在 IE 中会触发怪异模
         式。为避免怪异模式给我们带来不必要的麻烦，最好养成书写 DTD 声明的好习惯。

    ```

16. li 与 li 之间有看不见的空白间隔是什么原因引起的？有什么解决办法？
    ```
    浏览器会把 inline 元素间的空白字符（空格、换行、Tab 等）渲染成一个空格。而为了美观。我们通常是一个
    <li> 放在一行，这导致 <li> 换行后产生换行字符，它变成一个空格，占用了一个字符的宽度。

    解决办法：

    （1）为 <li> 设置 float: left。不足：有些容器是不能设置浮动，如左右切换的焦点图等。

    （2）将所有 <li> 写在同一行。不足：代码不美观。

    （3）将 <ul> 内的字符尺寸直接设为0，即 font-size: 0。不足：<ul> 中的其他字符尺寸也被设为0，需要
        额外重新设定其他字符尺寸，且在 Safari 浏览器依然会出现空白间隔。

    （4）消除 <ul> 的字符间隔 letter-spacing: -8px，不足：这也设置了 <li> 内的字符间隔，因此需要将
        <li> 内的字符间隔设为默认 letter-spacing: normal。 
    ```

17. 为什么要初始化 CSS 样式？
    ```
    - 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对 CSS 初始化往往会出现浏览器之间
      的页面显示差异。

    - 当然，初始化样式会对 SEO 有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。

    最简单的初始化方法： * {padding: 0; margin: 0;} （强烈不建议）

    淘宝的样式初始化代码：
    body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; }
    body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; }
    h1, h2, h3, h4, h5, h6{ font-size:100%; }
    address, cite, dfn, em, var { font-style:normal; }
    code, kbd, pre, samp { font-family:couriernew, courier, monospace; }
    small{ font-size:12px; }
    ul, ol { list-style:none; }
    a { text-decoration:none; }
    a:hover { text-decoration:underline; }
    sup { vertical-align:text-top; }
    sub{ vertical-align:text-bottom; }
    legend { color:#000; }
    fieldset, img { border:0; }
    button, input, select, textarea { font-size:100%; }
    table { border-collapse:collapse; border-spacing:0; }
    ```

18. 什么是包含块，对于包含块的理解。
    ```
    包含块（containing block）就是元素用来计算和定位的一个框。

    （1）根元素（很多场景下可以看成是 <html> ）被称为“初始包含块”，其尺寸等同于浏览器可视窗口的大小。

    （2）对于其他元素，如果该元素的 position 是 relative 或者 static，则“包含块”由其最近的块容器
        祖先盒的 content box 边界形成。

    （3）如果元素 position:fixed，则“包含块”是“初始包含块”。

    （4）如果元素position:absolute，则“包含块”由最近的position 不为static
        的祖先元素建立，具体方式如下：

        如果该祖先元素是纯 inline 元素，则规则略复杂：
            • 假设给内联元素的前后各生成一个宽度为 0 的内联盒子（inline box），则这两
              个内联盒子的 padding box 外面的包围盒就是内联元素的“包含块”；
            • 如果该内联元素被跨行分割了，那么“包含块”是未定义的，也就是CSS2.1
              规范并没有明确定义，浏览器自行发挥
        否则，“包含块”由该祖先的 padding box 边界形成。
    
       如果没有符合条件的祖先元素，则“包含块”是“初始包含块”。

    ```

19. CSS 里的 visibility 属性有个 collapse 属性值是干嘛用的？在不同浏览器下以后什么区别？
    ```
    （1）对于一般的元素，它的表现跟 visibility：hidden; 是一样的。元素是不可见的，但此时仍占用页面空间。

    （2）但例外的是，如果这个元素是 table 相关的元素，例如 table 行，table group，table列，table  column 
        group，它的表现却跟 display: none 一样，也就是说，它们占用的空间也会释放。

    在不同浏览器下的区别：

    在谷歌浏览器里，使用 collapse 值和使用 hidden 值没有什么区别。

    在火狐浏览器、 Opera 和 IE11 里，使用 collapse 值的效果就如它的字面意思：table 的行会消失，它的下面一行
    会补充它的位置。

    ```
    详细资料可以参考：
    [CSS里的visibility属性有个鲜为人知的属性值：collapse](http://www.webhek.com/post/visibility-collapse.html)

20. 伪类与伪元素的区别
    ```
    css 引入伪类和伪元素概念是为了格式化文档树以外的信息。也就是说，伪类和伪元素是用来修饰不在文档树中的部分，
    比如，一句话中的第一个字母，或者是列表中的第一个元素。

    伪类用于当已有元素处于的某个状态时，为其添加对应的样式，这个状态是根据用户行为而动态变化的。比如说，当用户
    悬停在指定的元素时，我们可以通过 :hover 来描述这个元素的状态。

    伪元素用于创建一些不在文档树中的元素，并为其添加样式。它们允许我们为元素的某些部分设置样式。比如说，我们可
    以通过 ::before 来在一个元素前增加一些文本，并为这些文本添加样式。虽然用户可以看到这些文本，但是这些文本
    实际上不在文档树中。

    有时你会发现伪元素使用了两个冒号 (::) 而不是一个冒号 (:)。 这是 CSS3 的一部分，并尝试区分伪类和伪元素。
    大多数浏览器都支持这两个值。按照规则应该使用(::)而不是(:)，从而区分伪类和伪元素。但是，由于在旧版本的 W3C
    规范并未对此进行特别区分，因此目前绝大多数的浏览器都支持使用这两种方式表示伪元素。
    ```
    详细资料可以参考：
    [总结伪类与伪元素](http://www.alloyteam.com/2016/05/summary-of-pseudo-classes-and-pseudo-elements/)

21. width:auto 和 width:100% 的区别
    ```
    一般而言
    
    width:100% 会使元素 box 的宽度等于父元素的 content box 的宽度。

    width:auto 会使元素撑满整个父元素，margin、border、padding、content 区域会自动分配水平空间。 
    ```

22. 绝对定位元素与非绝对定位元素的百分比计算的区别
    ```
    绝对定位元素的宽高百分比是相对于临近的 position 不为 static 的祖先元素的 padding box 来计算的。

    非绝对定位元素的宽高百分比则是相对于父元素的 content box 来计算的。
    ```

23. 简单介绍使用图片 Base64 编码的优点和缺点。
    ```
    图片的 Base64 编码就是可以将一副图片数据编码成一串字符串，使用该字符串代替图像地址。

    （1）使用 Base64 不代表性能优化，使用 Base64 的好处是能够减少一个图片的 HTTP 请求，然而，与之同时
        付出的代价则是 CSS 文件体积的增大。而 CSS 文件体积的增大意味着什么呢？意味着 CRP 关键渲染路径
        的阻塞。

    （2）Base64 跟 CSS 混在一起，大大增加了浏览器需要解析 CSS 树的耗时。其实解析 CSS 树的过程是很快的，
        一般在几十微妙到几毫秒之间。
    ```
    详细资料可以参考：
    [玩转图片Base64编码](https://www.cnblogs.com/coco1s/p/4375774.html)


24. 'display'、'position' 和 'float' 的相互关系？
    
    ```
    （1） 首先我们判断 display 属性是否为 none，如果为 none ，则 position 和 float 属性的值不影响元
         素最后的表现。
         
    （2） 然后判断 position 的值是否为 absolute 或者 fixed ，如果是，则 float 属性失效，并且 display
         的值应该被设置为 table 或者 block，具体转换需要看初始转换值。
    
    （3） 如果 position 的值不为 absolute 或者 fixed，则判断 float 属性的值是否为 none ，如果不是，则
         display 的值则按上面的规则转换。注意，如果 position 的值为 relative 并且 float 属性的值存在，
         则 relative 失效。
     
    （4）如果 float 的值不为 none ，则判断元素是否为根元素，如果是根元素则 display 属性按照上面的规则转换，
         如果不是，则保持指定的 display 属性值不变。
    ```
    详细资料可以参考：
    [position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？](https://www.cnblogs.com/jackyWHJ/p/3756087.html)

25. margin 重叠问题的理解。
    
    ```
    块级元素的上外边距（margin-top）与下外边距（margin-bottom）有时会合并为单个外边距，这样的现象称为
    “margin 合并”。

    产生折叠的必备条件：margin 必须是邻接的!

    而根据w3c规范，两个 margin 是邻接的必须满足以下条件：

     • 必须是处于常规文档流（非 float 和绝对定位）的块级盒子,并且处于同一个 BFC 当中。
     • 没有线盒，没有空隙，没有 padding 和 border 将他们分隔开
     • 都属于垂直方向上相邻的外边距，可以是下面任意一种情况
     • 元素的 margin-top 与其第一个常规文档流的子元素的 margin-top
     • 元素的 margin-bottom 与其下一个常规文档流的兄弟元素的 margin-top
     • height 为 auto 的元素的 margin-bottom 与其最后一个常规文档流的子元素的 margin-bottom
     • 高度为0并且最小高度也为0，不包含常规文档流的子元素，并且自身没有建立新的 BFC 的元素的 margin-top
       和 margin-bottom


    margin 合并的3种场景：

    （1） 相邻兄弟元素 margin 合并。

          解决办法：
            • 设置块状格式化上下文元素（BFC）

    （2） 父级和第一个/最后一个子元素的 margin 合并。

          解决办法：
          
              对于 margin-top 合并，可以进行如下操作（满足一个条件即可）：
                • 父元素设置为块状格式化上下文元素；
                • 父元素设置 border-top 值；
                • 父元素设置 padding-top 值；
                • 父元素和第一个子元素之间添加内联元素进行分隔。

              对于 margin-bottom 合并，可以进行如下操作（满足一个条件即可）：
                • 父元素设置为块状格式化上下文元素；
                • 父元素设置 border-bottom 值；
                • 父元素设置 padding-bottom 值；
                • 父元素和最后一个子元素之间添加内联元素进行分隔；
                • 父元素设置height、min-height 或max-height。

     （3）空块级元素的 margin 合并。

         解决办法：
            • 设置垂直方向的 border；
            • 设置垂直方向的 padding；
            • 里面添加内联元素（直接 Space 键空格是没用的）；
            • 设置 height 或者 min-height。

    ```

26. 对 BFC 规范（块级格式化上下文：block formatting context）的理解？
    ```
    块格式化上下文（Block Formatting Context，BFC）是Web页面的可视化CSS渲染的一部分，是布局过程中生
    成块级盒子的区域，也是浮动元素与其他元素的交互限定区域。

    通俗来讲

    • BFC 是一个独立的布局环境，可以理解为一个容器，在这个容器中按照一定规则进行物品摆放，并且不会影响其
      它环境中的物品。
    • 如果一个元素符合触发 BFC 的条件，则 BFC 中的元素布局不受外部影响。

    创建 BFC

    （1）根元素或包含根元素的元素
    （2）浮动元素 float ＝ left | right 或 inherit（≠ none）
    （3）绝对定位元素 position ＝ absolute 或 fixed
    （4）display ＝ inline-block | flex | inline-flex | table-cell 或 table-caption
    （5）overflow ＝ hidden | auto 或 scroll (≠ visible)

    ```

    详细资料可以参考：
    [深入理解BFC和Margin Collapse](https://www.w3cplus.com/css/understanding-bfc-and-margin-collapse.html)
    [前端面试题-BFC(块格式化上下文)](https://segmentfault.com/a/1190000013647777)


27. 请解释一下为什么需要清除浮动？清除浮动的方式
    ```
    浮动元素可以左右移动，直到遇到另一个浮动元素或者遇到它外边缘的包含框。浮动框不属于文档流中的普通流，当元
    素浮动之后，不会影响块级元素的布局，只会影响内联元素布局。此时文档流中的普通流就会表现得该浮动框不存在一
    样的布局模式。当包含框的高度小于浮动框的时候，此时就会出现“高度塌陷”。

    清除浮动是为了清除使用浮动元素产生的影响。浮动的元素，高度会塌陷，而高度的塌陷使我们页面后面的布局不能
    正常显示。

    清除浮动的方式

    （1）使用 clear 属性清除浮动。参考 28。

    （2）使用 BFC 块级格式化上下文来清除浮动。参考 26。

        因为 BFC 元素不会影响外部元素的特点，所以 BFC 元素也可以用来清除浮动的影响，因为如果不清除，子元素浮动
        则父元素高度塌陷，必然会影响后面元素布局和定位，这显然有违 BFC 元素的子元素不会影响外部元素的设定。

    ```

28. 使用 clear 属性清除浮动的原理？
    ```
    使用 clear 属性清除浮动，其语法如下：

        clear: none | left | right | both

        如果单看字面意思，clear:left 应该是“清除左浮动”，clear:right 应该是“清除右浮动”的意思，实际上，这种
        解释是有问题的，因为浮动一直还在，并没有清除。

        官方对 clear 属性的解释是：“元素盒子的边不能和前面的浮动元素相邻。”，我们对元素设置 clear 属性是为了避
        免浮动元素对该元素的影响，而不是清除掉浮动。

        还需要注意的一点是 clear 属性指的是元素盒子的边不能和前面的浮动元素相邻，注意这里“前面的”3 个字，也就是
         clear 属性对“后面的”浮动元素是不闻不问的。考虑到float 属性要么就left 要么就right，不可能同时存在，同
        时由于 clear 属性对“后面的”浮动元素不闻不问，因此，当 clear:left 有效的时候，clear:right 必定无效，
        也就是此时clear:left 等同于设置clear:both；同样地，clear:right 如果有效也是等同于设置clear:both。
        由此可见，clear:left 和clear:right 这两个声明就没有任何使用的价值，至少在CSS 世界中是如此，直接使用
        clear:both 吧。

        一般使用伪元素的方式清除浮动

        .clear::after {
            content: '';
            display: table; // 也可以是'block'，或者是'list-item'
            clear: both;
        }

        clear 属性只有块级元素才有效的，而::after 等伪元素默认都是内联水平，这就是借助伪元素清除浮动影响时需要
        设置 display 属性值的原因。
    ```

29. zoom:1 的清除浮动原理?
    ```
    清除浮动，触发 hasLayout ；
    zoom 属性是 IE 浏览器的专有属性，它可以设置或检索对象的缩放比例。解决 ie 下比较奇葩的 bug 。
    譬如外边距（margin）的重叠，浮动清除，触发 ie 的 haslayout 属性等。

    来龙去脉大概如下：
    当设置了 zoom 的值之后，所设置的元素就会就会扩大或者缩小，高度宽度就会重新计算了，这里一旦改变 zoom 值时
    其实也会发生重新渲染，运用这个原理，也就解决了 ie 下子元素浮动时候父元素不随着自动扩大的问题。

    zoom 属性是 IE 浏览器的专有属性，火狐和老版本的 webkit 核心的浏览器都不支持这个属性。然而，zoom 现在已
    经被逐步标准化，出现在 CSS 3.0 规范草案中。

    目前非 ie 由于不支持这个属性，它们又是通过什么属性来实现元素的缩放呢？
    可以通过 css3 里面的动画属性 scale 进行缩放。
    ```

30. 移动端的布局用过媒体查询吗？
    ```
    假设你现在正用一台显示设备来阅读这篇文章，同时你也想把它投影到屏幕上，或者打印出来， 而显示设备、屏幕投影和
    打印等这些媒介都有自己的特点，CSS 就是为文档提供在不同媒介上展示的适配方法

    当媒体查询为真时，相关的样式表或样式规则会按照正常的级联规被应用。 当媒体查询返回假， 标签上带有媒体查询的
    样式表 仍将被下载 （只不过不会被应用）。

    包含了一个媒体类型和至少一个使用 宽度、高度和颜色等媒体属性来限制样式表范围的表达式。 CSS3加入的媒体查询使
    得无需修改内容便可以使样式应用于某些特定的设备范围。

    <style> @media (min-width: 700px) and (orientation: landscape){ .sidebar { display: none; } } </style>
    ```
    详细资料可以参考：
    [CSS3 @media 查询](http://www.runoob.com/cssref/css3-pr-mediaquery.html)

31. 使用 CSS 预处理器吗？喜欢哪个？
    ```
    SASS (SASS、LESS没有本质区别，只因为团队前端都是用的SASS)
    ```
32. CSS 优化、提高性能的方法有哪些？
    ```
    加载性能：

    （1） css 压缩：将写好的 css 进行打包压缩，可以减少很多的体积。
    （2） css 单一样式：当需要下边距和左边距的时候，很多时候选择: margin: top 0 bottom 0; 但 
         margin-bottom: bottom;margin-left: left; 执行的效率更高。
    （3） 减少使用 @import, 而建议使用 link， 因为后者在页面加载时一起加载，前者是等待页面加载完
         成之后再进行加载;
    
    选择器性能：

    （1）关键选择器（key selector）。选择器的最后面的部分为关键选择器（即用来匹配目标元素的部分）。
        CSS 选择符是从右到左进行匹配的。当使用后代选择器的时候，浏览器会遍历所有子元素来确定是否是
        指定的元素等等；

    （2）如果规则拥有 ID 选择器作为其关键选择器，则不要为规则增加标签。过滤掉无关的规则（这样样式系
        统就不会浪费时间去匹配它们了）。

    （3）避免使用通配规则，如 *{} 计算次数惊人！只对需要用到的元素进行选择。

    （4）尽量少的去对标签进行选择，而是用 class。

    （5）尽量少的去使用后代选择器，降低选择器的权重值。后代选择器的开销是最高的，尽量将选择器的深度降
         到最低，最高不要超过三层，更多的使用类来关联每一个标签元素。

    （6）了解哪些属性是可以通过继承而来的，然后避免对这些属性重复指定规则。

    渲染性能：

    （1）慎重使用高性能属性：浮动、定位。

    （2）尽量减少页面重排、重绘。

    （3）去除空规则：｛｝。空规则的产生原因一般来说是为了预留样式。去除这些空规则无疑能减少 css 文档体积。 

    （4）属性值为0时，不加单位。

    （5）属性值为浮动小数0.**，可以省略小数点之前的0。

    （6）标准化各种浏览器前缀：带浏览器前缀的在前。标准属性在后。

    （7）不使用 @import 前缀，它会影响 css 的加载速度。

    （8）选择器优化嵌套，尽量避免层级过深。

    （9）css雪碧图，同一页面相近部分的小图标，方便使用，减少页面的请求次数，但是同时图片本身会变大，使
         用时，优劣考虑清楚，再使用。

    （10）正确使用 display 的属性，由于 display 的作用，某些样式组合会无效，徒增样式体积的同时也影响
         解析性能。

    （11）不滥用 web 字体。对于中文网站来说 Web Fonts 可能很陌生，国外却很流行。web fonts通常体积庞大，
         而且一些浏览器在下载 web fonts 时会阻塞页面渲染损伤性能。 

     可维护性、健壮性：

     （1）将具有相同属性的样式抽离出来，整合并通过 class 在页面中进行使用,提高 css 的可维护性。

     （2）样式与内容分离：将 css 代码定义到外部 css 中。

    ```

    详细资料可以参考：
    [CSS 优化、提高性能的方法有哪些？](https://www.zhihu.com/question/19886806)
    [css优化，提高性能的方法](https://www.jianshu.com/p/4e673bf24a3b)

33. 浏览器是怎样解析 CSS 选择器的？
    ```
    样式系统从关键选择器开始匹配，然后左移查找规则选择器的祖先元素。
    只要选择器的子树一直在工作，样式系统就会持续左移，直到和规则匹配，或者是因为不匹配而放弃该规则。

    试想一下，如果采用从左至右的方式读取 CSS 规则，那么大多数规则读到最后（最右）才会发现是不匹配的，
    这样会做费时耗能，最后有很多都是无用的；而如果采取从右向左的方式，那么只要发现最右边选择器不匹配，
    就可以直接舍弃了，避免了许多无效匹配。
    ```
    详细资料可以参考：
    [探究 CSS 解析原理](https://juejin.im/entry/5a123c55f265da432240cc90)

34. 在网页中的应该使用奇数还是偶数的字体？为什么呢？
    
    ```
    （1）偶数字号相对更容易和 web 设计的其他部分构成比例关系。比如：当我用了 14 px 的正文字号，我可能会在一
        些地方  用 14 × 0.5 = 7 px 的 margin，在另一些地方用 14 × 1.5 = 21 px 的标题字号。
    
    （2）浏览器缘故，低版本的浏览器 ie6 会把奇数字体强制转化为偶数，即 13px 渲染为 14px。

    （3）系统差别，早期的 Windows 里，中易宋体点阵只有 12 和 14、15、16 px，唯独缺少 13 px。
    ```
    详细资料可以参考：
    [谈谈网页中使用奇数字体和偶数字体](https://blog.csdn.net/jian_xi/article/details/79346477)
    [现在网页设计中的为什么少有人用 11px、13px、15px 等奇数的字体？](https://www.zhihu.com/question/20440679)

35. margin 和 padding 分别适合什么场景使用？
    ```
    margin 是用来隔开元素与元素的间距；padding 是用来隔开元素与内容的间隔。
    margin 用于布局分开元素使元素与元素互不相干。
    padding 用于元素与内容之间的间隔，让内容（文字）与（包裹）元素之间有一段距离。

    何时应当使用 margin：
         • 需要在 border 外侧添加空白时。
         • 空白处不需要背景（色）时。
         • 上下相连的两个盒子之间的空白，需要相互抵消时。如15px + 20px 的 margin，将得到 20px
           的空白。

    何时应当时用 padding：
         • 需要在 border 内测添加空白时。
         • 空白处需要背景（色）时。
         • 上下相连的两个盒子之间的空白，希望等于两者之和时。如15px + 20px的 padding ，将得
           到 35px 的空白。
    ```

36. 抽离样式模块怎么写，说出思路，有无实践经验？[阿里航旅的面试题]
    ```
    我的理解是把常用的 css 样式单独做成 css 文件……通用的和业务相关的分离出来，通用的做成样式模块儿共享，
    业务相关的，放进业务相关的库里面做成对应功能的模块儿。
    ```
    详细资料可以参考：
    [CSS规范 - 分类方法](http://nec.netease.com/standard/css-sort.html)

37. 简单说一下 css3 的 all 属性。
    ```
    all 属性实际上是所有 CSS 属性的缩写，表示，所有的 CSS 属性都怎样怎样，但是，不包括 unicode-bidi 
    和 direction 这两个 CSS 属性。支持三个 CSS 通用属性值，initial, inherit, unset。

    initial 是初始值的意思，也就是该元素元素都除了 unicode-bidi 和 direction 以外的 CSS 属性都使
    用属性的默认初始值。

    inherit 是继承的意思，也就是该元素除了 unicode-bidi 和 direction 以外的 CSS 属性都继承父元素
    的属性值。

    unset 是取消设置的意思，也就是当前元素浏览器或用户设置的 CSS 忽略，然后如果是具有继承特性的 CSS ，
    如 color ， 则使用继承值；如果是没有继承特性的 CSS 属性，如 background-color， 则使用初始值。

    ```
    详细资料可以参考：
    [简单了解CSS3的all属性](https://www.zhangxinxu.com/wordpress/2016/03/know-about-css3-all/)


38. 为什么不建议使用统配符初始化 css 样式。
    ```
    采用 *{pading:0;margin:0;} 这样的写法好处是写起来很简单，但是是通配符，需要把所有的标签都遍历
    一遍，当网站较大时，样式比较多，这样写就大大的加强了网站运行的负载，会使网站加载的时候需要很长一段
    时间，因此一般大型的网站都有分层次的一套初始化样式。

    出于性能的考虑，并不是所有标签都会有 padding 和 margin ，因此对常见的具有默认 padding 和 margin
    的元素初始化即可，并不需使用通配符 * 来初始化。
    ```

39. absolute 的 containing block (包含块) 计算方式跟正常流有什么不同？
    ```
    （1）内联元素也可以作为“包含块”所在的元素；

    （2）“包含块”所在的元素不是父块级元素，而是最近的 position 不为 static 的祖先
        元素或根元素；

    （3）边界是 padding box 而不是 content box。
    ```

40. 对于 hasLayout 的理解？
    ```
    hasLayout 是 IE 特有的一个属性。很多的 ie 下的 css bug 都与其息息相关。在 ie 中，一个元素要么自己对自
    身的内容进行计算大小和组织，要么依赖于父元素来计算尺寸和组织内容。当一个元素的 hasLayout 属性值为 true 时，
    它负责对自己和可能的子孙元素进行尺寸计算和定位。虽然这意味着这个元素需要花更多的代价来维护自身和里面的内容，
    而不是依赖于祖先元素来完成这些工作。

    ```
    详细资料可以参考：
    [CSS基础篇--CSS中IE浏览器的hasLayout，IE低版本的bug根源](https://segmentfault.com/a/1190000010883974)
    [CSS魔法堂：hasLayout原来是这样的！](https://segmentfault.com/a/1190000004632071)

41. 元素竖向的百分比设定是相对于容器的高度吗？
    ```
    如果是 height 的话，是相对于容器高度。
    
    如果是 padding 或者 margin 竖直方向的属性则是相对于容器的宽度。
    ```

42. 全屏滚动的原理是什么？用到了 CSS 的哪些属性？（待深入实践）
    ```
    原理：有点类似于轮播，整体的元素一直排列下去，假设有5个需要展示的全屏页面，那么高度是500%，只是展示100%，
         容器及容器内的页面取当前可视区高度，同时容器的父级元素 overflow 属性值设为 hidden，通过更改容器 
         容器可视区的位置来实现全屏滚动效果。主要是响应鼠标事件，页面通过 CSS 的动画效果，进行移动。

    overflow：hidden；transition：all 1000ms ease；
    ```
    详细资料可以参考：
    [js实现网页全屏切换（平滑过渡），鼠标滚动切换](https://blog.csdn.net/liona_koukou/article/details/52680409)
    [用 ES6 写全屏滚动插件](https://juejin.im/post/5aeef41cf265da0ba0630de0)


43. 什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的IE？（待深入了解）
    ```
    响应式网站设计(Responsive Web design)是一个网站能够兼容多个终端，而不是为每一个终端做一个特定的版本。基
    本原理是通过媒体查询检测不同的设备屏幕尺寸做处理。页面头部必须有 meta 声明的 viewport 。
    ```
    详细资料可以参考：
    [响应式布局原理](https://blog.csdn.net/dreamerframework/article/details/8994741)
    [响应式布局的实现方法和原理](http://www.mahaixiang.cn/wzsj/278.html)

44. 视差滚动效果，如何给每页做不同的动画？（回到顶部，向下滑动要再次出现，和只出现一次分别怎么做？）
    ```
    视差滚动（Parallax Scrolling）是指多层背景以不同的速度移动，形成立体的运动效果，带来非常出色的视觉体验。
    ```
    详细资料可以参考：
    [如何实现视差滚动效果的网页？](https://www.zhihu.com/question/20990029)

45. ::before 和 :after 中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用。
    ```
    单冒号(:)用于 CSS3 伪类，双冒号(::)用于 CSS3 伪元素。（伪元素由双冒号和伪元素名称组成）
    双冒号是在当前规范中引入的，用于区分伪类和伪元素。不过浏览器需要同时支持旧的已经存在的伪元素写法，
    比如:first-line、:first-letter、:before、:after 等，
    而新的在 CSS3 中引入的伪元素则不允许再支持旧的单冒号的写法。

    想让插入的内容出现在其它内容前，使用::before，否者，使用::after；
    在代码顺序上，::after 生成的内容也比::before 生成的内容靠后。
    如果按堆栈视角，::after 生成的内容会在::before 生成的内容之上
    ```

46. 如何修改 chrome 记住密码后自动填充表单的黄色背景 ？
    ```
    chrome 表单自动填充后，input 文本框的背景会变成黄色的，通过审查元素可以看到这是由于 chrome 会默认给自
    动填充的 input 表单加上 input:-webkit-autofill 私有属性，然后对其赋予以下样式：

    {
        background-color: rgb(250, 255, 189) !important;
        background-image: none !important;
        color: rgb(0, 0, 0) !important;
    }

    对 chrome 默认定义的 background-color，background-image，color 使用 important 是不能提高其优先级
    的，但是其他属性可使用。

    使用足够大的纯色内阴影来覆盖 input 输入框的黄色背景，处理如下

    input:-webkit-autofill , textarea:-webkit-autofill, select:-webkit-autofill {
      -webkit-box-shadow: 0 0 0px 1000px white inset;
      border: 1px solid #CCC!important;
    }

    ```
    详细资料可以参考：
    [去掉chrome记住密码后的默认填充样式](https://blog.csdn.net/zsl_955200/article/details/78276209)
    [修改谷歌浏览器chrome记住密码后自动填充表单的黄色背景](https://blog.csdn.net/M_agician/article/details/73381706)


47. 怎么让 Chrome 支持小于12px 的文字？
    ```
    在谷歌下 css 设置字体大小为12px及以下时，显示都是一样大小，都是默认12px;

    解决办法：

    （1）可以使用 Webkit 的内核的 -webkit-text-size-adjust 的私有 CSS 属性来解决，只要 加了
        -webkit-text-size-adjust:none; 字体大小 就不受限制了。但是 chrome 更新到27版本之后
        就不可以用了。所以高版本 chrome 谷歌浏览器已经不再支持 -webkit-text-size-adjust 样式，
        所以要使用时候慎用。

    （2）还可以使用 css3 的 transform 缩放属性 -webkit-transform: scale(0.5);注意-webkit-transform: scale(0.75); 
        收缩的是整个元素的大小，这时候，如果是内联元素，必须要将内联元素转换成块元素，可以使用 display：block/inline-block/...；

    
    （3）使用图片：如果是内容固定不变情况下，使用将小于 12px 文字内容切出做图片，这样不影响兼容也不影响美观。
    ```
    详细资料可以参考：
    [谷歌浏览器不支持CSS设置小于12px的文字怎么办？](https://570109268.iteye.com/blog/2406562)


48. 让页面里的字体变清晰，变细用 CSS 怎么做？
    ```
     webkit 内核的私有属性： -webkit-font-smoothing，用于字体抗锯齿,使用后字体看起来会更清晰舒服。

     在 MacOS 测试环境下面设置 -webkit-font-smoothing: antialiased; 但是这个属性仅仅是面向 MacOS，
     其他操作系统设置后无效。
    ```
    详细资料可以参考：
    [让字体变的更清晰CSS 中 -webkit-font-smoothing](https://blog.csdn.net/huo_bao/article/details/50251585)

49. font-style 属性中 italic 和 oblique 的区别？
    ```
    italic 和 oblique 这两个关键字都表示“斜体”的意思。

    它们的区别在于， italic 是使用当前字体的斜体字体，而 oblique 只是单纯地让文字倾斜。如果当前字体没有对
    应的斜体字体，则退而求其次，解析为 oblique，也就是单纯形状倾斜。
    ```

50. position:fixed;在 android 下无效怎么处理？
    ```
    因为移动端浏览器默认的 viewport 叫做 layout viewport。在移动端显示时，因为 layout viewport 的宽度
    大于移动端屏幕的宽度，所以页面会出现滚动条左右移动，fiexed 的元素是相对 layout viewport 来固定位置的，
    而不是移动端屏幕来固定位置的，所以会出现感觉 fixed 无效的情况。

    如果想实现 fixed 相对于屏幕的固定效果，我们需要改变的是 viewport 的大小为 ideal viewport，可以如下设置：

    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no"/>
    ```
    详细资料可以参考：
    [移动前端开发之viewport的深入理解](https://www.cnblogs.com/2050/p/3877280.html)
    [说说移动前端中 viewport （视口）](https://www.html.cn/archives/5975)

51. 如果需要手动写动画，你认为最小时间间隔是多久，为什么？（阿里）
    ```
    多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60*1000 ms ＝ 16.7 ms
    ```

52. 如何让去除 inline-block 元素间间距？
    ```
    移除空格、使用 margin 负值、使用 font-size:0、letter-spacing、word-spacing
    ```
    详细资料可以参考：
    [去除inline-block元素间间距的N种方法](https://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

53. overflow: scroll 时不能平滑滚动的问题怎么处理？
    ```
    以下代码可解决这种卡顿的问题：-webkit-overflow-scrolling: touch;，是因为这行代码启用了硬件加速特性，
    所以滑动很流畅。
    ```
    详细资料可以参考：
    [解决页面使用overflow: scroll在iOS上滑动卡顿的问题](https://www.jianshu.com/p/1f4693d0ad2d)

54. 有一个高度自适应的 div，里面有两个 div，一个高度 100px，希望另一个填满剩下的高度。
    ```
    1. 外层 div 使用 position：relative；高度要求自适应的 div 使用position: absolute; top: 100px;
     bottom: 0; left: 0

    2. 使用 flex 布局，设置主轴为竖轴，第二个 div 的 flex-grow 为1。
    ```
    详细资料可以参考：
    [有一个高度自适应的div，里面有两个div，一个高度100px，希望另一个填满剩下的高度(三种方案)](https://blog.csdn.net/xutongbao/article/details/79408522)

55. png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过webp？
    ```
    （1）png 是便携式网络图片（Portable Network Graphics）是一种无损数据压缩位图文件格式.优点是：压缩
        比高，色彩好。 大多数地方都可以用。

    （2）jpg 是一种针对相片使用的一种失真压缩方法，是一种破坏性的压缩，在色调及颜色平滑变化做的不错。在 www 上，
        被用来储存和传输照片的格式。

    （3）gif 是一种位图文件格式，以8位色重现真色彩的图像。可以实现动画效果.

    （4）webp 格式是谷歌在2010年推出的图片格式，压缩率只有 jpg 的2/3，大小比 png 小了45%。缺点是压缩的时间
        更久了，兼容性不好，目前谷歌和 opera 支持。
    ```
    详细资料可以参考：
    [图片格式那么多，哪种更适合你？](http://zhaox.github.io/multimedia/2016/01/13/introducing-image-types)


56. 什么是 Cookie 隔离？（或者说：请求资源的时候不要让它带cookie怎么做）
    ```
    网站向服务器请求的时候，会自动带上 cookie 这样增加 表头信息量，使请求变慢。

    如果静态文件都放在主域名下，那静态文件请求的时候都带有的 cookie 的数据提交给 server 的，非常浪费流量，
    所以不如隔离开，静态资源放 CDN 。

    因为 cookie 有域的限制，因此不能跨域提交请求，故使用非主要域名的时候，请求头中就不会带有 cookie 数据，
    这样可以降低请求头的大小，降低请求时间，从而达到降低整体请求延时的目的。

    同时这种方式不会将 cookie 传入 Web Server，也减少了 Web Server 对 cookie 的处理分析环节，
    提高了 webserver 的 http 请求的解析速度。
    ```
    详细资料可以参考：
    [CDN是什么？使用CDN有什么优势？](https://www.zhihu.com/question/36514327?rf=37353035)


57.  style 标签写在 body 后与 body 前有什么区别？
     ```
     页面加载自上而下 当然是先加载样式。写在 body 标签后由于浏览器以逐行方式对 HTML 文档进行解析，当解析到
     写在尾部的样式表（外联或写在 style 标签）会导致浏览器停止之前的渲染，等待加载且解析样式表完成之后重新渲
     染，在 windows 的 IE 下可能会出现 FOUC 现象（即样式失效导致的页面闪烁问题）
     ```

58. 什么是 CSS 预处理器 / 后处理器？
    ```
    CSS 预处理器定义了一种新的语言，其基本思想是，用一种专门的编程语言，为 CSS 增加了一些编程的特性，将 CSS
    作为目标生成文件，然后开发者就只要使用这种语言进行编码工作。通俗的说，CSS 预处理器用一种专门的编程语言，进
    行 Web 页面样式设计，然后再编译成正常的 CSS 文件。
    预处理器例如：LESS、Sass、Stylus，用来预编译 Sass 或 less，增强了 css 代码的复用性，
    还有层级、mixin、变量、循环、函数等，具有很方便的UI组件模块化开发能力，极大的提高工作效率。

    CSS 后处理器 是对 CSS 进行处理，并最终生成 CSS 的 预处理器，它属于广义上的 CSS 预处理器。 我们很久以前
    就在用 CSS 后处理器 了，最典型的例子是 CSS 压缩工具（如 clean-css），只不过以前没单独拿出来说过。还有最
    近比较火的 Autoprefixer，以 Can I Use 上的 浏览器支持数据 为基础，自动处理兼容性问题。
    后处理器例如：PostCSS，通常被视为在完成的样式表中根据 CSS 规范处理 CSS，让其更有效；目前最常做的
    是给 CSS 属性添加浏览器私有前缀，实现跨浏览器兼容性的问题。
    ```
    详细资料可以参考：
    [CSS预处理器和后处理器](https://blog.csdn.net/yushuangyushuang/article/details/79209752)

59. 阐述一下 CSS Sprites
    ```
    将一个页面涉及到的所有图片都包含到一张大图中去，然后利用 CSS 的 background-image，background- repeat，
    background-position 的组合进行背景定位。利用 CSS Sprites 能很好地减少网页的 http 请求，从而大大的
    提高页面的性能；CSS Sprites 能减少图片的字节。
    ```

60. 使用 rem 布局的优缺点？
    ```
    优点：
    在屏幕分辨率千差万别的时代，只要将 rem 与屏幕分辨率关联起来就可以实现页面的整体缩放，使得在设备上的展现
    都统一起来了。而且现在浏览器基本都已经支持 rem 了，兼容性也非常的好。

    缺点：
    （1）在奇葩的 dpr 设备上表现效果不太好，比如 一些华为的高端机型用 rem 布局会出现错乱。

    （2）使用 iframe 引用也会出现问题。

    （3）rem 在多屏幕尺寸适配上与当前两大平台的设计哲学不一致。即大屏的出现到底是为了看得又大又清楚，还是为了
        看的更多的问题。
    ```
    详细资料可以参考：
    [css3的字体大小单位rem到底好在哪？](https://www.zhihu.com/question/21504656)
    [VW: 是时候放弃REM布局了](https://www.jianshu.com/p/e8ae1c3861dc)
    [为什么设计稿是750px](https://blog.csdn.net/Honeymao/article/details/76795089)
    [使用Flexible实现手淘H5页面的终端适配](https://github.com/amfe/article/issues/17)

