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

    在 ie8+ 浏览器中使用哪个盒模型可以由 box-sizing ( CSS 新增的属性)控制，默认值为 content-box ，即标准盒模型；如果将 box-sizing 设为 border-box 则用的是 IE 盒模型。如果在 ie6,7,8 中 DOCTYPE 缺失会将盒子模型解释为IE盒子模型。若在页面中声明了 DOCTYPE 类型，所有的浏览器都会把盒模型解释为 W3C 盒模型。
   ```
   
   详细的资料可以参考：
   [CSS盒模型详解](https://juejin.im/post/59ef72f5f265da4320026f76)