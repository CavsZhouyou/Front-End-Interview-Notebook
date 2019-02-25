# JavaScript 知识总结

本部分主要是笔者在学习 JavaScript 相关知识和一些相关面试题所做的笔记，如果出现错误，希望大家指出！

## 知识点总结

1. 介绍 js 的基本数据类型。
   ```
   Undefined、Null、Boolean、Number、String、
   ECMAScript 2015 新增: Symbol (创建后独一无二且不可变的数据类型 )
   ```

2. 介绍 js 有哪些内置对象？
   ```
   全局的对象（ global objects ）或称标准内置对象，不要和 "全局对象（global object）" 混淆。这里说的全局
   的对象是说在全局作用域里的对象。全局作用域中的其他对象可以由用户的脚本创建或由宿主程序提供。

   标准内置对象的分类

   （1）值属性，这些全局属性返回一个简单值，这些值没有自己的属性和方法。
        
       例如 Infinity、NaN、undefined、null 字面量

   （2）函数属性，全局函数可以直接调用，不需要在调用时指定所属对象，执行结束后会将结果直接返回给调用者。

       例如 eval()、parseFloat()、parseInt() 等
    
   （3）基本对象，基本对象是定义或使用其他对象的基础。基本对象包括一般对象、函数对象和错误对象。
        
       例如 Object、Function、Boolean、Symbol、Error 等

   （4）数字和日期对象，用来表示数字、日期和执行数学计算的对象。

       例如 Number、Math、Date 

   （5）字符串，用来表示和操作字符串的对象。
       
       例如 String、RegExp

   （6）可索引的集合对象，这些对象表示按照索引值来排序的数据集合，包括数组和类型数组，以及类数组结构的对象。

       例如 Array

   （7）使用键的集合对象，这些集合对象在存储数据时会使用到键，支持按照插入顺序来迭代元素。
        
       例如 Map、Set、WeakMap、WeakSet
    
   （8）矢量集合，SIMD 矢量集合中的数据会被组织为一个数据序列。
   
       例如 SIMD 等

   （9）结构化数据，这些对象用来表示和操作结构化的缓冲区数据，或使用 JSON （JavaScript Object Notation）编
       码的数据。

       例如 JSON 等

   （10）控制抽象对象

       例如 Promise、Generator 等

   （11）反射

       例如 Reflect、Proxy

   （12）国际化，为了支持多语言处理而加入 ECMAScript 的对象。

       例如 Intl、Intl.Collator 等

   （13）WebAssembly

   （14）其他

        例如 arguments

   ```
   详细资料可以参考：
   [标准内置对象的分类](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects)
   [JS所有内置对象属性和方法汇总](https://segmentfault.com/a/1190000011467723#articleHeader24)

3. 说几条写 JavaScript 的基本规范？
   ```
   （1）一个函数作用域中所有的变量声明尽量提到函数首部，用一个 var 声明，不允许出现两个连续的 var 声明，声明
      时如果没有值，则给该变量为对应类型的初始值。

   （2）代码中出现的地址、时间等字符串时等需要使用常量代替。

   （3）用'===', '!=='代替'==', '!='。

   （4）不要在内置对象的原型上添加方法，如 Array, Date。

   （5）switch 语句必须带有 default 分支。

   （6）for 循环必须使用大括号。

   （7）if 语句必须使用大括号。
   ```

4. JavaScript 原型，原型链？ 有什么特点？
   ```
   当我们调用构造函数创建一个新实例后，在这个实例的内部将包含一个指针，指向构造函数的 prototype 属性，在 ECMA-262 第五版
   中管这个指针叫做 [[Prototype]]（原型）。

   当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么它就会去它的原型对象里找这个属性，这个原型
   对象又会有自己的原型，于是就这样一直找下去，也就是我们平时所说的原型链的概念。

   特点：
   JavaScript 对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改
   原型时，与之相关的对象也会继承这一改变。
   ```
   详细资料可以参考：
   [JavaScript深入理解之原型与原型链](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E5%8E%9F%E5%9E%8B%E4%B8%8E%E5%8E%9F%E5%9E%8B%E9%93%BE.html)
   

5. JavaScript 有几种类型的值？你能画一下他们的内存图吗？
   ```
   栈：原始数据类型（Undefined，Null，Boolean，Number、String）
   堆：引用数据类型（对象、数组和函数）

   两种类型的区别是：存储位置不同。
   原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储。

   引用数据类型存储在堆(heap)中的对象，占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；引用数据
   类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址
   后从堆中获得实体。
   ```
   详细资料可以参考：
   [JavaScript有几种类型的值？](https://blog.csdn.net/lxcao/article/details/52749421)
   [JavaScript有几种类型的值？能否画一下它们的内存图；](https://blog.csdn.net/jiangjuanjaun/article/details/80327342)


6. undefined 与 undeclared 的区别？
   ```
   已在作用域中声明但还没有赋值的变量，是 undefined 的。相反，还没有在作用域中声明过的变量，是 undeclared 的。

   对于 undeclared 变量的引用，浏览器会报引用错误，如 ReferenceError: b is not defined 。

   但是我们可以使用 typeof 的安全防范机制来避免报错，因为 对于undeclared（或者not defined）变量，typeof 
   会返回 "undefined"。
   ```

7. 在 js 中不同进制数字的表示方式
   ```
   （1）以 0X、0x 开头的表示为十六进制。

   （2）以 0、0O、0o 开头的表示为八进制。

   （3）以 0B、0b 开头的表示为二进制格式。
   ```

8. js 中整数的安全范围是多少？
   ```
   能够被“安全”呈现的最大整数是2^53 - 1，即9007199254740991，在ES6 中被定义为 Number.MAX_SAFE_INTEGER。最小整数是-9007199254740991，在 ES6 中被定义为 Number.MIN_SAFE_INTEGER。
   ```

9. 如何获取安全的 undefined 值？
    ```
    因为 undefined 是一个标识符，所以可以被当作变量来使用和赋值，但是这样会影响 undefined 的正常判断。

    表达式void ___ 没有返回值，因此返回结果是 undefined。void 并不改变表达式的结果，只是让表达式不返回值。

    按惯例我们用 void 0 来获得 undefined。
    ```

10. typeof NaN 的结果是什么？
    ```
    NaN 意指“不是一个数字”（not a number），NaN 是一个“警戒值”（sentinel value，有特殊用途的常规值），
    用于指出数字类型中的错误情况，即“执行数学运算没有成功，这是失败后返回的结果”。

    typeof NaN; // "number"

    NaN 是一个特殊值，它和自身不相等，是唯一一个非自反（自反，reflexive，即x === x 不成立）的值。而
    NaN != NaN 为 true。
    ```

11. isNaN 和 Number.isNaN 函数的区别？
    ```
    函数 isNaN 检查参数是不是 NaN 或者 不是数字的情况，因此非数字值传入也会返回 true ，会影响 NaN 的判断。

    函数 Number.isNaN 会首先判断传入参数是否为数字，如果是数字再继续判断是否为 NaN 。
    ```

12. 内部属性 [[Class]] 是什么？
    ```
    所有 typeof 返回值为 "object" 的对象（如数组）都包含一个内部属性 [[Class]]（我们可以把它看作一个内部
    的分类，而非传统的面向对象意义上的类）。这个属性无法直接访问， 一般通过 Object.prototype.toString(..) 
    来查看。例如：

    Object.prototype.toString.call( [1,2,3] );
    // "[object Array]"

    Object.prototype.toString.call( /regex-literal/i );
    // "[object RegExp]"
    ```

13. Array 构造函数只有一个参数值时的表现？
    ```
    Array 构造函数只带一个数字参数的时候，该参数会被作为数组的预设长度（length），而非只充当数组中的
    一个元素。这样创建出来的只是一个空数组，只不过它的 length 属性被设置成了指定的值。

    构造函数 Array(..) 不要求必须带 new 关键字。不带时，它会被自动补上。
    ```

14. 非字符串到字符串的转换规则？
    ```
    规范的 9.8 节中定义了抽象操作 ToString ，它负责处理非字符串到字符串的强制类型转换。

    基本类型值的字符串化规则为：null 转换为 "null"，undefined 转换为 "undefined"，true 转换为 "true"。
    数字的字符串化则遵循通用规则，不过那些极小和极大的数字会使用指数形式。

    对普通对象来说，除非自行定义，否则 toString()（Object.prototype.toString()）返回内部属性 [[Class]] 
    的值，如"[object Object]"。如果对象有自己的 toString() 方法，字符串化时就会调用该方法并使用其返回值。

    ```

15. 非数字值到数字值的转换规则？
    
    ```
    有时我们需要将非数字值当作数字来使用，比如数学运算。为此 ES5 规范在 9.3 节定义了抽象操作 ToNumber。

    其中 true 转换为1，false 转换为0。undefined 转换为 NaN，null 转换为0。

    ToNumber 对字符串的处理基本遵循数字常量的相关规则/语法（空字符串为0，含有除表示数字字符以外的字符为 NaN），
    处理失败时返回 NaN。不同之处是 ToNumber 对以 0 开头的十六进制数并不按十六进制处理，而是按十进制。

    对象（包括数组）会首先被转换为相应的基本类型值，如果返回的是非数字的基本类型值，则再遵循以上规则将其强制转
    换为数字。

    为了将值转换为相应的基本类型值，抽象操作 ToPrimitive 会首先（通过内部操作 DefaultValue）检查该值是否有
    valueOf() 方法。如果有并且返回基本类型值，就使用该值进行强制类型转换。如果没有就使用 toString() 的返回
    值（如果存在）来进行强制类型转换。

    如果 valueOf() 和toString() 均不返回基本类型值，会产生TypeError 错误。
    ```
16. {} 和 [] 的 valueOf 和 toString 的结果是什么？
    ```
    {} 的 valueOf 结果为 {} ，toString 的结果为 "[object Object]"

    [] 的 valueOf 结果为 [] ，toString 的结果为 ""
    ```

17. 其他值到布尔类型的值的转换规则？
    ```
    ES5 规范 9.2 节中定义了抽象操作 ToBoolean，列举了布尔强制类型转换所有可能出现的结果。

    以下这些是假值：
        • undefined
        • null
        • false
        • +0、-0 和NaN
        • ""

    假值的布尔强制类型转换结果为 false。从逻辑上说，假值列表以外的都应该是真值。
    ```

18. 什么是假值对象？
    ```
    浏览器在某些特定情况下，在常规 JavaScript 语法基础上自己创建了一些外来值，这些就是“假值对象”。假值对象
    看起来和普通对象并无二致（都有属性，等等），但将它们强制类型转换为布尔值时结果为 false 最常见的例子是document.all，
    它是一个类数组对象，包含了页面上的所有元素，由 DOM（而不是JavaScript 引擎）提供给 JavaScript 程序使用。
    ```

19. ~ 操作符的作用？
    ```
    ~ 返回 2 的补码。

    ~x 大致等同于-(x+1)。
    ```

20. 解析字符串中的数字和将字符串强制类型转换为数字的返回结果都是数字，它们之间的区别是什么？
    ```
    解析允许字符串（如 parseInt() ）中含有非数字字符，解析按从左到右的顺序，如果遇到非数字字符就停止。而
    转换（如 Number ()）不允许出现非数字字符，否则会失败并返回 NaN。
    ```

21. `+` 操作符什么时候用于字符串的拼接？
    ```
    根据 ES5 规范 11.6.1 节，如果某个操作数是字符串或者能够通过以下步骤转换为字符串的话，+ 将进行拼接操作。
    如果其中一个操作数是对象（包括数组），则首先对其调用 ToPrimitive 抽象操作，该抽象操作再调用[[DefaultValue]]，以数字作为上下文。

    简单来说就是，如果 + 的其中一个操作数是字符串（或者通过以上步骤最终得到字符串），则执行字符串拼接；否则执
    行数字加法。
    ```

22. 什么情况下会发生布尔值的隐式强制类型转换？
    ```
    （1） if (..) 语句中的条件判断表达式。
    （2） for ( .. ; .. ; .. ) 语句中的条件判断表达式（第二个）。
    （3） while (..) 和 do..while(..) 循环中的条件判断表达式。
    （4） ? : 中的条件判断表达式。
    （5） 逻辑运算符 ||（逻辑或）和 &&（逻辑与）左边的操作数（作为条件判断表达式）。
    ```

23. || 和 && 操作符的返回值？
    ```
    || 和 && 首先会对第一个操作数执行条件判断，如果其不是布尔值就先进行 ToBoolean 强制类型转换，然后再
    执行条件判断。

    对于 || 来说，如果条件判断结果为 true 就返回第一个操作数的值，如果为 false 就返回第二个操作数的值。

    && 则相反，如果条件判断结果为 true 就返回第二个操作数的值，如果为 false 就返回第一个操作数的值。

    || 和 && 返回它们其中一个操作数的值，而非条件判断的结果 
    ```

24. Symbol 值的强制类型转换？
    ```
    ES6 允许从符号到字符串的显式强制类型转换，然而隐式强制类型转换会产生错误。

    Symbol 值不能够被强制类型转换为数字（显式和隐式都会产生错误），但可以被强制类型转换为布尔值
    （显式和隐式结果都是 true ）。
    ```

25. == 操作符的强制类型转换规则？
    ```
    （1）字符串和数字之间的相等比较，将字符串转换为数字之后再进行比较。

    （2）其他类型和布尔类型之间的相等比较，先将布尔值转换为数字后，在应用其他规则进行比较。

    （3）null 和 undefined 之间的相等比较，结果为真。其他值和它们进行比较都返回假值。

    （4）对象和非对象之间的相等比较，对象先调用 ToPromitive 抽象操作后，再进行比较。
    
    （5）如果一个操作值为 NaN ，则相等比较返回 false（ NaN 本身也不等于 NaN ）。

    （6）如果两个操作值都是对象，则比较它们是不是指向同一个对象。如果两个操作数都指向同一个对象，则相等操作
        符返回 true，否则，返回 false。
    ```
   详细资料可以参考：
   [JavaScript字符串间的比较](https://www.jeffjade.com/2015/08/28/2015-09-02-js-string-compare/)

26. 如何将字符串转化为数字，例如 '12.3b'?
    ```
    （1） 使用 Number() 方法，前提是所包含的字符串不包含不合法字符。

    （2） 使用 parseInt() 方法，parseInt() 函数可解析一个字符串，并返回一个整数。还可以设置要解析的数
         字的基数。当基数的值为 0，或没有设置该参数时，parseInt() 会根据 string 来判断数字的基数。

    （3）使用 parseFloat() 方法，该函数解析一个字符串参数并返回一个浮点数。

    （4）使用 + 操作符的隐式转换。
    ```
    详细资料可以参考：
    [详解JS中Number()、parseInt()和parseFloat()的区别](https://blog.csdn.net/m0_38099607/article/details/72638678)


27. 如何将浮点数点左边的数每三位添加一个逗号，如12000000.11转化为『12,000,000.11』?
    ```
    function format(number){
         return number && number.replace(/(?!^)(?=(\d{3})+\.)/g,",")
    }
    ```
28. 生成随机数的各种方法？
    [JS - 生成随机数的方法汇总（不同范围、类型的随机数）](http://www.hangge.com/blog/cache/detail_1872.html)

29. 如何实现数组的随机排序？
    ```
    （1）使用数组 sort 方法对数组元素随机排序，让 Math.random() 出来的数与 0.5 比较，如果大于就返回 1 
        不交换位置，如果小于就返回 -1，交换位置。

        function randomSort(a, b) { 
          return Math.random() > 0.5 ? -1 : 1; 
        }
        
        缺点：每个元素被派到新数组的位置不是随机的，原因是 sort() 方法是依次比较的。

    
    （2）随机从原数组抽取一个元素，加入到新数组

        function randomSort(arr) {
            var result = [];

            while (arr.length > 0) {
                var randomIndex = Math.floor(Math.random() * arr.length);
                result.push(arr[randomIndex]);
                arr.splice(randomIndex, 1);
            }

            return result;
        }

     （3）随机交换数组内的元素（洗牌算法类似）

         function randomSort(arr) {
          var index,
            randomIndex,
            temp,
            len = arr.length;

          for (index = 0; index < len; index++) {
            randomIndex = Math.floor(Math.random() * (len - index)) + index;

            temp = arr[index];
            arr[index] = arr[randomIndex];
            arr[randomIndex] = temp;
          }

          return arr;
        }

    ```
    详细资料可以参考：
    [Fisher and Yates 的原始版](https://gaohaoyang.github.io/2016/10/16/shuffle-algorithm/#top)
    [javascript实现数组随机排序?](https://www.zhihu.com/question/32303195)
    [JavaScript学习笔记：数组随机排序](https://www.w3cplus.com/javascript/how-to-randomize-shuffle-a-javascript-array.html)

30. javascript 创建对象的几种方式？
    [JavaScript深入理解之对象创建](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E5%AF%B9%E8%B1%A1%E5%88%9B%E5%BB%BA.html)

31. JavaScript 继承的几种实现方式？
    [JavaScript深入理解之继承](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E7%BB%A7%E6%89%BF.html)

32. Javascript 的作用域链?
    [JavaScript深入理解之作用域链](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E4%BD%9C%E7%94%A8%E5%9F%9F%E9%93%BE.html)

33. 谈谈 This 对象的理解。
    [JavaScript深入理解之this详解](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8Bthis%E8%AF%A6%E8%A7%A3.html)

34. eval 是做什么的？
    ```
    它的功能是把对应的字符串解析成 JS 代码并运行。

    应该避免使用 eval，不安全，非常耗性能（2次，一次解析成 js 语句，一次执行）。
    ``` 
    详细资料可以参考：
    [eval()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/eval)

35. 什么是 window 对象? 什么是 document 对象?
    ```
    Window 对象表示浏览器中打开的窗口。如果文档包含框架（frame 或 iframe 标签），浏览器会为 HTML 文档
    创建一个 window 对象，并为每个框架创建一个额外的 window 对象。

    每个载入浏览器的 HTML 文档都会成为 Document 对象。Document 对象使我们可以从脚本中对 HTML 页面中的
    所有元素进行访问。Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。
    ```
    详细资料可以参考：
    [DOM, DOCUMENT, BOM, WINDOW 有什么区别?](https://www.zhihu.com/question/33453164)
    [Window 对象](http://www.w3school.com.cn/jsref/dom_obj_window.asp)

36. null，undefined 的区别？
    [JavaScript深入理解之undefined与null](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8Bundefined%E4%B8%8Enull.html)



37. 写一个通用的事件侦听器函数。
    ```
    const EventUtils = {
     		// 页面加载完成后
     		readyEvent : function(fn) {
     			if (fn==null) {
     				fn=document;
     			}
     			var oldonload = window.onload;
     			if (typeof window.onload != 'function') {
     				window.onload = fn;
     			} else {
     				window.onload = function() {
     					oldonload();
     					fn();
     				};
     			}
     		},
     		// 视能力分别使用dom0||dom2||IE方式 来绑定事件
     		// 参数： 操作的元素,事件名称 ,事件处理程序
     		addEvent : function(element, type, handler) {
     			if (element.addEventListener) {
     				//事件类型、需要执行的函数、是否捕捉
     				element.addEventListener(type, handler, false);
     			} else if (element.attachEvent) {
     				element.attachEvent('on' + type, function() {
     					handler.call(element);
     				});
     			} else {
     				element['on' + type] = handler;
     			}
     		},
     		// 移除事件
     		removeEvent : function(element, type, handler) {
     			if (element.removeEventListener) {
     				element.removeEventListener(type, handler, false);
     			} else if (element.datachEvent) {
     				element.detachEvent('on' + type, handler);
     			} else {
     				element['on' + type] = null;
     			}
     		},
     		// 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)
     		stopPropagation : function(ev) {
     			if (ev.stopPropagation) {
     				ev.stopPropagation();
     			} else {
     				ev.cancelBubble = true;
     			}
     		},
     		// 取消事件的默认行为
     		preventDefault : function(event) {
     			if (event.preventDefault) {
     				event.preventDefault();
     			} else {
     				event.returnValue = false;
     			}
     		},
     		// 获取事件目标
     		getTarget : function(event) {
     			return event.target || event.srcElement;
     		},
     		// 获取event对象的引用，取到事件的所有信息，确保随时能使用event；
     		getEvent : function(e) {
     			var ev = e || window.event;
     			if (!ev) {
     				var c = this.getEvent.caller;
     				while (c) {
     					ev = c.arguments[0];
     					if (ev && Event == ev.constructor) {
     						break;
     					}
     					c = c.caller;
     				}
     			}
     			return ev;
     		}
     	};
    ```
    详细资料可以参考：
    [JS事件模型](https://segmentfault.com/a/1190000006934031#articleHeader6)
  
38. 事件是什么？IE 与火狐的事件机制有什么区别？ 如何阻止冒泡？

    ```
    （1）事件是用户操作网页时发生的交互动作，比如 click/move, 事件除了用户触发的动作外，还可以是文档加载，
        窗口滚动和大小调整。事件被封装成一个 event 对象，包含了该事件发生时的所有相关信息（ event 的属性）
        以及可以对事件进行的操作（event的方法）。
    
    （2）事件处理机制：IE 支持事件冒泡、Firefox 同时支持两种事件模型，也就是：事件冒泡和事件捕获。

    （3） event.stopPropagation() 或者 ie 下的方法 event.cancelBubble = true;
    ```
    详细资料可以参考：
    [Javascript事件模型系列（一）事件及事件的三种模型](https://www.cnblogs.com/lvdabao/p/3265870.html)
    [Javascript事件模型：事件捕获和事件冒泡](https://blog.csdn.net/wuseyukui/article/details/13771493)

39. 我们给一个 dom 同时绑定两个点击事件，一个用捕获，一个用冒泡。会执行几次事件，会先执行冒泡还是捕获？
    详细资料可以参考：
    [一个DOM元素绑定多个事件时，先执行冒泡还是捕获](https://blog.csdn.net/u013217071/article/details/77613706)


40. ["1", "2", "3"].map(parseInt) 答案是多少？
    ```
    parseInt() 函数能解析一个字符串，并返回一个整数，需要两个参数 (val, radix)，其中 radix 表示要解析
    的数字的基数。（该值介于 2 ~ 36 之间，并且字符串中的数字不能大于 radix 才能正确返回数字结果值）。


    此处 map 传了 3 个 参数(element, index, array)，默认第三个参数被忽略掉，因此三次传入的参数分别为

    "1-0", "2-1", "3-2"

    因为字符串的值不能大于基数，因此后面两次调用均失败，返回 NaN ，第一次基数为 0 ，按十进制解析返回1。

    ```
    详细资料可以参考：
    [为什么 ["1", "2", "3"].map(parseInt) 返回 [1,NaN,NaN]？](https://blog.csdn.net/justjavac/article/details/19473199)

41. 什么是 闭包（closure），为什么要用它？
    ```
    闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，
    通过另一个函数访问这个函数的局部变量,利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。

    ```
    详细资料可以参考：
    [JavaScript深入理解之闭包](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E9%97%AD%E5%8C%85.html)


42. javascript 代码中的 "use strict"; 是什么意思 ? 使用它区别是什么？
    ```
    use strict是一种 ECMAscript 5 添加的（严格）运行模式，这种模式使得 Javascript 在更严格的条件下运行。
    

    设立"严格模式"的目的，主要有以下几个：

        - 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为;

        - 消除代码运行的一些不安全之处，保证代码运行的安全；

        - 提高编译器效率，增加运行速度；

        - 为未来新版本的Javascript做好铺垫。

    区别：

    （1）禁止使用 with 语句。
    （2）禁止 this 关键字指向全局对象。
    （3）对象不能有重名的属性。

     ......
    ```
    详细资料可以参考：
    [Javascript 严格模式详解](http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html)


43. 如何判断一个对象是否属于某个类？
    ```
    instanceof 运算符用于测试构造函数的 prototype 属性是否出现在对象的原型链中的任何位置。
    ```
    详细资料可以参考：
    [instanceof](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/instanceof)
    [js 判断一个对象是否属于某一类](https://blog.csdn.net/haitunmin/article/details/78418522)

44. new 操作符具体干了什么呢？如何实现？
    ```
    （1）首先创建了一个空对象
    （2）设置原型，将对象的原型设置为函数的 prototype 对象。
    （3）让函数的 this 指向这个对象，执行构造函数的代码（为这个新对象添加属性）
    （4）判断函数的返回值类型，如果是值类型，返回创建的对象。如果是引用类型，就返回这个引用类型的对象。
    
    实现:

    function create() {
      let obj = {}
      let Con = [].shift.call(arguments)
      obj.__proto__ = Con.prototype
      let result = Con.apply(obj, arguments)
      return result instanceof Object ? result : obj
    }
    ```
    详细资料可以参考：
    [new 操作符具体干了什么？](https://segmentfault.com/a/1190000008576048)
    [JavaScript深入之new的模拟实现](https://github.com/mqyqingfeng/Blog/issues/13)


45. Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？
    ```
    hasOwnProperty

    所有继承了 Object 的对象都会继承到 hasOwnProperty 方法。这个方法可以用来检测一个对象是否含有特定
    的自身属性；和 in 运算符不同，该方法会忽略掉那些从原型链上继承到的属性。
    ```
    详细资料可以参考：
    [Object.prototype.hasOwnProperty()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)

46. 对于 JSON 的了解？
    ```
    JSON 是一种数据交换格式，基于文本，优于轻量，用于交换数据。

    JSON 可以表示数字、布尔值、字符串、null、数组（值的有序序列），以及由这些值（或数组、对象）所组成的
    对象（字符串与值的映射）。

    JSON 使用 JavaScript 语法，但是 JSON 格式仅仅是一个文本。文本可以被任何编程语言读取及作为数据格式传递。
    ```
    详细资料可以参考：
    [深入了解JavaScript中的JSON ](https://my.oschina.net/u/3284240/blog/874368)


47. [].forEach.call($$("*"),function(a){a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16)}) 能解释一下这段代码的意思吗？
    ```
    （1）选取页面所有 DOM 元素。

    （2）循环遍历 DOM 元素

    （3）给元素添加 outline 。

    （4）生成随机颜色函数。
    ```
    详细资料可以参考：
    [通过一行代码学JavaScript](https://2008winstar.iteye.com/blog/2128290)
  
48. js 延迟加载的方式有哪些？
    ```
    JS 延迟加载，也就是等页面加载完成之后再加载 JavaScript 文件。 JS 延迟加载有助于提高页面加载速度。

    一般有以下几种方式：

        defer 属性
        async 属性
        动态创建 DOM 方式
        使用 setTimeout 延迟方法
        让 JS 最后加载
    ```
    详细资料可以参考：
    [JS延迟加载的几种方式](https://blog.csdn.net/meijory/article/details/76389762)
    [HTML 5 <script> async 属性](http://www.w3school.com.cn/html5/att_script_async.asp)


49. Ajax 是什么? 如何创建一个Ajax？
    ```
    2005年2月，AJAX 这个词第一次正式提出，它是 Asynchronous JavaScript and XML 的缩写，指的是通过
    JavaScript 的异步通信，从服务器获取 XML 文档从中提取数据，再更新当前网页的对应部分，而不用刷新整个网页。

    具体来说，AJAX 包括以下几个步骤。

    (1)创建 XMLHttpRequest 对象,也就是创建一个异步调用对象
    (2)创建一个新的 HTTP 请求,并指定该 HTTP 请求的方法、URL 及验证信息
    (3)设置响应 HTTP 请求状态变化的函数
    (4)发送 HTTP 请求
    (5)获取异步调用返回的数据
    (6)使用 JavaScript 和 DOM 实现局部刷新
    ```
    详细资料可以参考：
    [XMLHttpRequest 对象](https://wangdoc.com/javascript/bom/xmlhttprequest.html)

50. Ajax 解决浏览器缓存问题？
    ```
    1、在 ajax 发送请求前加上 anyAjaxObj.setRequestHeader("If-Modified-Since","0")。 

    2、在 ajax 发送请求前加上 anyAjaxObj.setRequestHeader("Cache-Control","no-cache")。 

    3、在 URL 后面加上一个随机数： "fresh=" + Math.random();。 

    4、在 URL 后面加上时间戳："nowtime=" + new Date().getTime();。 

    5、如果是使用 jQuery，直接这样就可以了$.ajaxSetup({cache:false})。这样页面的所有 ajax 都会执行这
       条语句就是不需要保存缓存记录。
    ```
    详细资料可以参考：
    [Ajax中浏览器的缓存问题解决方法](https://www.cnblogs.com/cwzqianduan/p/8632009.html)
    [浅谈浏览器缓存](https://segmentfault.com/a/1190000012573337)

51. 同步和异步的区别？
    ```
    同步，可以理解为在执行完一个函数或方法之后，一直等待系统返回值或消息，这时程序是处于阻塞的，只有接收到返
    回的值或消息后才往下执行其他的命令。  

    异步，执行完函数或方法后，不必阻塞性地等待返回值或消息，只需要向系统委托一个异步过程，那么当系统接收到返
    回值或消息时，系统会自动触发委托的异步过程，从而完成一个完整的流程。 
    ```
    详细资料可以参考：
    [同步和异步的区别](https://blog.csdn.net/tennysonsky/article/details/45111623)

52. 如何解决跨域问题？
    ```
    （1） 通过 jsonp 跨域
    （2） document.domain + iframe 跨域
    （3） location.hash + iframe
    （4） window.name + iframe 跨域
    （5） postMessage 跨域
    （6） 跨域资源共享（CORS）
    （7） nginx 代理跨域
    （8） nodejs 中间件代理跨域
    （9） WebSocket 协议跨域
    ```
    详细资料可以参考：
    [前端常见跨域解决方案（全）](https://segmentfault.com/a/1190000011145364)
    [浏览器同源政策及其规避方法](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html)
    [跨域，你需要知道的全在这里](https://juejin.im/entry/59feae9df265da43094488f6)
    [为什么form表单提交没有跨域问题，但ajax提交有跨域问题？](https://www.zhihu.com/question/31592553)


53. 服务器代理转发时，该如何处理 cookie？
    详细资料可以参考：
    [深入浅出Nginx](https://www.jianshu.com/p/5eab0f83e3b4)
    [HTTP cookies](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Cookies)
    [聊一聊 cookie](https://segmentfault.com/a/1190000004556040)

54. 模块化开发怎么做？
    ```
    把函数作为模块 缺陷: 污染全局变量 模块成员之间没什么关系 面向对象思想 并使用立即执行函数 实现闭包 避免
    了变量污染 同时同一模块内的成员也有了关系 在模块外部无法修改我们没有暴露出来的变量、函数 这就是简单的模
    块。
    ```
    详细资料可以参考：
    [浅谈模块化开发](https://juejin.im/post/5ab378c46fb9a028ce7b824f)
    [Javascript模块化编程（一）：模块的写法](http://www.ruanyifeng.com/blog/2012/10/javascript_module.html)
    [前端模块化：CommonJS,AMD,CMD,ES6](https://juejin.im/post/5aaa37c8f265da23945f365c)
    [Module 的语法](http://es6.ruanyifeng.com/#docs/module)

55. AMD 和 CMD 规范的区别？
    ```
    Asynchronous Module Definition，异步模块定义，所有的模块将被异步加载，模块加载不影响后面语句运行。
    所有依赖某些模块的语句均放置在回调函数中。

    区别：

     1. 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行
     （根据写法不同，处理方式不同）。CMD 推崇 as lazy as possible.
     1. CMD 推崇依赖就近，AMD 推崇依赖前置。看代码：

    // CMD
    define(function(require, exports, module) {
     var a = require('./a')
     a.doSomething()
     // 此处略去 100 行
     var b = require('./b') // 依赖可以就近书写
     b.doSomething()
     // ...
    })

    // AMD 默认推荐
    define(['./a', './b'], function(a, b) { // 依赖必须一开始就写好
     a.doSomething()
     // 此处略去 100 行
     b.doSomething()
     // ...
    })
    ```
    详细资料可以参考：
    [前端模块化，AMD与CMD的区别](https://juejin.im/post/5a422b036fb9a045211ef789)

56. requireJS 的核心原理是什么？（如何动态加载的？如何避免多次加载的？如何 缓存的？）
    详细资料可以参考：
    [requirejs的用法和原理分析](https://github.com/HRFE/blog/issues/10)
    [requireJS 的核心原理是什么？](https://zhuanlan.zhihu.com/p/55039478)
    [从 RequireJs 源码剖析脚本加载原理](https://www.cnblogs.com/dong-xu/p/7160919.html)
    [requireJs原理分析](https://www.jianshu.com/p/5a39535909e4)


57. JS 模块加载器的轮子怎么造，也就是如何实现一个模块加载器？
    详细资料可以参考：
    [JS模块加载器加载原理是怎么样的？](https://www.zhihu.com/question/21157540)

58. ECMAScript6 怎么写 class，为什么会出现 class 这种东西?
    详细资料可以参考：
    [ECMAScript 6实现了class，对JavaScript前端开发有什么意义？](https://www.zhihu.com/question/29789315)
    [Class 的基本语法](http://es6.ruanyifeng.com/#docs/class)

59. documen.write和 innerHTML 的区别？
    ```
     document.write 只能重绘整个页面

    innerHTML 可以重绘页面的一部分
    ```
    详细资料可以参考：
    [简述document.write和 innerHTML的区别。](https://www.nowcoder.com/questionTerminal/2c5d8105b2694d85b06eff85e871cf50)

60. DOM 操作——怎样添加、移除、移动、复制、创建和查找节点？
    ```
    （1）创建新节点
    createDocumentFragment()    //创建一个DOM片段
    createElement()   //创建一个具体的元素
    createTextNode()   //创建一个文本节点
    （2）添加、移除、替换、插入
    appendChild()
    removeChild()
    replaceChild()
    insertBefore() //在已有的子节点前插入一个新的子节点
    （3）查找
    getElementsByTagName()    //通过标签名称
    getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，会得到一个数组，其中包括id等于name值的)
    getElementById()    //通过元素Id，唯一性
    ```
    详细资料可以参考：
    [DOM概述](https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model/Introduction#DOM_interfaces)
    [原生 JavaScript 的 DOM 操作汇总](https://harttle.land/2015/10/01/javascript-dom-api.html)
    [原生JS中DOM节点相关API合集](https://microzz.com/2017/04/06/jsdom/)

61. .call() 和 .apply() 的区别？
    ```
    它们的作用一模一样，区别仅在于传入参数的形式的不同。

    apply 接受两个参数，第一个参数指定了函数体内 this 对象的指向，第二个参数为一个带下标的集合,这个集合可以
    为数组，也可以为类数组，apply 方法把这个集合中的元素作为参数传递给被调用的函数。

    call 传入的参数数量不固定，跟 apply 相同的是，第一个参数也是代表函数体内的 this 指向， 从第二个参数开、
    始往后，每个参数被依次传入函数。
    ``` 
    详细资料可以参考：
    [apply、call 的区别和用途](https://juejin.im/entry/58d0a7b22f301e007e5a15ae)

62. 数组和对象有哪些原生方法，列举一下？
    详细资料可以参考：
    [JavaScript深入理解之Array类型详解](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8BArray%E8%AF%A6%E8%A7%A3.html)

63. JavaScript 中的作用域与变量声明提升？
    详细资料可以参考：
    [JavaScript深入理解之变量对象](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E5%8F%98%E9%87%8F%E5%AF%B9%E8%B1%A1.html)

64. 如何编写高性能的 Javascript ？
    详细资料可以参考：
    [如何编写高性能的Javascript？](https://zhuanlan.zhihu.com/p/34780474)

65. 那些操作会造成内存泄漏？
    ```
    （1）意外的全局变量
    （2）被遗忘的计时器或回调函数
    （3）脱离 DOM 的引用
    （4）闭包
    ```
    详细资料可以参考：
    [JavaScript 内存泄漏教程](http://www.ruanyifeng.com/blog/2017/04/memory-leak.html)
    [4类 JavaScript 内存泄漏及如何避免](https://jinlong.github.io/2016/05/01/4-Types-of-Memory-Leaks-in-JavaScript-and-How-to-Get-Rid-Of-Them/)
    [杜绝js中四种内存泄漏类型的发生](https://juejin.im/entry/5a64366c6fb9a01c9332c706)
    [深入理解V8的垃圾回收原理](https://www.jianshu.com/p/b8ed21e8a4fb)
    [javascript典型内存泄漏及chrome的排查方法](https://segmentfault.com/a/1190000008901861)
    [JavaScript 中的垃圾回收](https://zhuanlan.zhihu.com/p/23992332)


66. 需求：实现一个页面操作不会整页刷新的网站，并且能在浏览器前进、后退时正确响应。给出你的技术实现方案？
    ```
    pushState + ajax 实现浏览器无刷新前进后退
    ```
    详细资料可以参考：
    [pushState + ajax 实现浏览器无刷新前进后退](http://blog.chenxu.me/post/detail?id=ed4f0732-897f-48e4-9d4f-821e82f17fad)
    [Manipulating the browser history](https://developer.mozilla.org/zh-CN/docs/Web/API/History_API)

67. 如何判断当前脚本运行在浏览器还是node环境中？（阿里）
    ```
    this === window ? 'browser' : 'node';

    通过判断 Global 对象是否为 window，如果不为 window，当前脚本没有运行在浏览器中
    ``` 

68. 把 Script 标签 放在页面的最底部的body封闭之前 和封闭之后有什么区别？浏览器会如何解析它们？
    详细资料可以参考：
    [为什么把 Script 标签放在 body 结束标签之后 html 结束标签之前？](https://www.zhihu.com/question/20027966)
    [从Chrome源码看浏览器如何加载资源](https://zhuanlan.zhihu.com/p/30558018)


69. 移动端的点击事件的有延迟，时间是多久，为什么会有？ 怎么解决这个延时？（click 有 300ms 延迟,为了实现
    safari 的双击事件的设计，浏览器要知道你是不是要双击操作。）
    详细资料可以参考：
    [移动端300ms点击延迟和点击穿透](https://juejin.im/post/5b3cc9836fb9a04f9a5cb0e0)

70. 什么是“前端路由”?什么时候适合使用“前端路由”? “前端路由”有哪些优点和缺点？
    ```
    （1）什么是前端路由？

        路由是根据不同的 url 地址展示不同的内容或页面
        前端路由就是把不同路由对应不同的内容或页面的任务交给前端来做，之前是通过服务端根据 url 的不同返回
        不同的页面实现的。

    （2）什么时候使用前端路由？

        在单页面应用，大部分页面结构不变，只改变部分内容的使用

    （3）前端路由有什么优点和缺点？

        优点
        用户体验好，不需要每次都从服务器全部获取，快速展现给用户

        缺点
        单页面无法记住之前滚动的位置，无法在前进，后退的时候记住滚动的位置
    ```
    详细资料可以参考：
    [什么是“前端路由”](https://segmentfault.com/q/1010000005336260)
    [浅谈前端路由 ](https://github.com/kaola-fed/blog/issues/137)
    [前端路由是什么东西？](https://www.zhihu.com/question/53064386)

71. 如何测试前端代码么？ 知道BDD, TDD, Unit Test么? 知道怎么测试你的前端工程么(mocha, sinon, 
    jasmin, qUnit..)？
    详细资料可以参考：
    [浅谈前端单元测试](https://juejin.im/post/5b2da89cf265da597f1c7cab)

72. 检测浏览器版本版本有哪些方式？
    ```
    功能检测、userAgent特征检测
    ```
    详细资料可以参考：
    [JavaScript判断浏览器类型](https://www.jianshu.com/p/d99f4ca385ac)

73. 什么是 Polyfill ？
    ```
    Polyfill的准确意思为：用于实现浏览器并不支持的原生 API 的代码。
    ```
    详细资料可以参考：
    [Web开发中的“黑话”](https://segmentfault.com/a/1190000002593432)
    [polyfill为何物](https://juejin.im/post/5a579bc7f265da3e38496ba1)

74. 使用 JS 实现获取文件扩展名？
    ```
      function getFileExtension(filename) {
        return filename.slice((filename.lastIndexOf(".") - 1 >>> 0) + 2);
      }

      String.lastIndexOf() 方法返回指定值（本例中的'.'）在调用该方法的字符串中最后出现的位置，如果没找到
      则返回 -1。
      对于'filename'和'.hiddenfile'，lastIndexOf 的返回值分别为0和-1无符号右移操作符(»>) 将-1转换为4294967295，将-2转换为4294967294，这个方法可以保证边缘情况时文件名不变。
      String.prototype.slice() 从上面计算的索引处提取文件的扩展名。如果索引比文件名的长度大，结果为""。
    ```
    详细资料可以参考：
    [如何更有效的获取文件扩展名](https://segmentfault.com/a/1190000004993946)

75. 介绍一下 js 的节流与防抖？
    ```
    函数防抖： 在事件被触发 n 秒后再执行回调，如果在这 n 秒内又被触发，则重新计时。

    函数节流： 规定一个单位时间，在这个单位时间内，只能有一次触发事件的回调函数执行，如果在同一个单位时间
             内某事件被触发多次，只有一次能生效。
    ```
    详细资料可以参考：
    [轻松理解JS函数节流和函数防抖](https://juejin.im/post/5a35ed25f265da431d3cc1b1)
    [JavaScript 事件节流和事件防抖](https://juejin.im/post/5aa60b0e518825556b6c6d1a)
    [JS的防抖与节流](https://juejin.im/entry/5b1d2d54f265da6e2545bfa4)
    

76. Object.is() 与原来的比较操作符“ ===”、“ ==”的区别？
    ```
    两等号判等，会在比较时进行类型转换；
    三等号判等(判断严格)，比较时不进行隐式类型转换,（类型不同则会返回false）；

    Object.is 在三等号判等的基础上特别处理了 NaN 、-0 和 +0 ，保证 -0 和 +0 不再相同，
    但 Object.is(NaN, NaN) 会返回 true.

    Object.is 应被认为有其特殊的用途，而不能用它认为它比其它的相等对比更宽松或严格。
    ```

77. escape,encodeURI,encodeURIComponent 有什么区别? 
    ```
    escape 和 encodeURI 都属于 Percent-encoding，基本功能都是把 URI 非法字符转化成合法字符，
    转化后形式类似「%*」。它们的根本区别在于，escape 在处理 0xff 之外字符的时候，是直接使用字符的
    unicode 在前面加上一个 「%u」，而 encodeURI 则是先进行 UTF-8，再在 UTF-8 的每个字节码前加上
    一个 「%」；在处理 0xff 以内字符时，编码方式是一样的（都是「%XX」，XX 为字符的 16 进制 unicode，
    同时也是字符的 UTF-8），只是范围（即哪些字符编码哪些字符不编码）不一样。
    ```
    详细资料可以参考：
    [escape,encodeURI,encodeURIComponent有什么区别?](https://www.zhihu.com/question/21861899)
    [字符编码笔记：ASCII，Unicode 和 UTF-8](http://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html)


78. js 的事件循环是什么？
    ```
    事件队列是一个存储着待执行任务的队列，其中的任务严格按照时间先后顺序执行，排在队头的任务将会率先执行，而排
    在队尾的任务会最后执行。事件队列每次仅执行一个任务，在该任务执行完毕之后，再执行下一个任务。执行栈则是一个
    类似于函数调用栈的运行容器，当执行栈为空时，JS 引擎便检查事件队列，如果不为空的话，事件队列便将第一个任务
    压入执行栈中运行。
    ```
    详细资料可以参考：
    [浏览器事件循环机制（event loop）](https://juejin.im/post/5afbc62151882542af04112d)
    [详解JavaScript中的Event Loop（事件循环）机制](https://zhuanlan.zhihu.com/p/33058983)
    [什么是 Event Loop？](http://www.ruanyifeng.com/blog/2013/10/event_loop.html)


79. js 中的深浅拷贝实现？
    ```
    浅拷贝的实现

    var shallowCopy = function(obj) {
    // 只拷贝对象
    if (typeof obj !== 'object') return;
    // 根据obj的类型判断是新建一个数组还是对象
    var newObj = obj instanceof Array ? [] : {};
    // 遍历obj，并且判断是obj的属性才拷贝
    for (var key in obj) {
        if (obj.hasOwnProperty(key)) {
            newObj[key] = obj[key];
        }
    }
    return newObj;
    }

    深拷贝的实现

    var deepCopy = function(obj) {
    if (typeof obj !== 'object') return;
    var newObj = obj instanceof Array ? [] : {};
    for (var key in obj) {
        if (obj.hasOwnProperty(key)) {
            newObj[key] = typeof obj[key] === 'object' ? deepCopy(obj[key]) : obj[key];
        }
    }
    return newObj;
    }

    ```
    详细资料可以参考：
    [JavaScript专题之深浅拷贝](https://github.com/mqyqingfeng/Blog/issues/32)
    [前端面试之道](https://juejin.im/book/5bdc715fe51d454e755f75ef/section/5bed40d951882545f73004f6)

80. 手写 call、apply 及 bind 函数
    ```
    call 函数实现

    Function.prototype.myCall = function(context) {
      if (typeof this !== 'function') {
        throw new TypeError('Error')
      }
      context = context || window
      context.fn = this
      const args = [...arguments].slice(1)
      const result = context.fn(...args)
      delete context.fn
      return result
    }

    apply 函数实现

    Function.prototype.myApply = function(context) {
      if (typeof this !== 'function') {
        throw new TypeError('Error')
      }
      context = context || window
      context.fn = this
      let result
      // 处理参数和 call 有区别
      if (arguments[1]) {
        result = context.fn(...arguments[1])
      } else {
        result = context.fn()
      }
      delete context.fn
      return result
    }

    bind 函数实现

    Function.prototype.myBind = function (context) {
      if (typeof this !== 'function') {
        throw new TypeError('Error')
      }
      const _this = this
      const args = [...arguments].slice(1)
      // 返回一个函数
      return function F() {
        // 因为返回了一个函数，我们可以 new F()，所以需要判断
        if (this instanceof F) {
          return new _this(...args, ...arguments)
        }
        return _this.apply(context, args.concat(...arguments))
      }
    }
    ```
    详细资料可以参考：
    [手写 call、apply 及 bind 函数](https://juejin.im/book/5bdc715fe51d454e755f75ef/section/5bdd0d8e6fb9a04a044073fe)
    [JavaScript深入之call和apply的模拟实现](https://github.com/mqyqingfeng/Blog/issues/11)


81. 为什么 0.1 + 0.2 != 0.3？如何解决这个问题？
    详细资料可以参考：
    [0.1 + 0.2不等于0.3？](https://juejin.im/post/5b90e00e6fb9a05cf9080dff)
    [JavaScript 中的数字](http://web.jobbole.com/74199/)


82. 浏览器的渲染原理？
    详细资料可以参考：
    [浏览器渲染原理](https://juejin.im/book/5bdc715fe51d454e755f75ef/section/5bdc7207f265da613c09425d)
    [浏览器的渲染原理简介](https://coolshell.cn/articles/9666.html)
    [前端必读：浏览器内部工作原理](https://kb.cnblogs.com/page/129756/)
    [深入浅出浏览器渲染原理](https://blog.fundebug.com/2019/01/03/understand-browser-rendering/)


83. 前端安全防范
    详细资料可以参考：
    [前端安全系列（一）：如何防止XSS攻击？](https://juejin.im/post/5bad9140e51d450e935c6d64)
    [内容安全策略   (CSP) ](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CSP)
    [前端安全系列之二：如何防止CSRF攻击？](https://juejin.im/post/5bc009996fb9a05d0a055192)
    [web安全之--点击劫持攻击与防御技术简介](https://juejin.im/post/5bc009996fb9a05d0a055192)
    [[HTTP趣谈]origin,referer和host区别](https://www.jianshu.com/p/1f9c71850299)

84. 什么是 MVVM？比之 MVC 有什么区别？
    详细资料可以参考：
    [浅析前端开发中的 MVC/MVP/MVVM 模式](https://juejin.im/post/593021272f301e0058273468)
    [MVC，MVP 和 MVVM 的图示](http://www.ruanyifeng.com/blog/2015/02/mvcmvp_mvvm.html)
    [MVVM](https://juejin.im/book/5bdc715fe51d454e755f75ef/section/5bdc72e6e51d45054f664dbf)
    [一篇文章了解架构模式：MVC/MVP/MVVM](https://segmentfault.com/a/1190000015310674)

85. 什么是 Virtual DOM？为什么 Virtual DOM 比原生 DOM 快？
    详细资料可以参考：
    [Virtual DOM](https://juejin.im/book/5bdc715fe51d454e755f75ef/section/5bdc72e6e51d45054f664dbf)
    [理解 Virtual DOM](https://github.com/y8n/blog/issues/5)
    [深度剖析：如何实现一个 Virtual DOM 算法](https://github.com/livoras/blog/issues/13)
    [网上都说操作真实 DOM 慢，但测试结果却比 React 更快，为什么？](https://www.zhihu.com/question/31809713/answer/53544875)

86. 双向数据绑定原理？
    详细资料可以参考：
    [Vue.js双向绑定的实现原理](http://www.cnblogs.com/kidney/p/6052935.html?utm_source=gold_browser_extension)

87. 什么是 requestAnimationFrame ？
    详细资料可以参考：
    [你需要知道的requestAnimationFrame](https://juejin.im/post/5a82f0626fb9a06358657c9c)
    [CSS3动画那么强，requestAnimationFrame还有毛线用？](https://www.zhangxinxu.com/wordpress/2013/09/css3-animation-requestanimationframe-tween-%E5%8A%A8%E7%94%BB%E7%AE%97%E6%B3%95/)


88. 谈谈你对 webpack 的看法
    ```
    WebPack 是一个模块打包工具，你可以使用 WebPack 管理你的模块依赖，并编绎输出模块们所需的静态文件。它能
    够很好地管理、打包 Web 开发中所用到的 HTML、Javascript、CSS 以及各种静态文件（图片、字体等），让开发
    过程更加高效。对于不同类型的资源，webpack 有对应的模块加载器。webpack 模块打包器会分析模块间的依赖关系，
    最后 生成了优化且合并后的静态资源
    ```

89. offsetWidth/offsetHeight,clientWidth/clientHeight 与 scrollWidth/scrollHeight 的区别？
    ```
    offsetWidth/offsetHeight 返回值包含 content + padding + border 包含了滚动条

    clientWidth/clientHeight 返回值只包含 content + padding，如果有滚动条，也不包含滚动条

    scrollWidth/scrollHeight 返回值包含 content + padding + 溢出内容的尺寸
    ```
    详细资料可以参考：
    [offsetWidth/offsetHeight,clientWidth/clientHeight 与 scrollWidth/scrollHeight 的区别](https://www.bgpy.net/biancheng/js_49841.html)

90. 谈一谈你理解的函数式编程？
    ```
    简单说，"函数式编程"是一种"编程范式"（programming paradigm），也就是如何编写程序的方法论

    它具有以下特性：闭包和高阶函数、惰性计算、递归、函数是"第一等公民"、只用"表达式"
    ```
    详细资料可以参考：
    [函数式编程初探](http://www.ruanyifeng.com/blog/2012/04/functional_programming.html)

91. 异步编程的实现方式？
    ```
    回调函数
    优点：简单、容易理解
    缺点：不利于维护，代码耦合高

    事件监听(采用时间驱动模式，取决于某个事件是否发生)：
    优点：容易理解，可以绑定多个事件，每个事件可以指定多个回调函数
    缺点：事件驱动型，流程不够清晰

    发布/订阅(观察者模式)
    类似于事件监听，但是可以通过‘消息中心’，了解现在有多少发布者，多少订阅者

    Promise对象
    优点：可以利用then方法，进行链式写法；可以书写错误时的回调函数；
    缺点：编写和理解，相对比较难

    Generator函数
    优点：函数体内外的数据交换、错误处理机制
    缺点：流程管理不方便

    async函数
    优点：内置执行器、更好的语义、更广的适用性、返回的是Promise、结构清晰。
    缺点：错误处理机制

    ```

92. Js 动画与 CSS 动画区别及相应实现
    ```
    CSS3 的动画的优点

    在性能上会稍微好一些，浏览器会对 CSS3 的动画做一些优化
    代码相对简单

    缺点

    在动画控制上不够灵活
    兼容性不好

    JavaScript 的动画正好弥补了这两个缺点，控制能力很强，可以单帧的控制、变换，同时写得好完全可以兼
    容 IE6，并且功能强大。对于一些复杂控制的动画，使用 javascript 会比较靠谱。而在实现一些小的交互
    动效的时候，就多考虑考虑 CSS 吧
    ```

93. get 请求传参长度的误区
    ```
    误区：我们经常说 get 请求参数的大小存在限制，而 post 请求的参数大小是无限制的。

    实际上 HTTP 协议从未规定 GET/POST 的请求长度限制是多少。对 get 请求参数的限制是来源与浏览器或 web
    服务器，浏览器或 web 服务器限制了 url 的长度。为了明确这个概念，我们必须再次强调下面几点:

    （1）HTTP 协议 未规定 GET 和 POST 的长度限制
    （2）GET 的最大长度显示是因为 浏览器和 web 服务器限制了 URI 的长度
    （3）不同的浏览器和 WEB 服务器，限制的最大长度不一样
    （4）要支持 IE，则最大长度为 2083byte，若只支持 Chrome，则最大长度 8182byte
    ```

94. URL 和 URI 的区别？
    ```
    URI：Uniform Resource Identifier，统一资源标识符
    URL：Uniform Resource Location统一资源定位符

    URL是一种 URI，它标识一个互联网资源，并指定对其进行操作或获取该资源的方法。可能通过对主要访问手段的描述，
    也可能通过网络“位置”进行标识。
    ```
    详细资料可以参考：
    [HTTP 协议中 URI 和 URL 有什么区别？](https://www.zhihu.com/question/21950864)

95. get 和 post 请求在缓存方面的区别
    ```
    get 请求类似于查找的过程，用户获取数据，可以不用每次都与数据库连接，所以可以使用缓存。

    post 不同，post 做的一般是修改和删除的工作，所以必须与数据库交互，所以不能使用缓存。因此 get 请求适合
    于请求缓存。
    ```

96. 图片的懒加载和预加载
    ```
    预加载：提前加载图片，当用户需要查看时可直接从本地缓存中渲染。

    懒加载：懒加载的主要目的是作为服务器前端的优化，减少请求数或延迟请求数。

    两种技术的本质：两者的行为是相反的，一个是提前加载，一个是迟缓甚至不加载。 懒加载对服务器前端有一定的
    缓解压力作用，预加载则会增加服务器前端压力。
    ```

97. mouseover 和 mouseenter 的区别？
    ```
    当鼠标移动到元素上时就会触发 mouseenter 事件，类似 mouseover，它们两者之间的差别是 mouseenter 
    不会冒泡。

    由于 mouseenter 不支持事件冒泡，导致在一个元素的子元素上进入或离开的时候会触发其 mouseover 和
    mouseout 事件，但是却不会触发 mouseenter 和 mouseleave 事件。
    ```
    详细资料可以参考：
    [mouseenter与mouseover为何这般纠缠不清？](https://github.com/qianlongo/zepto-analysis/issues/1)


98. js 拖拽功能的实现
    ```
    首先是三个事件，分别是 mousedown，mousemove，mouseup
    当鼠标点击按下的时候，需要一个 tag 标识此时已经按下，可以执行 mousemove 里面的具体方法。
    clientX，clientY 标识的是鼠标的坐标，分别标识横坐标和纵坐标，并且我们用 offsetX 和 offsetY 来表示
    元素的元素的初始坐标，移动的举例应该是：
    鼠标移动时候的坐标-鼠标按下去时候的坐标。
    也就是说定位信息为：
    鼠标移动时候的坐标-鼠标按下去时候的坐标+元素初始情况下的offetLeft.
    ```
    详细资料可以参考：
    [js拖拽功能的实现](https://juejin.im/post/5b44a485e51d4519945fb6b7)

99. 用 setTimeout 实现 setInterval
    ```
    思路是使用递归函数，不断地去执行 setTimeout 从而达到 setInterval 的效果

    function mySetInterval(fn, millisec,count){
      function interval(){
        if(typeof count===‘undefined’||count-->0){
          setTimeout(interval, millisec);
          try{
            fn()
          }catch(e){
            t = 0;
            throw e.toString();
          }
        }
      }
      setTimeout(interval, millisec)
    }
    ```
    详细资料可以参考：
    [用setTimeout实现setInterval](https://www.jianshu.com/p/32479bdfd851)
    [setInterval有什么缺点？](https://zhuanlan.zhihu.com/p/51995737)