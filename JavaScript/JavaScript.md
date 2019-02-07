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
   当我们调用构造函数创建一个新实例后，在这个实例的内部将包含一个指针，指向构造函数的 prototype 属性，在 ECMA-262 第五版中管这个指针叫做 [[Prototype]]（原型）。

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

   引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；引用数据
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
    所有 typeof 返回值为"object" 的对象（如数组）都包含一个内部属性 [[Class]]（我们可以把它看作一个内部
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

    基本类型值的字符串化规则为：null 转换为"null"，undefined 转换为"undefined"，true 转换为"true"。
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

16. 其他值到布尔类型的值的转换规则？
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

17. 什么是假值对象？
    ```
    浏览器在某些特定情况下，在常规 JavaScript 语法基础上自己创建了一些外来值，这些就是“假值对象”。假值对象
    看起来和普通对象并无二致（都有属性，等等），但将它们强制类型转换为布尔值时结果为 false 最常见的例子是document.all，它是一个类数组对象，包含了页面上的所有元素，由 DOM（而不是JavaScript 引擎）提供给 JavaScript 程序使用。
    ```

18. ~ 操作符的作用？
    ```
    ~ 返回 2 的补码。

    ~x 大致等同于-(x+1)。
    ```

19. 解析字符串中的数字和将字符串强制类型转换为数字的返回结果都是数字，它们之间的区别是什么？
    ```
    解析允许字符串（如 parseInt() ）中含有非数字字符，解析按从左到右的顺序，如果遇到非数字字符就停止。而
    转换（如 Number ()）不允许出现非数字字符，否则会失败并返回 NaN。
    ```

20.  `+` 操作符什么时候用于字符串的拼接？
    ```
    根据 ES5 规范 11.6.1 节，如果某个操作数是字符串或者能够通过以下步骤转换为字符串的话，+ 将进行拼接操作。
    如果其中一个操作数是对象（包括数组），则首先对其调用 ToPrimitive 抽象操作，该抽象操作再调用[[DefaultValue]]，以数字作为上下文。

    简单来说就是，如果 + 的其中一个操作数是字符串（或者通过以上步骤可以得到字符串），则执行字符串拼接；否则执
    行数字加法。
    ```

21. 什么情况下会发生布尔值的隐式强制类型转换？
    ```
    （1） if (..) 语句中的条件判断表达式。
    （2） for ( .. ; .. ; .. ) 语句中的条件判断表达式（第二个）。
    （3） while (..) 和 do..while(..) 循环中的条件判断表达式。
    （4） ? : 中的条件判断表达式。
    （5） 逻辑运算符 ||（逻辑或）和 &&（逻辑与）左边的操作数（作为条件判断表达式）。
    ```

22. || 和 && 操作符的返回值？
    ```
    || 和 && 首先会对第一个操作数（a 和 c）执行条件判断，如果其不是布尔值（如上例）就
    先进行 ToBoolean 强制类型转换，然后再执行条件判断。

    对于 || 来说，如果条件判断结果为 true 就返回第一个操作数（a 和 c）的值，如果为
    false 就返回第二个操作数（b）的值。

    && 则相反，如果条件判断结果为 true 就返回第二个操作数（b）的值，如果为 false 就返
    回第一个操作数（a 和c）的值。

    || 和 && 返回它们其中一个操作数的值，而非条件判断的结果 
    ```

23. Symbol 值的强制类型转换？
    ```
    ES6 允许从符号到字符串的显式强制类型转换，然而隐式强制类型转换会产生错误。

    Symbol 值不能够被强制类型转换为数字（显式和隐式都会产生错误），但可以被强制类型转换为布尔值
    （显式和隐式结果都是 true ）。
    ```

24. == 操作符的强制类型转换规则？
    ```
    （1）符串和数字之间的相等比较，将字符串转换为数字之后再进行比较。

    （2）其他类型和布尔类型之间的相等比较，先将布尔值转换为数字后，在应用其他规则进行比较。

    （3） null 和 undefined 之间的相等比较，结果为真。其他值和它们进行比较都返回假值。

    （4） 对象和非对象之间的相等比较，对象先调用 ToPromitive 抽象操作后，再进行比较。
    ```

25. 如何将字符串转化为数字，例如 '12.3b'?
    ```
    （1） 使用 Number() 方法，前提是所包含的字符串不包含不合法字符。

    （2） 使用 parseInt() 方法，parseInt() 函数可解析一个字符串，并返回一个整数。还可以设置要解析的数
         字的基数。当基数的值为 0，或没有设置该参数时，parseInt() 会根据 string 来判断数字的基数。

    （3）使用 parseFloat() 方法，该函数解析一个字符串参数并返回一个浮点数。

    （4）使用 + 操作符的隐式转换。
    ```
    详细资料可以参考：
    [详解JS中Number()、parseInt()和parseFloat()的区别](https://blog.csdn.net/m0_38099607/article/details/72638678)


26. 如何将浮点数点左边的数每三位添加一个逗号，如12000000.11转化为『12,000,000.11』?
    ```
    function format(number){
         return number && number.replace(/(?!^)(?=(\d{3})+\.)/g,",")
    }
    ```
27. 生成随机数的各种方法？
    [JS - 生成随机数的方法汇总（不同范围、类型的随机数）](http://www.hangge.com/blog/cache/detail_1872.html)

28. 如何实现数组的随机排序？
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

29. javascript 创建对象的几种方式？
    [JavaScript深入理解之对象创建](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E5%AF%B9%E8%B1%A1%E5%88%9B%E5%BB%BA.html)

30. JavaScript 继承的几种实现方式？
    [JavaScript深入理解之继承](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E7%BB%A7%E6%89%BF.html)

31. Javascript 的作用域链?
    [JavaScript深入理解之作用域链](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E4%BD%9C%E7%94%A8%E5%9F%9F%E9%93%BE.html)

32. 谈谈 This 对象的理解。
    [JavaScript深入理解之this详解](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8Bthis%E8%AF%A6%E8%A7%A3.html)

33. eval 是做什么的？
    ```
    它的功能是把对应的字符串解析成 JS 代码并运行。

    应该避免使用 eval，不安全，非常耗性能（2次，一次解析成 js 语句，一次执行）。
    ``` 
    详细资料可以参考：
    [eval()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/eval)

34. 什么是 window 对象? 什么是 document 对象?
    ```
    Window 对象表示浏览器中打开的窗口。如果文档包含框架（frame 或 iframe 标签），浏览器会为 HTML 文档
    创建一个 window 对象，并为每个框架创建一个额外的 window 对象。

    每个载入浏览器的 HTML 文档都会成为 Document 对象。Document 对象使我们可以从脚本中对 HTML 页面中的
    所有元素进行访问。Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。
    ```
    详细资料可以参考：
    [DOM, DOCUMENT, BOM, WINDOW 有什么区别?](https://www.zhihu.com/question/33453164)
    [Window 对象](http://www.w3school.com.cn/jsref/dom_obj_window.asp)

35. null，undefined 的区别？
    [JavaScript深入理解之undefined与null](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8Bundefined%E4%B8%8Enull.html)



36. 写一个通用的事件侦听器函数。
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
  
37. 事件是什么？IE 与火狐的事件机制有什么区别？ 如何阻止冒泡？
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


38. ["1", "2", "3"].map(parseInt) 答案是多少？
    ```
    parseInt() 函数能解析一个字符串，并返回一个整数，需要两个参数 (val, radix)，其中 radix 表示要解析
    的数字的基数。（该值介于 2 ~ 36 之间，并且字符串中的数字不能大于 radix 才能正确返回数字结果值）。


    此处 map 传了 3 个 参数(element, index, array)，默认第三个参数被忽略掉，因此三次传入的参数分别为

    "1-0", "2-1", "3-2"

    因为字符串的值不能大于基数，因此后面两次调用均失败，返回 NaN ，第一次基数为 0 ，按十进制解析返回1。

    ```
    详细资料可以参考：
    [为什么 ["1", "2", "3"].map(parseInt) 返回 [1,NaN,NaN]？](https://blog.csdn.net/justjavac/article/details/19473199)

39. 什么是 闭包（closure），为什么要用它？
    ```
    闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，
    通过另一个函数访问这个函数的局部变量,利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。

    ```
    详细资料可以参考：
    [JavaScript深入理解之闭包](http://cavszhouyou.top/JavaScript%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E4%B9%8B%E9%97%AD%E5%8C%85.html)


40. javascript 代码中的 "use strict"; 是什么意思 ? 使用它区别是什么？
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


41. 如何判断一个对象是否属于某个类？
    ```
    instanceof 运算符用于测试构造函数的 prototype 属性是否出现在对象的原型链中的任何位置。
    ```
    详细资料可以参考：
    [instanceof](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/instanceof)
    [js 判断一个对象是否属于某一类](https://blog.csdn.net/haitunmin/article/details/78418522)

42. new 操作符具体干了什么呢?
    ```
    （1）首先创建了一个空对象
    （2）设置原型，将对象的原型设置为函数的 prototype 对象。
    （3）让函数的 this 指向这个对象，执行构造函数的代码（为这个新对象添加属性）
    （4）判断函数的返回值类型，如果是值类型，返回创建的对象。如果是引用类型，就返回这个引用类型的对象。
    ```
    详细资料可以参考：
    [new 操作符具体干了什么？](https://segmentfault.com/a/1190000008576048)


43. Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？
    ```
    hasOwnProperty

    所有继承了 Object 的对象都会继承到 hasOwnProperty 方法。这个方法可以用来检测一个对象是否含有特定
    的自身属性；和 in 运算符不同，该方法会忽略掉那些从原型链上继承到的属性。
    ```
    详细资料可以参考：
    [Object.prototype.hasOwnProperty()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)

44. 对于 JSON 的了解？
    ```
    JSON 是一种数据交换格式，基于文本，优于轻量，用于交换数据。

    JSON 可以表示数字、布尔值、字符串、null、数组（值的有序序列），以及由这些值（或数组、对象）所组成的
    对象（字符串与值的映射）。
    ```
    详细资料可以参考：
    [深入了解JavaScript中的JSON ](https://my.oschina.net/u/3284240/blog/874368)


45. [].forEach.call($$("*"),function(a){a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16)}) 能解释一下这段代码的意思吗？
    ```
    （1）选取页面所有 DOM 元素。

    （2）循环遍历 DOM 元素

    （3）给元素添加 outline 。

    （4）生成随机颜色函数。
    ```
    详细资料可以参考：
    [通过一行代码学JavaScript](https://2008winstar.iteye.com/blog/2128290)
  
46. js 延迟加载的方式有哪些？
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