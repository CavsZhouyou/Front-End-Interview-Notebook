# Css 知识总结

本部分主要是笔者在学习 Css 相关知识和一些相关面试题所做的笔记，如果出现错误，希望大家指出！

## 知识点总结

1. 介绍一下标准的 CSS 的盒子模型？低版本 IE 的盒子模型有什么不同的？
   
   ```
   （1）有两种盒子模型： IE 盒模型、W3C 标准盒模型。
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
    1.id选择器（ # myid）
  	2.类选择器（.myclassname）
  	3.标签选择器（div, h1, p）
  	4.相邻选择器（h1 + p）
  	5.子选择器（ul > li）
  	6.后代选择器（li a）
  	7.通配符选择器（ * ）
  	8.属性选择器（a[rel = "external"]）
  	9.伪类选择器（a:hover, li:nth-child）
   ```

3. CSS 中哪些属性可以继承？
   ```
   css 样式表继承指的是，特定的 css 属性向下传递到后代元素。对于一些可以继承的属性，可以只设置上级的 css 样式表树形，子级（下级）不用设置，会自动继承此 css 属性，可以减少 css 代码，便于维护。

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


   但这些属性并不是所有类型的元素都能够继承，我们可以做如下分类

   所有元素可以继承的属性：visibility、cursor

   内联元素可以继承的属性：字体系列属性、除 text-indent、text-align 之外的文本系列属性

   块级元素可以继承的属性: text-indent、text-align


   注意：当一个属性不是和继承属性时，可以使用 inherit 关键字指定一个属性应从父元素继承它的值，inherit 
   关键字可用于任何 HTML 元素上的任何 CSS 属性。


   ```

   详细的资料可以参考：
   [继承属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/inheritance)
   [CSS有哪些属性可以继承？](https://www.jianshu.com/p/34044e3c9317)


4. CSS 优先级算法如何计算？
   ```
   CSS 的优先级是根据样式声明的特殊性值来判断的。
   
   特殊性值越大的声明优先级越高。
   
   相同特殊性值的声明，如果是在同一种引入方式内（例如都是在外部样式中），则最后出现的优先级最高。但如果是在不同的
   引入方式中（例如在内部样式和外部样式中都有相同特殊性值的声明），则内部样式的声明的优先级高于外部样式声明的优先级。

   特殊：!important 的优先级最高

   声明样式的优先级，一般来说满下面这个规则：

   （1）继承不如指定
   （2）!important > 内联 > ID > Class|属性|伪类 > 元素选择器
   （3）:link、:visited、:hover、:active 按照 LVHA（LoVe HAte）顺序定义

  
   ```
   对于组合声明的特殊性值计算可以参考：
   [CSS优先级计算及应用](https://www.jianshu.com/p/1c4e639ff7d5)
   [css优先级计算规则](http://www.cnblogs.com/wangmeijian/p/4207433.html)


5. 关于伪类 LVHA 的解释
   ```
   a 标签有四种状态：链接访问前、链接访问后、鼠标滑过、激活，分别对应四种伪类:link、:visited、:hover、:active；

   （1）当鼠标滑过 a 链接时，满足 :link 和 :hover 两个伪类，要改变 a 标签的颜色，就必须将 :hover 
       伪类在 :link 伪类后面声明；
   （2）当鼠标点击激活 a 链接时，同时满足 :link、:hover、:active 三种状态，要显示 a 标签激活时的
       样式（:active），必须将 :active 声明放到 :link 和 :hover 之后。因此得出 LVHA 这个顺序。

   这个顺序能不能变？可以，但也只有:link和:visited可以交换位置，因为一个链接要么访问过要么没访问过，不可能同时满足，也就不存在覆盖的问题。
   ```

6. CSS3 新增伪类有那些？
   ```
   （1）elem:nth-child(n)        选中父元素下的第 n 个子元素，并且这个子元素的标签名为 elem ， n 可以接受具体的数值，也可以接受函数。

   （2）elem:nth-last-child(n)   作用同上，不过是从后开始查找。

   （3）elem:last-child          选中最后一个子元素。

   （4）elem:only-child          如果 elem 是父元素下唯一的子元素，则选中之。

   （5）elem:nth-of-type(n)      选中父元素下第 n 个 elem 类型元素，n 可以接受具体的数值，也可以接受函数。

   （6）elem:first-of-type       选中父元素下第一个 elem 类型元素。

   （7）elem:last-of-type        选中父元素下最后一个 elem 类型元素。

   （8）elem:only-of-type        如果父元素下的子元素只有一个 elem 类型元素，则选中该元素。

   （9）elem:empty               选中不包含子元素和内容的 elem 类型元素。

   （10）::after		             在元素之前添加内容，也可以用来做清除浮动。
 
   （11）::before		           	 在元素之后添加内容
    
   （12）:enabled  	             控制表单控件的禁用状态。	

   （13）:disabled 		           控制表单控件的禁用状态。

    (14):checked                单选框或复选框被选中。
 
   ```
   详细的资料可以参考：
   [css3新特性总结(伪类)](https://www.cnblogs.com/SKLthegoodman/p/css3.html)
   
  
7. 如何居中 div ？
     * 水平居中：给div设置一个宽度，然后添加margin:0 auto属性
        ```css
          div{
          	 width:200px;
          	 margin:0 auto;
           }
        ```
        
      * 让绝对定位的div居中
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
           	position: relative;	           	/* 相对定位或绝对定位均可 */
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

9. position 的值 relative 和 absolute 定位原点是？
   ```
   absolute
   生成绝对定位的元素，相对于值不为 static 的第一个父元素进行定位，也可以理解为离自己这一级元素最近的一级 position 设置为 absolute 或者 relative 的父元素的左上角为原点的。

   fixed （老IE不支持）
   生成绝对定位的元素，相对于浏览器窗口进行定位。

   relative
   生成相对定位的元素，相对于其元素本身所在正常位置进行定位。

   static
   默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。
   
   inherit
   规定从父元素继承 position 属性的值。
   ```

10. CSS3 有哪些新特性？（未掌握）
    ```
    新增各种CSS选择器	（: not(.input)：所有 class 不是“input”的节点）
    圆角		    （border-radius:8px）
    多列布局	    （multi-column layout）
    阴影和反射	（Shadow\Reflect）
    文字特效		（text-shadow、）
    文字渲染		（Text-decoration）
    线性渐变		（gradient）
    旋转		 	（transform）
    缩放,定位,倾斜,动画,多背景
    例如:transform:\scale(0.85,0.90)\ translate(0px,-30px)\ skew(-9deg,0deg)\Animation:
    ```

11. 请解释一下 CSS3 的 Flexbox（弹性盒布局模型），以及适用场景？（未掌握）
    ```
    一个用于页面布局的全新 CSS3 功能，Flexbox 可以把列表放在同一个方向（从上到下排列，从左到右），并让列表能延伸到占用可用的空间。
    较为复杂的布局还可以通过嵌套一个伸缩容器（flex container）来实现。
    采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。
    它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。
    常规布局是基于块和内联流方向，而 Flex 布局是基于 flex-flow 流可以很方便的用来做局中，能对不同屏幕大小自适应。
    在布局上有了比以前更加灵活的空间。
    ```
    详细资料可以参考：
    [Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
    [Flex 布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)


12. 用纯 CSS 创建一个三角形的原理是什么？
    ```
    把上、左、右三条边隐藏掉（颜色设为 transparent）
    #demo {
    width: 0;
    height: 0;
    border-width: 20px;
    border-style: solid;
    border-color: transparent transparent red transparent;
    }
    ```

13. 一个满屏 品 字布局 如何设计?
    ```
    简单的方式：
      	上面的div宽100%，
      	下面的两个div分别宽50%，
      	然后用float或者inline使其不换行即可
    ```

14. CSS 多列等高如何实现？
    ```
    利用padding-bottom|margin-bottom正负值相抵；
    设置父容器设置超出隐藏（overflow:hidden），这样子父容器的高度就还是它里面的列没有设定 padding-bottom 时的高度，
    当它里面的任 一列高度增加了，则父容器的高度被撑到里面最高那列的高度，
    其他比这列矮的列会用它们的 padding-bottom 补偿这部分高度差。
    ```

    详细资料可以参考：
    [前端应该掌握的CSS实现多列等高布局](https://juejin.im/post/5b0fb34151882515662238fd)\

15. 经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用 hack 的技巧 ？
    ```
    （1） png24 位的图片在 iE6 浏览器上出现背景
    解决方案：做成 PNG8 ，也可以引用一段脚本处理。

    （2） 浏览器默认的 margin 和 padding 不同
    解决方案：加一个全局的 *{ margin:0; padding:0;} 来统一。

    （3） IE6 双边距 bug ：在 IE6 下，如果对元素设置了浮动，同时又设置了 margin-left 或 margin-right，margin 值会加倍。

    #box{ float:left; width:10px; margin:0 0 0 10px;} 

    这种情况之下IE会产生20px的距离
    解决方案：在float的标签样式控制中加入 _display:inline; 将其转化为行内属性。( _ 这个符号只有ie6会识别)

    （4） 渐进识别的方式，从总体中逐渐排除局部。
    首先，巧妙的使用"\9"这一标记，将 IE 游览器从所有情况中分离出来。 
    接着，再次使用 "+" 将 IE8 和 IE7 、IE6 分离开来，这样 IE8 已经独立识别。
    .bb{
       background-color:#f1ee18; /*所有识别*/
       .background-color:#00deff\9; /*IE6、7、8识别*/
       +background-color:#a200ff; /*IE6、7识别*/
       _background-color:#1e0bd1; /*IE6识别*/ 
    } 

    （5） IE下，可以使用获取常规属性的方法来获取自定义属性，也可以使用 getAttribute() 获取自定义属性；Firefox下,只能使用 getAttribute() 获取自定义属性
    解决方法：统一通过 getAttribute() 获取自定义属性。

    （6） IE下，event对象有 x、y 属性，但是没有 pageX、pageY属性; Firefox下，event对象有 pageX、pageY 属性，但是没有 x、y 属性
    解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

    （7） Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示
    解决方法：可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决

    （8） 超链接访问过后 hover 样式就不出现了，被点击访问过的超链接样式不再具有 hover 和 active 了
    解决方法：改变 CSS 属性的排列顺序 L-V-H-A

    （9） 怪异模式问题：漏写 DTD 声明，Firefox 仍然会按照标准模式来解析网页，但在 IE 中会触发怪异模式。为避免怪异模式给我们带来不必要的麻烦，最好养成书写 DTD 声明的好习惯。

    （10） 上下 margin 重合问题：ie 和 ff 都存在，相邻的两个 div 的 margin-left 和 margin-right 不会重合，但是 margin-top 和 margin-bottom 却会发生重合。
    解决方法：养成良好的代码编写习惯，同时采用 margin-top 或者同时采用 margin-bottom 。

    ```

16. li 与 li 之间有看不见的空白间隔是什么原因引起的？有什么解决办法？
    ```
    行框的排列会受到中间空白（回车\空格）等的影响，因为空格也属于字符，这些空白也会被应用样式，占据空间，
    所以会有间隔，把字符大小设为0，就没有空格了。
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

18. absolute 的 containing block (容器块)计算方式跟正常流有什么不同？（未掌握）
    ```
    无论属于哪种，都要先找到其祖先元素中最近的 position 值不为 static 的元素，然后再判断：
    1、若此元素为 inline 元素，则 containing block 为能够包含这个元素生成的第一个和最后一个 inline box 的 padding box (除 margin, border 外的区域) 的最小矩形；
    2、否则,则由这个祖先元素的 padding box 构成。
    如果都找不到，则为 initial containing block。

    补充：
    1. static(默认的)/relative：简单说就是它的父元素的内容框（即去掉padding的部分）
    2. absolute: 向上找最近的定位为absolute/relative的元素
    3. fixed: 它的containing block一律为根元素(html/body)，根元素也是initial containing block
    ```

19. CSS 里的 visibility 属性有个 collapse 属性值是干嘛用的？在不同浏览器下以后什么区别？
    ```
   （1）对于一般的元素，它的表现跟 display:hidden 是一样的。元素是不可见的，相当于 display：hidden；，
       但此时仍占用页面空间。

   （2）但例外的是，如果这个元素是 table 相关的元素，例如 table 行，table group，table列，table column 
       group，它的表现却跟 display: none 一样，也就是说，它们占用的空间也会释放。

    在不同浏览器下的区别：

    在谷歌浏览器里，使用 collapse 值和使用 hidden 值没有什么区别。

    在火狐浏览器、 Opera 和 IE11 里，使用 collapse 值的效果就如它的字面意思：table 的行会消失，它的下面一行会补充它的位置。
    
    ```
    详细资料可以参考：
    [CSS里的visibility属性有个鲜为人知的属性值：collapse](http://www.webhek.com/post/visibility-collapse.html)
