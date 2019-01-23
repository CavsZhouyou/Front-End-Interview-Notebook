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