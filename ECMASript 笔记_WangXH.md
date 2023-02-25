<h1 style="text-align:center">ECMASript 语言笔记</h1>

--------------------------------------------------------------------------------
* 参考文档
    * 官方
        - [ECMAScript 官网](https://www.ecma-international.org/publications-and-standards/standards/ecma-262/)
        - [JavaSript 官网](https://www.javascript.com/)
    * 网上资源
        - [JavaSript 教程](https://wangdoc.com/javascript/index.html)
        - [ECMAScript 6 教程](https://wangdoc.com/es6/)
* 笔记内容只到 ECMAScript 2020

--------------------------------------------------------------------------------

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=3 orderedList=false} -->

<!-- code_chunk_output -->

- [1. 关于 JavaScript](#-1-关于-javascript-)
- [2. 基础语法](#-2-基础语法-)
  - [2.1. 关键词与保留词](#-21-关键词与保留词-)
    - [2.1.1. 关键词 (ES2020)](#-211-关键词-es2020-)
    - [2.1.2. 保留词 (ES2020)](#-212-保留词-es2020-)
  - [2.2. 标识符](#-22-标识符-)
  - [2.3. 语句结构](#-23-语句结构-)
  - [2.4. 注释](#-24-注释-)
  - [2.5. 数据类型与值](#-25-数据类型与值-)
    - [2.5.1. 概述](#-251-概述-)
    - [2.5.2. Undefined](#-252-undefined-)
    - [2.5.3. Null](#-253-null-)
    - [2.5.4. Boolean](#-254-boolean-)
    - [2.5.5. Number](#-255-number-)
    - [2.5.6. BigInt (ES2020)](#-256-bigint-es2020-)
    - [2.5.7. Symbol (ES6)](#-257-symbol-es6-)
    - [2.5.8. String](#-258-string-)
    - [2.5.9. Object](#-259-object-)
    - [2.5.10. 数组](#-2510-数组-)
    - [2.5.11. Function](#-2511-function-)
    - [2.5.12. Set (ES6)](#-2512-set-es6-)
    - [2.5.13. WeakSet (ES6)](#-2513-weakset-es6-)
    - [2.5.14. Map (ES6)](#-2514-map-es6-)
    - [2.5.15. WeakMap (ES6)](#-2515-weakmap-es6-)
    - [2.5.16. 类型转换](#-2516-类型转换-)
  - [2.6. 变量](#-26-变量-)
    - [2.6.1. 声明与赋值](#-261-声明与赋值-)
    - [2.6.2. 解构赋值 (ES6)](#-262-解构赋值-es6-)
    - [2.6.3. 声明提升 (Hoisting)](#-263-声明提升-hoisting-)
  - [2.7. 运算符](#-27-运算符-)
    - [2.7.1. 一般运算符](#-271-一般运算符-)
    - [2.7.2. 特殊运算符](#-272-特殊运算符-)
    - [2.7.3. 运算符优先级和结合性](#-273-运算符优先级和结合性-)
  - [2.8. 条件控制](#-28-条件控制-)
  - [2.9. 循环控制](#-29-循环控制-)
  - [2.10. 函数](#-210-函数-)
    - [2.10.1. 函数的声明](#-2101-函数的声明-)
    - [2.10.2. 函数的调用](#-2102-函数的调用-)
    - [2.10.3. 函数表达式](#-2103-函数表达式-)
    - [2.10.4. Function 对象](#-2104-function-对象-)
    - [2.10.5. 箭头函数 (ES6)](#-2105-箭头函数-es6-)
    - [2.10.6. 闭包](#-2106-闭包-)
    - [2.10.7. 全局 eval() 函数](#-2107-全局-eval-函数-)
  - [2.11. 作用域](#-211-作用域-)
    - [2.11.1. 作用域类型](#-2111-作用域类型-)
    - [2.11.2. 注意事项](#-2112-注意事项-)
  - [2.12. 对象](#-212-对象-)
    - [2.12.1. 创建](#-2121-创建-)
    - [2.12.2. 属性](#-2122-属性-)
    - [2.12.3. 方法](#-2123-方法-)
    - [2.12.4. 深入理解对象](#-2124-深入理解对象-)
    - [2.12.5. 元对象](#-2125-元对象-)
  - [2.13. 错误与异常](#-213-错误与异常-)
    - [2.13.1. 错误类型](#-2131-错误类型-)
    - [2.13.2. 异常处理](#-2132-异常处理-)
    - [2.13.3. 产生异常](#-2133-产生异常-)
  - [2.14. 模块 (ES6)](#-214-模块-es6-)
    - [2.14.1. export](#-2141-export-)
    - [2.14.2. import](#-2142-import-)
    - [2.14.3. 转发接口](#-2143-转发接口-)
  - [2.15. 输入/输出](#-215-输入输出-)
  - [2.16. 调试](#-216-调试-)
  - [2.17. 严格模式](#-217-严格模式-)
- [3. 面向对象编程](#-3-面向对象编程-)
  - [3.1. 构造器](#-31-构造器-)
    - [3.1.1. 构造函数](#-311-构造函数-)
    - [3.1.2. 构造对象的过程](#-312-构造对象的过程-)
    - [3.1.3. constructor 属性](#-313-constructor-属性-)
  - [3.2. this](#-32-this-)
  - [3.3. 继承](#-33-继承-)
    - [3.3.1. 原型链](#-331-原型链-)
    - [3.3.2. 构造函数的继承](#-332-构造函数的继承-)
    - [3.3.3. 多重继承](#-333-多重继承-)
  - [3.4. class (ES6)](#-34-class-es6-)
    - [3.4.1. 声明](#-341-声明-)
    - [3.4.2. 例化](#-342-例化-)
    - [3.4.3. 继承](#-343-继承-)
- [4. 高级语法 (ES6)](#-4-高级语法-es6-)
  - [4.1. Generator](#-41-generator-)
  - [4.2. Iterator](#-42-iterator-)
  - [4.3. 异步操作](#-43-异步操作-)
    - [4.3.1. 概述](#-431-概述-)
    - [4.3.2. 定时器](#-432-定时器-)
    - [4.3.3. Promise 对象](#-433-promise-对象-)
    - [4.3.4. async 和 await](#-434-async-和-await-)
    - [4.3.5. 异步遍历器](#-435-异步遍历器-)
  - [4.4. 二进制数组](#-44-二进制数组-)
- [5. 标准库](#-5-标准库-)
  - [5.1. 概述](#-51-概述-)
  - [5.2. Boolean 对象](#-52-boolean-对象-)
  - [5.3. Number 对象](#-53-number-对象-)
  - [5.4. BigInt](#-54-bigint-)
  - [5.5. Symbol](#-55-symbol-)
  - [5.6. String 对象](#-56-string-对象-)
  - [5.7. Array 对象](#-57-array-对象-)
  - [5.8. Set (ES6)](#-58-set-es6-)
  - [5.9. WeakSet (ES6)](#-59-weakset-es6-)
  - [5.10. Map (ES6)](#-510-map-es6-)
  - [5.11. WeakMap (ES6)](#-511-weakmap-es6-)
  - [5.12. Math 对象](#-512-math-对象-)
  - [5.13. Date  对象](#-513-date--对象-)
  - [5.14. RegExp 对象](#-514-regexp-对象-)
  - [5.15. JSON 对象](#-515-json-对象-)
- [6. 其它相关](#-6-其它相关-)
  - [6.1. Node.js](#-61-nodejs-)

<!-- /code_chunk_output -->

--------------------------------------------------------------------------------
# 1. 关于 JavaScript
* **特征**:
    * **解释型脚本语言**:
        * JavaScript 是一种解释型脚本语言, 无需编译, 可以直接运行
        * 常用的宿主环境: 浏览器, 服务器 (Node.js)
        * 宿主提供额外的 API, 例如浏览器的 API 可分为 3 类:
            * 浏览器控制类: 操作浏览器
            * DOM 类: 操作网页的各种元素
            * Web 类: 实现互联网的各种功能
    * **面向对象**:
        * JavaScript 是一种面向对象语言, 使用 JavaScript 不仅可以创建对象, 也能操作使用已有的对象
    * **弱类型**:
        * JavaScript 是一种弱类型的编程语言, 对使用的数据类型没有严格的要求, 可以将一个变量初始化为任意类型, 也可以随时改变这个变量的类型
    * **动态性**:
        * JavaScript 是一种采用事件驱动的脚本语言, 它不需要借助 Web 服务器就可以对用户的输入做出响应, 例如我们在访问一个网页时, 通过鼠标在网页中进行点击或滚动窗口时, 通过 JavaScript 可以直接对这些事件做出响应
    * **跨平台**:
        * JavaScript 不依赖操作系统, 在浏览器中就可以运行。因此一个 JavaScript 脚本在编写完成后可以在任意系统上运行, 只需要系统上的浏览器支持 JavaScript 即可
* **开发调试环境**
    * VSCode
    * 网页浏览器

--------------------------------------------------------------------------------
# 2. 基础语法

## 2.1. 关键词与保留词

### 2.1.1. 关键词 (ES2020)
* 列表
    ```js {.line-numbers}
    await,
    break,
    case, catch, class, const, continue,
    debugger, default, delete, do,
    else, enum, export, extends,
    false, finally, for, function,
    if, import, in, instanceof,
    new, null,
    return,
    super, switch,
    this, throw, true, try, typeof,
    var, void,
    while, with,
    yield
    ```
* 分类
    类别            | 关键词
    :-------------: | :-------------------------------------------------------
    数据类型        | `enum`
    变量            | `var`, `let`, `const`, `delete`
    内置常量        | `true`, `false`, `null`
    运算符          | `in`, `instanceof`, `typeof`, `void`
    程序控制 (分支) | `if...else if...else`, `switch...case...break...default`
    程序控制 (循环) | `for`, `for...in`, `for...of`, `while`, `do...while`, `break`, `continue`
    函数            | `function...return`
    异常处理        | `throw`, `try...catch...finally`
    类与对象        | `new`, `this`, `class`, `extends`, `super`
    异步编程        | `await`, `yield`
    模块            | `import`, `export`
    Runtime / 调试  | `debugger`
    其他            | `with`

### 2.1.2. 保留词 (ES2020)
```js {.line-numbers}
implements, interface,
package, private, protected, public,
```

## 2.2. 标识符
* 以 Unicode 字母 (包括英文字母和其他语言的字符), 下划线 (`_`) 或美元符号 (`$`)开始, 由 Unicode 字符 (包括数字) 组成
    * 支持中文标识符
    * 可以使用 Unicode 转义序列 (例如: 字符 a 可以使用 "\u0061" 表示)
* 不能是关键词或保留词
* 区分大小写
* 一般采用`驼峰式大小写`

## 2.3. 语句结构
* `;` 分隔语句
    * 行尾的`;`可有可无
    * 一行可写多个语句, 如
    ```js
    a = 5;
    b = 6;
    c = a + b
    // 一行可写多个语句
    a = 5; b = 6; c = a + b;
    ```
    * 一行只有一个表达式时无需`;`
    * 一行中最后一个表达式无需`;`
* 区块: `{...}`
* 标签: 相当于定位符, 用于跳转到程序的任意位置
    ```js
    标签:
        代码块
    ```
    * 常与 `break` 和 `continue` 配合使用

## 2.4. 注释
* `//...` 或 `/*...*/`
    ```js
    // 单行注释...

    /* ...
    多行注释
    ...*/
    ```

## 2.5. 数据类型与值

### 2.5.1. 概述
* 数据类型包括
    * **原始值**
        * [Undefined](#252-undefined)
        * [Null](#253-null)
        * [Boolean](#254-boolean)
        * [Number](#255-number)
        * [BigInt](#256-bigint-es2020)
        * [Symbol](#257-symbol-es6)
        * [String](#258-string)
    * `Object`
        * 数组, 参见 [数组](#2510-数组) 和 [Array 对象](#57-array-对象)
        * 函数 (一种特殊的 `object`)
        * [ES6] 集合 `Set` (参见 [Set 对象](#58-set-es6)), 弱集合 `WeakSet` (参见  [WeakSet 对象](#59-weakset-es6))
        * [ES6] 映射 `Map` (参见 [Map 对象](#510-map-es6)), 弱映射 `WeakMap` (参见 [WeakMap 对象](#511-weakmap-es6))
        * ...
* 原始值类型
    * 是基本数据类型, 赋值和传参时, 使用值传递
    * 其中部分原始值类型也有类似 `Object` 的属性和方法
        * `Boolean`: 参见 [Boolean 对象](#52-boolean-对象)
        * `Number`: 参见 [Number 对象](#53-number-对象)
        * `BigInt`: 参见 [BigInt 对象](#54-bigint)
        * `Symbol`: 参见 [Symbol 对象](#55-symbol)
        * `String`: 参见 [String 对象](#56-string-对象)
    * 其中部分原始值类型也有对应的 `Object`, 包括
        * [Boolean 对象](#52-boolean-对象)
        * [Number 对象](#53-number-对象)
        * [String 对象](#56-string-对象)
* `Object` 类型
    * 是引用数据类型
        * 赋值和传参时, 使用引用传递
        * 多个变量指向同一个 `Object` 时, 改变其中任意一个, 其它的都跟着变
* `typeof` 操作符可以获取变量的数据类型
    ```js
    typeof 变量
    typeof (变量)
    ```

### 2.5.2. Undefined
* 只有一个值 (`undefined`) 的特殊数据类型, 表示未定义
    * 声明一个变量但未给变量赋值时, 其默认值就是`Undefined`, 如
        ```js
        let num;        // 未被赋值时, num = undefined
        typeof(num);    // undefined
        ```
* 与 `null` 不同
    ```js
    typeof undefined    // undefined
    typeof null         // object
    null === undefined  // false
    null == undefined   // true
    ```

### 2.5.3. Null
* 只有一个值 (`null`) 的特殊数据类型, 表示 "空" 值, 如
    ```js
    let a = null;           // 将变量赋值为 null 可以创建一个空对象
    console.log(typeof a);  // 控制台输出: object
    ```

### 2.5.4. Boolean
* 只有两个值: `true`, `false`
* 可以通过一些表达式得到布尔类型的值, 如:
    ```js
    var a = true;
    var b = false;
    var c = 2 > 1;  // ture
    var d = 2 < 1;  // false
    ```
* `Boolean`类型转换时
    * `undefined`, `null`, `false`, `0`, `NaN`, 空字符串(`""`或`''`) 转为 `false`
    * 空对象 (`{}`) 和空数组 (`[]`) 转为 `true`
    * 其它全转为 `true`

### 2.5.5. Number
* JavaScript 使用 IEEE754 64 位浮点数表示所有数字, 包括整数和小数, 因此
    * 数值范围: $[5 \times 10^{-324}, 1.7976931348623157 \times 10^{308}]$
        * 分别对应 `Number.MIN_VALUE` 和 `Number.MAX_VALUE`
    * 由于精度问题, 能精确表示的整数的范围:  $[-2^{53} - 1, 2^{53} - 1]$, 即 $[-9007199254740991, 9007199254740991]$
        * 分别对应 `Number.MIN_SAFE_INTEGER` 和 `Number.MAX_SAFE_INTEGER`
        * 测试实例
            ```js
            // 整数范围
            console.log(2 ** 53);       // 输出: 9007199254740992
            console.log(2 ** 53 + 1);   // 输出: 9007199254740992
            console.log(2 ** 53 + 2);   // 输出: 9007199254740994
            console.log(2 ** 53 + 3);   // 输出: 9007199254740996
            console.log(2 ** 53 + 4);   // 输出: 9007199254740996
            // 超出后精度损失
            console.log(9007199254740992111);   // 输出: 9007199254740992000
            ```
    * 有两个 `0`: `+0` 和 `-0`, 基本完全等价
        ```js
        -0 === +0   // true
        0 === -0    // true
        0 === +0    // true

        (-0).toString() // '0'
        (+0).toString() // '0'

        (1 / +0) === (1 / -0)   // false
        (1 / +0)                // Infinity
        (1 / -0)                // -Infinity
        ```
    * 特殊值
        * `Infinity`: 正无穷, 一般指大于 `Number.MAX_VALUE` 的数
            * 大于一切数值
            * 基本运算符合数学计算规则
            * 特殊运算
                ```js
                0 * Infinity        // NaN
                0 / Infinity        // 0
                Infinity / 0        // Infinity
                Infinity + Infinity // Infinity
                Infinity * Infinity // Infinity
                Infinity - Infinity // NaN
                Infinity / Infinity // NaN
                null * Infinity     // NaN
                null / Infinity     // 0
                Infinity / null     // Infinity
                undefined + Infinity // NaN
                undefined - Infinity // NaN
                undefined * Infinity // NaN
                undefined / Infinity // NaN
                Infinity / undefined // NaN
                ```
        * `-Infinity`: 负无穷, 一般指小于 `Number.MIN_VALUE` 的数
            * 小于一切值
            * 运算规则与 `Infinity` 类似
        * `NaN`: 非数值 (Not a Number, NaN), 用来表示无效或未定义的数学运算结构, 如 0 除以 0
            * 与任何值运算的结果都是 `NaN`
            * 与任何值 (包括它本身) 的比较都返回 `false`
* 表示方法
    * 正常十进制表示
    * 二/八/十六进制 (`0b|0B`ddd, `0o|0O`ddd, `0x|0X`ddd)
        * 非严格模式下八进制还能使用 `0`ddd 格式
    * 科学计数法: ddd`.`ddd`e|E[+|-]`ddd, 如: 4.5E-6
    * [ES2021] 允许数值使用下划线 (`_`) 作为分隔符, 其位置没有要求
* 类似 `Object` 的属性和方法
    方法                    | 描述
    :---------------------- | :----------------------------
    .toExponential()        | 转为指数计数法
    .toFixed()              | 转为字符串, 结果的小数点后有指定位数的数字
    .toLocaleString()       | 转为字符串, 使用本地数字格式顺序
    .toPrecision()          | 格式化为指定的长度
* 与数值相关的全局方法
    * `parseInt()` (其实是 `Number.parseInt()`)
        * 将字符串转为整数
            * 自动过滤字符串前导的空格
            * 如果参数不是字符串, 则先转为字符串再转换
            * 如果遇到不能转为数字的字符, 就不再进行下去, 返回已经转好的部分
            * 如果第一个字符不能转化为数字 (后面跟着数字的正负号除外), 返回 `NaN`
            * 支持 16 进制解析, 不支持 2/8 进制解析
            * 对于那些会自动转为科学计数法的数字, 将科学计数法的表示方法视为字符串, 因此导致一些奇怪的结果

            如
            ```js
            parseInt('123')     // 123
            parseInt('   81')   // 81
            parseInt(1.23)      // 1
            // 等同于
            parseInt('1.23')    // 1
            parseInt('8a')      // 8
            parseInt('12**')    // 12
            parseInt('12.34')   // 12
            parseInt('15e2')    // 15
            parseInt('15px')    // 15
            parseInt('abc')     // NaN
            parseInt('.3')      // NaN
            parseInt('')        // NaN
            parseInt('+')       // NaN
            parseInt('+1')      // 1
            parseInt('0x10')    // 16
            parseInt('011')     // 11
            parseInt(1000000000000000000000.5) // 1
            // 等同于
            parseInt('1e+21')   // 1
            parseInt(0.0000008) // 8
            // 等同于
            parseInt('8e-7')    // 8
            ```
        * 进制转换
            * 接受第二个参数 (2~36之间), 表示被解析的值的进制, 返回该值对应的十进制数
            * 如果第二个参数不是数值, 会被自动转为一个整数, 只有在 2 到 36 之间才能得到有意义的结果, 否则返回 `NaN`
            * 如果第二个参数是 `0`, `undefined` 和 `null`, 则直接忽略
            * 如果字符串包含对于指定进制无意义的字符, 则从最高位开始, 只返回可以转换的数值; 如果最高位无法转换, 则直接返回 `NaN`
            * 如果第一个参数不是字符串, 会被先转为字符串, 会导致一些令人意外的结果
                * 对于八进制的前缀 `0`, 尤其需要注意

            如
            ```js
            parseInt('1546', 2) // 1
            parseInt('546', 2)  // NaN
            parseInt(0x11, 36)  // 43
            parseInt(0x11, 2)   // 1
            // 等同于
            parseInt('17', 36)
            parseInt('17', 2)
            parseInt(011, 2)    // NaN
            // 等同于
            parseInt(String(9), 2)
            ```
    * `parseFloat()` (其实是 `Number.parseFloat()`)
        * 将一个字符串转为浮点数
            * 支持科学计数法
            * 如果字符串包含不能转为浮点数的字符, 则不再进行往后转换, 返回已经转好的部分
            * 自动过滤字符串前导的空格
            * 如果不是字符串, 或者字符串的第一个字符不能转化为浮点数, 则返回 `NaN`
                * 将空字符串转为 `NaN`
            * 转换结果不同于 `Number` 函数

            如
            ```js
            parseFloat('3.14')      // 3.14
            parseFloat('314e-2')    // 3.14
            parseFloat('0.0314E+2') // 3.14
            parseFloat('3.14more non-digit characters') // 3.14
            parseFloat('\t\v\r12.34\n ') // 12.34
            parseFloat([])          // NaN
            parseFloat('FF2')       // NaN
            parseFloat('')          // NaN

            parseFloat(true)        // NaN
            Number(true)            // 1
            parseFloat(null)        // NaN
            Number(null)            // 0
            parseFloat('')          // NaN
            Number('')              // 0
            parseFloat('123.45#')   // 123.45
            Number('123.45#')       // NaN
            ```
    * `isNaN()`
        * 判断一个值是否为 `NaN`
        * 只对数值有效, 如果传入其他值, 会被先转成数值
            * 如, 传入字符串的时候, 字符串会被先转成 `NaN`, 所以最后返回 `true`
            * 对于对象和数组, `isNaN` 也返回 `true`
            * 对于空数组和只有一个数值成员的数组, `isNaN` 返回 `false`

        如
        ```js
        isNaN(NaN)      // true
        isNaN(123)      // false
        isNaN('Hello')  // true
        // 相当于
        isNaN(Number('Hello'))  // true
        isNaN({})           // true
        // 等同于
        isNaN(Number({}))   // true
        isNaN(['xzy'])      // true
        // 等同于
        isNaN(Number(['xzy'])) // true
        isNaN([])       // false
        isNaN([123])    // false
        isNaN(['123'])  // false
        ```

        ```js
        // 使用 isNaN 之前, 最好判断一下数据类型
        function myIsNaN(value) {
            return typeof value === 'number' && isNaN(value);
        }
        // 判断NaN更可靠的方法是, 利用 NaN 为唯一不等于自身的值的这个特点, 进行判断
        function myIsNaN(value) {
            return value !== value;
        }
        ```
    * `isFinite()`
        * 某个值是否为正常的数值

        如
        ```js
        isFinite(Infinity)  // false
        isFinite(-Infinity) // false
        isFinite(NaN)       // false
        isFinite(undefined) // false
        isFinite(null)      // true
        isFinite(-1)        // true
        ```

### 2.5.6. BigInt (ES2020)
* 只用来表示整数, 没有位数的限制
* 表示方式: 整数 + 后缀 `n`, 如
    ```js
    123n    // 十进制
    0b1101n // 二进制
    0o777n  // 八进制
    0xFFn   // 十六进制
    ```
* 可以使用负号 (`-`), 但是不能使用正号 (`+`)

### 2.5.7. Symbol (ES6)
* 表示独一无二的值, 使用 `Symbol(变量或值)` 函数创建
    * 只要创建就独一无二, 即便使用相同的值创建
    * 不能与其他类型的值进行运算
* 可以转换为字符串或布尔值

    如
    ```js
    var str = "123";
    var sym1 = Symbol(str);
    var sym2 = Symbol(str);
    console.log(sym1);          // 输出 Symbol(123)
    console.log(sym2);          // 输出 Symbol(123)
    console.log(sym1 == sym2);  // 输出 false: sym1 和 sym2 都是独一无二的
    ```

### 2.5.8. String
* 一对单引号`'`或双引号`"`包裹的文本
    * 建议静态字符串一律使用单引号或反引号, 不使用双引号
    * 建议动态字符串使用反引号
* JavaScript 使用 Unicode 字符集
* 转义符
    转义字符    | 描述
    :---------: | :--------
    `\`(行尾)   | 续行符 (有些 JavaScript 宿主可能不支持)
    `\0`        | `null`
    `\'`        | 单引号
    `\"`        | 双引号
    `\\`        | 反斜杠符号
    `\b`        | 退格(Backspace)
    `\f`        | 换页
    `\n`        | 换行
    `\r`        | 回车
    `\t`        | 横向制表符
    `\v`        | 纵向制表符
    `\xyy`      | 十六进制数, y 是十六进制数, 例如: \x0a代表换行
    `\uXXXX`    | Unicode 码, X 是十六进制数
    `\u{X...X}` | [ES6] Unicode 码, X 是十六进制数, X 的数量可变
* 若字符串中包含引号, 可以使用转义符`\`, 或变换引号, 如:
    ```js
    let str = "Let's have a cup of coffee.";  // 双引号中包含单引号
    let str = 'He said "Hello" and left.';    // 单引号中包含双引号
    let str = 'We\'ll never give up.';        // 使用反斜杠转义字符串中的单引号
    ```
* 拼接: `字符串1 + 字符串2`
    * `字符串 + 变量`, `变量 + 字符串` 根据情况对表达式进行转换
        ```js
        '3' + 4 + 5 // "345"
        3 + 4 + '5' // "75"
        ```
    * 多行字符串可用 `+` 拼接
* **模板字符串** (ES6): 一对反引号 ``` ` ``` (不是单引号) 包裹的文本
    * 空格, 换行都被保留
    * 支持变量或表达式替换
        * 其中可以包含模板字符串, 即支持嵌套
        ```js
        `...${替换的变量或表达式}...`
        ```

        如
        ```js
        let a = 3;
        console.log(`${a} 的平方 = ${a**2}`)  // 3 的平方 = 9
        ```

### 2.5.9. Object
* 由 `(键, 值)` 对儿组成的无序集合, 字面量表示方法:
    ```js
    {键1: 值1, 键2: 值2, ..., 键n: 值n}
    ```
    * 键根据情况也叫属性或方法
        * 属性: 对应的值不是函数
        * 方法: 对应的值是函数
* 参见 [对象](#212-对象)

### 2.5.10. 数组
* 一种特殊的 `Object`
* 一组数据的集合, 可以包含任意类型的数据, 字面量表示方法:
    ```[元素1, 元素2, ..., 元素n]```
* 可用全局对象`Array`来处理数组

### 2.5.11. Function
* 一种特殊的`Object`, 详见 [Function 对象](#2103-function-对象)

### 2.5.12. Set (ES6)
* 类似于数组, 但是成员的值都是唯一的, 没有重复的值
    * 判断是否重复, 使用`===`运算
        * `NaN` 除外
* 创建
    ```js
    集合变量 = new Set(数组)
    集合变量 = Set(数组)
    ```

### 2.5.13. WeakSet (ES6)
* 与 `Set` 类似, 也是不重复的值的集合
* 区别
    * 只能是对象, 而不能是其他类型的值
    * 其中的对象都是弱引用
        * 即垃圾回收机制不考虑 `WeakSet` 对该对象的引用, 如果其他对象都不再引用该对象, 那么垃圾回收机制会自动回收该对象所占用的内存, 不考虑该对象还存在于 `WeakSet` 之中
        * 适合临时存放一组对象, 以及存放跟对象绑定的信息, 要这些对象在外部消失, 它在 `WeakSet` 里面的引用就会自动消失

### 2.5.14. Map (ES6)
* 类似于对象, 也是键值对的集合, 但是 "键" 的范围不限于字符串, 各种类型的值 (包括对象) 都可以当作键
    * `Map` 结构提供了 "值—值" 的对应, 是一种更完善的 Hash 结构实现
    * 如果对同一个键多次赋值, 后面的值将覆盖前面的值
    * 如果读取一个未知的键, 则返回`undefined`
    * 同样的值的两个实例, 在 `Map` 结构中被视为两个键
        * `Map` 的键实际上是跟内存地址绑定的
* 创建
    ```js
    Map变量 = new Map(数组)
    Map变量 = Map(数组)
    ```

### 2.5.15. WeakMap (ES6)
* 与`Map`结构类似, 也是用于生成键值对的集合
* 区别
    * 键名只能是对象 (`null`除外), 不接受其他类型的值作为键名
    * 键名所指向的对象都是弱引用

### 2.5.16. 类型转换
* 强制转换
    * 使用`Boolean()`, `Number()`, `BigInt()`, `Symbol()`, `String()` 等全局函数
* 自动转换:
    * 遇到以下三种情况时, JavaScript 会自动转换数据类型
        * 不同类型的数据互相运算
            ```js
            123 + 'abc' // "123abc"
            ```
        * 对非布尔值类型的数据求布尔值
            ```js
            if ('abc') {
                console.log('hello')
            }  // "hello"
            ```
        * 对非数值类型的值使用一元运算符 (如`+`和`-`)
            ```js
            + {foo: 'bar'}  // NaN
            - [1, 2, 3]     // NaN
            ```
    * 基本规则: 预期什么类型的值, 就调用该类型的转换函数, 如
        * 某个位置预期为字符串, 就调用`String()`函数进行转换
        * 如果该位置既可以是字符串, 也可能是数值, 那么默认转为数值
    * ==自动转换具有不确定性, 而且不易除错, 建议进行显式转换==

## 2.6. 变量
* 概念上的字面量和变量
    * 字面量: 被赋给变量的值
    * 变量:
        * 未被赋值的变量是 `Undefined` 类型
        * 用原始值赋值的变量是对应的原始值类型
            * 但用`new 原始值对象(原始值)`赋值的变量的数据类型是 `Object`
        * 用`Object`, 数组, 函数赋值的变量, 其类型是 `Object`, `Object`, `function`

### 2.6.1. 声明与赋值
* 语法:
    ```js
    // 声明
    var/let/const 变量;
    var/let/const 变量1, 变量2, 变量3;
    var/let/const 变量 = 值;
    var/let/const 变量1 = 值1, 变量2 = 值2;

    // 重新赋值
    变量 = 新值;    // const 声明的变量不能重新赋值
    ```
    * 建议用`let`取代`var`
    * 建议优先使用`const`
* 定义变量时无需指定变量类型, 程序运行时动态决定, 可使用同一个变量存储不同类型的数据, 如:
    ```js
    var a;              // 此时 a 为 Undefined
    a = "abc";          // 此时 a 为 String 类型
    a = 123;            // 此时 a 为 Number 类型
    a = function(){};   // 此时 a 为 Function 类型
    ```
* `var` 在任何位置都可以重新声明
* `let` 声明的变量只在其所在的代码块中有效
    * 在同一个作用域, 不能再次声明同一个变量
        * 在更内层的作用域中, `let` 可以声明同一个变量, 且临时 "绑定" (binding)
    * 声明的变量不会被提升, 变量不能在声明前使用
* `const` 声明的变量必须在声明时赋值, 且不能修改
    * `const` 并没有定义常量值, 只是定义了对值的常量引用, 虽然不能更改常量原始值, 但可以更改常量对象的属性
        ```js
        // 对于对象
        const car = {type:"porsche", model:"911", color:"Black"};
        car.color = "White";    // 以更改属性
        car.owner = "Bill";     // 可以添加属性
        car = {type:"Volvo", model:"XC60", color:"White"};  // 报错
        // 对于数组
        const cars = ["Audi", "BMW", "porsche"];
        cars[0] = "Honda";  // 可以更改元素
        cars.push("Volvo"); // 可以添加元素
            cars = ["Honda", "Toyota", "Volvo"];    // 报错
        ```
    * 只在其所在的代码块中有效
    * 在同一个作用域, 不能再次声明同一个变量
    * 声明的变量不会被提升, 变量不能在声明前使用

### 2.6.2. 解构赋值 (ES6)
* 语法
    ```js
    [变量列表] = 可枚举的变量 (如数组, 字符串, ...) // 变量列表的数量 无需与 可枚举的变量的数量 相同
    [变量1, 变量2, 。。。, ...rest_变量] = 可枚举的变量 (如数组, 字符串, ...)

    {变量列表} = 对象变量                           // 变量必须与属性同名, 才能取到正确的值, 无需列举所有变量
    {变量1, 变量2, 。。。, ...rest_变量} = 对象变量 // 变量必须与属性同名, 才能取到正确的值, rest 变量必须出现在最后一个
    {属性1:变量1, 属性2:变量2} = 对象变量           // 键必须与属性或方法同名, 属性或方法的值传递给变量
    {属性1, 属性2, 。。。, ...rest_变量} = 对象变量 // 键必须与属性或方法同名, 属性或方法的值传递给变量, rest 变量必须出现在最后一个
    ```

    如
    ```js
    let [x, y] = [1, 2, 3];     // x = 1, y = 2
    let [x, ...y] = [1, 2, 3];  // x = 1, y = [2, 3]

    const { log, info } = console;
    log('hello')    // 控制台输出: hello

    let v1 = {..."hello"}   // v1 = {0: 'h', 1: 'e', 2: 'l', 3: 'l', 4: 'o'}
    let { foo: baz } = { foo: 'aaa', bar: 'bbb' };  // baz = "aaa"
    ```
* 注意: 解构赋值是浅 copy
* 用途
    * 交换变量的值
    * 从函数返回多个值
    * 函数参数的定义
    * 提取 JSON 数据
    * 函数参数的默认值
    * 遍历 Map 结构
    * 输入模块的指定方法

### 2.6.3. 声明提升 (Hoisting)
* 变量和函数可以在使用后声明, 解释器会将它们提升到函数的最顶部
    * 严格模式下不会提升, 必须先声明后使用
* 只有声明的变量会提升, 初始化的不会

    如
    ```js
    // a 将被提升
    a = 5;
    var rslt = a ** 2;
    console.log(rslt);
    var a;
    // b 不被提升
    console.log(b);
    var b = 7;
    // f1 将被提升
    f1();   // 输出: hello
    function f1() { console.log('hello') }
    // f2 不被提升
    f2();    //Uncaught TypeError TypeError: f2 is not a function
    var f2 = function () { console.log('world') };
    ```

## 2.7. 运算符

### 2.7.1. 一般运算符
* 算术运算符 (均支持 `运算=`)
    运算符 | 含义  | 实例
    :----: | :---: | :-----------------
    `+`    | 正    | +1.2, +0
    `-`    | 负    | -3.4, -0
    `+`    | 加    | 1 + 3 => 4
    `-`    | 减    | 5.3 - 3.2 => 2.0999999999999996
    `*`    | 乘    | 2 * 3 => 6
    `/`    | 除    | 7 / 2 => 3.5
    `**`   | 幂 (ES2016) | 2 ** 3 => 8
    `%`    | 取余  | 5 % 2 => 1

    * 使用`+`对数值和字符串相加时, 数值会自动转换, `字符串 + 变量` 或 `变量 + 字符串` 根据情况, 略有区别
        * `+`的结合性是从左到右
        ```js
        '3' + 4 + 5 // "345"
        3 + 4 + '5' // "75"
        ```
    * `%` 的正负号由前边的数决定
    * `%` 还可以用于浮点数的运算, 但由于浮点数不是精确的值, 无法得到完全准确的结果
        ```js
        +7 % +2     // 1
        +7 % -2     // 1
        -7 % +2     // -1
        -7 % -2     // -1
        6.5 % 2.1   // 0.19999999999999973
        ```
* 自增和自减
    运算符   | 含义          | 实例
    :------: | :-----------: | :-----------------
    `变量++` | 先返回, 后加1 | var a = 1; console.log(a++); // 输出: 1
    `++变量` | 先加1, 后返回 | var a = 1; console.log(++a); // 输出: 2
    `变量--` | 先返回, 后减1 | var a = 1; console.log(a--); // 输出: 1
    `--变量` | 先减1, 后返回 | var a = 1; console.log(--a); // 输出: 0
* 赋值运算符
    表达方式        | 含义                       | 实例
    :-------------: | -------------------------- | ---------------
    `=`             | "引用"一个值               | a = 3
    `+=`, `-=`, ... | 先运算, 后赋值             | a += 1
* 比较运算符
    运算符 | 描述             | 实例
    :----: | :--------------: | :-----------------
    `==`   | 相等 ?           | (1 == 2) => false
    `===`  | 类型和值全相等 ? | 对于值类型, 比较值; 其它类型, 比较指向地址, 见实例
    `!=`   | 不等 ?           | (1 != 2) => true
    `!==`  | 类型和值不全等 ? | 对于值类型, 比较值; 其它类型, 比较指向地址, 见实例
    '`>`   | 大于 ?           | (1 > 2) => false
    `<`    | 小于 ?           | (1 < 2) => true
    `>=`   | 大于等于 ?       | (1 >= 2) => false
    `<=`   | 小于等于 ?       | (1 <= 1) => true

    * 等/全等:
        * 尽量使用`===`代替`==`, 因为结果可能不一致, 如
            ```js
            // 下面是两个对象的比较, 由于它们都引用了相同的地址, 所以返回 true
            var a = {};
            var b = a;
            console.log(a === b);  // 返回 true
            // 下面两个对象虽然结构相同, 但是地址不同, 所以不全等
            var a = {};
            var b = {};
            console.log(a === b);  // 返回 false
            // 对于复合型对象, 主要比较引用的地址, 不比较对象的值
            var a = new String("abcd"); //定义字符串  "abcd"  对象
            var b = new String("abcd"); //定义字符串  "abcd"  对象
            console.log(a === b);       //返回 false
            console.log(a == b);        //返回 false
            // 在上面示例中, 两个对象的值相等, 但是引用地址不同, 所以它们既不想等, 也不全等
            // 因此, 对于复合型对象来说, 相等==和全等===运算的结果是相同的
            ```
        * [ES6] `Object.is` 与 `===` 基本一致, 例外:
            ```js
            Object.is(+0, -0)   // false
            Object.is(NaN, NaN) // true
            ```
* 位运算符 (均支持 `运算=`)
    运算符 | 描述       | 实例
    :----: | :--------: | ---------------------
    `&`    | 按位与     | 0b1100 & 0b0101 => 0b0100
    `\|`   | 按位或     | 0b1100 \| 0b0101 => 0b1101
    `~`    | 按位取反   | ~0b1100 => 0b0011
    '`^`   | 按位异或   | 0b1100 ^ 0b0101 => 0b1001
    `<<`   | 左移       | 0xff << 2 => 0x3fc
    `>>`   | 右移       | 0xff >> 2 => 0x3f
    `>>>`  | 无符号右移 | -1 >>> 2 => 0x3fffffff
* 逻辑运算符
    运算符 | 描述   | 实例
    :----: | :----: | :-----------
    `&&`   | 逻辑与 | true && false => false
    `||`   | 逻辑或 | true \|\| false => true
    `!`    | 逻辑非 | ! true = false
* 三元操作
    ```js
    逻辑表达式 ? 真值对应的表达式 : 假值对应的表达式
    ```
    如
    ```js
    console.log(1 > 2 ? "对" : "错");   // 输出: 错
    ```

### 2.7.2. 特殊运算符
* **`new`**: 创建一个对象变量
    ```js
    变量 = new 对象([参数列表])
    ```
* **`in`**: 属性是否存在于对象
    ```js
    属性 in 对象
    属性 in (对象)
    ```
    * 检查的是键名, 不是键值
    * 不区分哪些属性是对象自身的, 哪些是继承的, 可以使用对象的 `hasOwnProperty` 方法判断是否为对象自身的属性

    如
    ```js
    var obj = { p: 1 };

    console.log("p" in obj)                     // true
    console.log('toString' in obj)              // true
    console.log(obj.hasOwnProperty('toString')) // false
    ```
* **`instanceof`**: 变量是否为某个对象的例化
    ```js
    变量 instanceof 对象
    变量 instanceof (对象)
    ```
* **`typeof`**: 返回变量的数据类型
    ```js
    typeof 变量
    typeof (变量)
    ```
* **`void`**: 执行一个表达式, 但不返回任何值, 或者说返回 `undefined`
    ```js
    void 表达式
    void(表达式) // 建议使用此方式, 因此优先级高, 容易漏掉后半句表达式, 如 void 4 + 7 实际上等同于 (void 4) + 7
    ```

    如
    ```js
    console.log(1 + 1)          // 输出: 2
    console.log(void (1 + 1))   // 输出: undefined
    ```
    * 主要用途是浏览器的书签工具 (Bookmarklet) , 以及在超级链接中插入代码防止网页跳转
        ```html
        <a href="javascript: void(f())">文字</a>
        ```
* **`...`**: 扩展运算符, 解构变量 (ES2018)
    * 将多个变量赋值给一个对象
        ```js
        (参数1, 参数2, ... rest 参数)   // 传参时, 其余参数传到 rest变量
        [变量1, 变量2, ... rest 变量] = 数组
        {属性1, 属性2, ... rest 属性} = 对象
        ```
    * 将可枚举对象 (数组, 字符串, Map, Set, ...) 解构, 变成逗号隔离的一系列变量
        ```js
        [变量1, 变量2, ..., 变量n] = ... 可枚举对象
        {属性1, 属性2, ..., 属性n} = ... 可枚举对象
        ```
    * 应用
        * 声明函数时作为 `rest` 参数 (形式为`...变量名`)
        * 传参: 将一个数组转为用逗号分隔的参数序列, 如
            ```js
            console.log(...[1, 2, 3])       // 1 2 3
            console.log(1, ...[2, 3, 4], 5) // 1 2 3 4 5
            ```
            * 注意: 只有函数调用时, 扩展运算符才可以放在圆括号中, 否则会报错
        * 克隆数组
            ```js
            目标数组变量 = [...被克隆的数组变量]
            [...目标数组变量] = 被克隆的数组变量
            ```
        * 合并数组 (浅拷贝)
            ```js
            [...数组1, ...数组2, ...数组3]
            ```
        * 与解构赋值结合使用
            ```js
            [变量1, ...其余变量] = 列表
            ```
        * 将任何定义了遍历器 (`Iterator`) 接口的对象转为真正的数组
            ```js
            数组变量 = [...可迭代对象]
            ```
* **`?.`**: [ES2020] "链判断运算符" (optional chaining operator), 在链式调用时判断左侧对象是否为`null`或`undefined`, 如果是就不再运算, 并返回`undefined`
    * 有三种写法
        * `对象?.属性`: 对象属性是否存在
        * `对象?.[表达式]`: 对象属性是否存在
        * `函数?.(参数列表)`: 函数或对象方法是否存在

    如
    ```js
    let hex = "#C0FFEE".match(/#([A-Z]+)/i)?.[1];

    a?.b    // 等同于
    a == null ? undefined : a.b

    a?.[x]  // 等同于
    a == null ? undefined : a[x]

    a?.b()  // 等同于
    a == null ? undefined : a.b()

    a?.()   // 等同于
    a == null ? undefined : a()
    ```
* **`??`**: [ES2020] Null 判断运算符, 跟链判断运算符`?.`配合使用, 为`null`或`undefined`的值设置默认值

    如
    ```js
    const enable = obj.enabled ?? true;
    ```
* **`,`**: 用于两个表达式, 执行两个表达式, 并返回后一个的值
    ```js
    表达式1, 表达式2    // 返回表达式2 的值
    ```

    如
    ```js
    var value = (console.log('Hi!'), true); // Hi!
    console.log(value)                      // true
    ```

### 2.7.3. 运算符优先级和结合性
优先级  | 运算符类型            | 结合性        | 运算符
:-----: | :-------------------: | :-----------: | :----:
21      | 圆括号                | n/a (不相关)  | `(`...`)`
20      | 属性访问              | 从左到右      | 对象`.`属性
^       | 需计算的属性访问      | 从左到右      | 对象`[`属性`]`
^       | `new` (带参数列表)    | n/a           | `new` 对象 `(`参数列表`)`
^       | 函数调用              | 从左到右      | 函数 `(`参数列表`)`
^       | 链判断运算符          | 从左到右      | 对象`?.`属性或方法
19      | `new` (无参数列表)    | 从右到左      | `new` 对象()
18      | 后置递增/减           | n/a           | 变量 `++`/`--`
17      | 逻辑非 (!)            | 从右到左      | `!` 逻辑表达式
^       | 按位非 (~)            | ^             | `~` 逻辑表达式
^       | 一元加/减法 (+/-)     | ^             | `+`/`-` 变量
^       | 前置递增/减           | ^             | `++`/`--` 变量
^       | `typeof`              | ^             | `typeof` 变量
^       | `void`                | ^             | `void` 表达式
^       | `delete`              | ^             | `delete` 变量
^       | `await`               | ^             | `await` 函数变量
16      | 幂 (**)               | 从右到左      | 变量1 `**` 变量2
15      | 乘法触发 (`*`/`/`)    | 从左到右      | 变量1 `*`/`/` 变量2
^       | 取余 (%)              | ^             | 变量1 `%` 变量2
14      | 加减法 (+/-)          | 从左到右      | 变量1 `+`/`-` 变量2
13      | 按位左/右移 (<</>>)   | 从左到右      | 变量1 `<<`/`>>` 变量2
^       | 无符号右移 (>>>)      | ^             | 变量1 `>>>` 变量2
12      | 大小比较 (</<=/>/>=)  | 从左到右      | 变量1 `<`/`<=`/`>`/`>=` 变量2
^       | `in`                  | ^             | 属性 `in` 对象
^       | `instanceof`          | ^             | 变量 `instanceof` 对象
11      | 相等比较 (\==/!=/\=\==/!==)  | 从左到右  | 变量1 `==`/`!=`/`===`/`!==` 变量2
10      | 按位与 (&)            | 从左到右      | 变量1 `&` 变量2
9       | 按位异或 (^)          | 从左到右      | 变量1 `^` 变量2
8       | 按位或 (\|)           | 从左到右      | 变量1 `|` 变量2
7       | 逻辑与 (&&)           | 从左到右      | 逻辑表达式1 `&&` 逻辑表达式2
6       | 逻辑或 (\|\|)         | 从左到右      | 逻辑表达式1 `||` 逻辑表达式2
5       | 空值合并 (??)         | 从左到右      | 变量1 `??` 变量2
4       | 条件 (三元) 运算符    | 从右到左      | 逻辑表达式 `?` 真值对应的表达式 `:` 假值对应的表达式
3       | 赋值                  | 从右到左      | 变量 `=`/`(运算)=` 值
2       | `yield`/`yield*`      | 从右到左      | `yield`/`yield*` ...
1       |  逗号/序列            | 从左到右      | 表达式1`,` 表达式2`,` ...

## 2.8. 条件控制
* **if...else...**
    ```js
    if (条件表达式) {
        代码块
    } else {
        代码块
    }
    ```
* **if...else if...else...**
    ```js
    if (条件表达式 1) {
        代码块
    } else if (条件表达式 2) {
        代码块
    }
    ...
    else if (条件表达式 n) {
        代码块
    } else {
        代码块
    }
    ```
* **switch...case...break...default...**
    ```js
    switch (表达式){
        case 值 1:
            代码块
            break;  // 可选, 如果没有, 回执行后续代码, 直到 break
        case 值 2:
            代码块
            break; // 可选
        ....
        case 值 n:
            代码块
            break;  // 可选
        default :   // 可选, 可以在任意位置, 但不在最后时注意是否需要 break
            代码块  // 如果没有与表达式相同的值, 则执行该代码
    }
    ```

## 2.9. 循环控制
* **while...**
    ```js
    while (条件表达式) {
        代码块
    }
    ```
* **do...while...**
    ```js
    do {
        代码块
    } while (条件表达式);
    ```
* **for...**
    ```js
    for(初始化; 条件表达式; 增量) {
        代码块
    }
    ```
    * 最好配合使用 `let`, 如
        ```js
        for (let i = 0; i < 5; i++) {
            console.log(i);
        }
        ```
* **for...in...**
    ```js
    for (变量 in 对象) {
        代码块
    }
    ```
    * 仅遍历可枚举 (enumerable) 的属性, 跳过不可枚举的属性
    * 不仅遍历对象自身的属性, 还遍历继承的属性
        * 若只想遍历自身的属性, 可以结合 `hasOwnProperty` 方法, 在循环内部判断一下
    * 数组也是对象, 但 `for...in` 用于数组时, 遍历其索引
        * 可以使用 `.forEach()` 方法
        ```js
        var arr = [1, 2, 3]
        arr[4] = 5     // 4 号是空位
        for (i in arr) {                                // i 是索引
            console.log("arr [" + i + "] =", arr[i]);   // arr[i] 是值
        }
        // 输出:
        // arr [ 0 ] =  1
        // arr [ 1 ] =  2
        // arr [ 2 ] =  3
        // arr [ 4 ] =  5
        arr.forEach(function (a) { console.log(a) });
        // 输出:
        // 1
        // 2
        // 3
        // 5
        ```
    * 最好配合使用 `let`
* **for...of...**
    ```js
    for (变量 of 可迭代变量) {  // 如数组, 字符串, ...
        代码块
    }
    ```
    * 可迭代对象: 数组, ...
    * 最好配合使用 `let`

    如
    ```js
    var arr = [1, 2, 3]
    arr[4] = 5     // 4 号是空位
    for (i of arr) {
        console.log(i);
    }
    // 输出:
    // 1
    // 2
    // 3
    // undefined
    // 5
    ```
* 循环控制:
    * `break`: 跳出循环
    * `continue`: 立即进入下次循环
    * 可与标签配合使用, 为了代码可读性, 建议不使用
        ```js
        top:
        for (var i = 0; i < 3; i++) {
            for (var j = 0; j < 3; j++) {
                if (i === 1 && j === 1) break top;
                console.log('i=' + i + ', j=' + j);
            }
        }
        // 输出:
        // i=0, j=0
        // i=0, j=1
        // i=0, j=2
        // i=1, j=0
        ```
        ```js
        foo: {
            console.log(1);
            break foo;
            console.log('本行不会输出');
        }
        console.log(2);
        // 输出:
        // 1
        // 2
        ```
        ```js
        top:
        for (var i = 0; i < 3; i++) {
            for (var j = 0; j < 3; j++) {
                if (i === 1 && j === 1) continue top;
                console.log('i=' + i + ', j=' + j);
            }
        }
        ```

## 2.10. 函数

### 2.10.1. 函数的声明
* 语法
    ```js
    function 函数名(形参列表){  // 最多 255 个参数, 可设默认值
        函数体
        [return 返回值;]
    }
    ```
* 参数不是必须的, 可以省略, 如
    ```js
    function f(a, b) {
        return a;
    }
    console.log(f(1, 2, 3));    // 输出: 1
    console.log(f(1));          // 输出: 1
    console.log(f());           // 输出: undefined
    console.log(f.length);      // 输出: 2
    ```
* [ES6] 可以在声明时设置参数默认值, 调用时可不设置参数
    * 参数默认值可以与解构赋值的默认值结合起来使用
    * 参数默认值的位置应该在末尾
    * 指定默认值以后`length`属性将返回没有指定默认值的参数个数, 也就是说, `length`属性将失真
    * 默认参数是每次调用函数时重新计算的, 因此可以此实现: 指定某一个参数不得省略, 如果省略就抛出一个错误

    如
    ```js
    function foo(x, y = 5) { console.log(x, y) }
    foo()       // 输出: undefined 5
    foo(1)      // 输出: 1 5
    foo(1, 2)   // 输出:  1 2

    // 解构赋值
    function foo({ x, y = 5 }) {console.log(x, y)}
    foo({})             // undefined 5
    foo({ x: 1 })       // 1 5
    foo({ x: 1, y: 2 }) // 1 2
    foo()   // TypeError: Cannot read property 'x' of undefined

    // 指定参数不得省略
    function throwIfMissing() {
        throw new Error('Missing parameter');
    }
    function foo(mustBeProvided = throwIfMissing()) {
        return mustBeProvided;
    }
    foo()   // Error: Missing parameter
    ```
* 参数在函数内部用 `arguments` 对象管理, 包含了函数调用的参数 "数组" (形似数组, 但不能 `for` 遍历)
    * 非严格模式下, 可在运行时修改

    如
    ```js
    var f = function (one) {
        console.log(one);
        console.log(arguments[1]);
        arguments[2] = 4;
        console.log(arguments[2]);
    }

    f(1, 2, 3)
    // 输出: 1
    // 输出: 2
    // 输出: 4
    ```
* [ES6] `rest` 参数 (形式为`...变量名`)
    * 用于获取函数的多余参数, 放入数组中
    * `rest` 参数必须在末尾

    如
    ```js
    function f(...values) {
        for (let i of values){
            console.log(i);
        }
    }

    f(1,2,3)
    // 1
    // 2
    // 3
    ```
* `return 返回值`
    * 可以是任何类型
* 如果函数多次声明, 会覆盖前面的

### 2.10.2. 函数的调用
* 语法
    ```js
    函数名(实参列表);
    返回值 = 函数名(实参列表);
    ```
* 参数传递: 顺序需一致, 默认参数可以不传参
    * 无法省略靠前的参数, 可以显式传入 `undefined`
* 值类型的数据 (如: `number`, `string`, `boolean`, ...) 是值传递, 其它是引用传递
* 支持**递归**调用
* **立即调用**的函数表达式 (IIFE)
    > 块级作用域的出现, 实际上使得 IIFE 不再必要了
    * 声明函数时直接在最后添加 `()`
        ```js
        (function () {
            代码块
        })();
        ```
    * 但 `function` 关键词不能出现在句首
    * 一般只对匿名函数使用此种调用, 好处:
        * 不必分配函数名, 避免污染全局变量
        * 形成一个单独的作用域, 封装一些外部无法读取的私有变量

    如
    ```js
    var f = function f() { return 1 }();

    // function 关键词不能出现在句首
    (function () { console.log("hello") }());
    !function () { console.log("hello") }();
    ~function () { console.log("hello") }();
    -function () { console.log("hello") }();
    +function () { console.log("hello") }();

    // 封装私有变量
    (function () {
        var tmp = newData;
        processData(tmp);
        storeData(tmp);
    }());
    // 等效于
    {
        let tmp = newData;
        processData(tmp);
        storeData(tmp);
    }
    ```
* 函数可以作为值使用, 如:
    ```js
    function myFunction(a, b) {
        return a * b;
    }
    var x = myFunction(4, 3) * 2;
    ```

### 2.10.3. 函数表达式
* 与声明变量相似, 语法格式:
    ```js
    var 变量 = function [函数名](参数列表){  // 最多 255 个参数
        函数体
        [return 返回值;]
    };  // 必须有分号
    ```
    * 函数名仅在函数内有效, 函数外无效
    * 函数名可以省略而会成为一个匿名函数, 如:
        ```js
        // 函数声明
        function getSum(num1, num2) {
            var total = num1 + num2;
            return total;
        }   // 无需分号, 有也不会报错
        // 函数表达式
        var getSum = function(num1, num2) {
            var total = num1 + num2;
            return total;
        };  //! 必须有分号
        ```
* 函数声明和函数表达式虽然非常相似, 但运行方式不同, 如:
    ```js
    declaration();  // 可以提升, 输出: function declaration
    function declaration() {
        console.log("function declaration");
    }
    expression();   // 不可提升, 报错: Uncaught TypeError: undefined is not a function
    var expression = function() {
        console.log("function expression");
    };
    ```

### 2.10.4. Function 对象
* 函数的类型是 `Function` 对象
* 创建:
    ```js
    var 函数变量 = new Function(参数列表);
    var 函数变量 = Function(参数列表);
    var 函数变量 = new 已有函数(参数列表);
    ```

    如:
    ```js
    var myFunction = new Function("a", "b", "return a * b");    // 也可以不用 new 关键词
    var x = myFunction(4, 3);
    ```
    ```js
    function myFunction(arg1, arg2) {
        this.firstName = arg1;
        this.lastName = arg2;
    }

    var x = new myFunction("John", "Doe");
    console.log(x.firstName);   // 输出: John
    ```
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    .name                   | 返回函数的名字, 如果是匿名函数则返回 "anonymous"
    .length                 | 预期传入的参数个数
* 静态方法
    * `Function.call(对象[, 参数列表])`: 指定函数内部`this`的指向 (即函数执行时所在的作用域), 然后在所指定的作用域中, 调用该函数
        * 参数应该是一个对象, 参数为空, `null`和`undefined`, 则默认传入全局对象
        * 如果参数是一个原始值, 会自动转成对应的包装对象, 然后传入`call`
    * `Function.apply(对象, 参数数组)`
        * 与`call`方法类似, 也是改变`this`指向, 然后再调用该函数
        * 区别: 接收一个数组作为函数执行时的参数
    * `Function.bind(对象[, 参数列表])`: 将函数体内的`this`绑定到某个对象, 然后返回一个新函数
        * 每运行一次, 就返回一个新函数
        * 结合回调函数使用
        * 结合`call()`方法使用

### 2.10.5. 箭头函数 (ES6)
* 比普通函数表达式更简洁, 语法:
    ```js
    (参数列表) => { 函数声明 }
    (参数列表) => 一句表达式    // 相当于: (参数列表) => { return 表达式; }
    // 只有一个参数时, 圆括号是可选的
    (单一参数) => {函数声明}
    单一参数 => {函数声明}
    // 没有参数时, 仅保留圆括号
    () => {函数声明}
    ```

    如:
    ```js
    // ES5
    var x = function(x, y) {
        return x * y;
    }
    // ES6
    const x = (x, y) => x * y;
    ```
* 注意:
    * 箭头函数没有自己的`this`, 不适合定义一个对象的方法
    * 使用箭头函数的时候, 箭头函数会默认绑定外层`this`的值, 所以在箭头函数中`this`的值和外层的`this`是一样的
    * 不可以当作构造函数
    * 不可以使用`arguments`对象, 该对象在函数体内不存在
    * 不可以使用`yield`命令, 因此箭头函数不能用作 `Generator` 函数
    * 箭头函数是不能提升的, 所以需要在使用之前定义
    * 使用`const`比使用`var`更安全, 因为函数表达式始终是一个常量
    * 如果函数部分只是一个语句, 则可以省略`return`关键字和大括号`{}`, 这是一个好习惯
        ```js
        const x = (x, y) => x * y;  // 等效于
        const x = (x, y) => { return x * y };
        ```

### 2.10.6. 闭包
* 嵌套在函数中的函数, 如
    ```js
    function funOne() {     // 外部函数
        var num = 0;        // 局部变量
        function funTwo() { // 内部函数
            num++;
            return num;
        }
        return funTwo;
    }
    var fun = funOne();     // 返回函数 funTwo
    ```
* 使函数拥有 "私有" 变量
    * 与 JavaScript 的垃圾回收机制有关, 如果一个对象不再被引用, 那么这个对象就会被 GC 回收, 否则这个对象会一直保存在内存中
        如: 内部函数 funTwo() 定义在外部函数 funOne() 中, 因此 funTwo() 依赖于 funOne(), 而全局变量 fun 又引用了 funTwo(), 所以 funOne() 间接的被 fun 引用
    * 当需要在函数中定义一些变量, 并且希望这些变量能够一直保存在内存中, 同时不影响函数外的全局变量时, 就可以使用闭包
* 在实际开发中, 通常会将闭包与匿名函数结合使用, 如:
    ```js
    var funOne = (function () {
        var num = 0;
        return function () {
            num++;
            return num;
        }
    })();
    console.log(funOne());  // 输出: 1
    console.log(funOne());  // 输出: 2
    console.log(funOne());  // 输出: 3
    ```
* 同一个闭包机制可以创建多个闭包函数, 彼此独立, 如:
    ```js
    function funOne(i) {
        return function () { console.log('数字: ' + i) };   // 匿名闭包函数
    };

    var fa = funOne(110);
    var fb = funOne(111);
    var fc = funOne(112);
    fa();       // 输出: 数字: 110
    fb();       // 输出: 数字: 111
    fc();       // 输出: 数字: 112
    ```
### 2.10.7. 全局 eval() 函数
* 接受一个字符串作为参数, 并将这个字符串当作语句执行
* 尽量不使用

## 2.11. 作用域

### 2.11.1. 作用域类型
* 全局作用域
    * 可在当前脚本的任意位置访问
    * 一般情况下拥有以下特征的变量具有全局作用域:
        * 最外层的函数, 以及最外层函数外定义的变量
        * 所有未定义直接赋值的变量
        * 所有 window 对象的属性, 例如 `window.name`, `window.location`, `window.top` 等
* 局部作用域
    * 在函数内部声明的变量, 只能在函数内使用, 函数执行完毕后会被立即销毁
* 块作用域 (ES6)
    * `{...}` 之间的作用域
    * 应该避免在块级作用域内声明函数, 如果确实需要, 应该写成函数表达式, 而不是函数声明语句

### 2.11.2. 注意事项
* 函数本身的作用域
    * 函数本身也是一个值, 也有其作用域, 是其声明时所在的作用域, 与其运行时所在的作用域无关
    * 实例
        ```js
        var a = 1;
        var x = function () {
            console.log(a);
        };

        function f() {
            var a = 2;
            x();    // x() 的作用域在外层
        }

        f()     // 输出: 1
        ```

## 2.12. 对象

### 2.12.1. 创建
* 语法
    ```js
    // 通过字母量创建
    var 对象 = {
        属性或方法1 : 值或函数1,
        [属性或方法表达式2] : 值或函数2,    // ES6 支持创建对象时使用属性表达式
        ...
        属性或方法n : 值或函数n
    }

    // 通过 new 创建
    var 对象变量 = new Object(可选参数)
    ```
    * 键 (根据值的类型也可以叫做属性或方法) 必须是 `String` 或 `Symbol`, 值则可以是任意数据类型
        * 创建时, 键可以不加引号, 除非
            * 属性名为 JavaScript 中的保留字
            * 属性名中包含空格或特殊字符
        * 键会自动被转为字符串
        * 使用`Symbol`值必须放在方括号之中
    * 允许属性的 "后绑定", 可以在任意时刻新增属性或方法
    * [ES6] 支持创建对象时使用属性表达式

    如:
    ```js
    var person = {
        name: "Peter",
        gender: "Male",
        "current age": 28,
        2022: "今年",
        [2022 + 1]: "明年", // 属性名表达式
        displayName: function () {
            console.log(this.name);
        }
    };
    person.isDied = true    // 后绑定
    ```
* [ES6] 属性的简洁表示法: 允许在大括号里面, 直接写入变量和函数, 作为对象的属性和方法
    * 但简洁写法不能用于构造函数
    * 创建对象时, 简洁表示和属性表达式不能同时出现

    如
    ```js
    const foo = 'bar';
    const baz = { foo }; // 属性的简洁表示
    // 等同于
    const baz = {foo: foo};

    console.log(baz);   // {foo: "bar"}

    ////////////////////////////////////////
    const o = {
        method() {      // 方法的简洁表示
            return "Hello!";
        }
    };
    // 等同于
    const o = {
        method: function () {
            return "Hello!";
        }
    };

    o.method()  // "Hello!"
    ```

### 2.12.2. 属性
* **访问属性**
    ```js
    // 方式 1: 点方法
    对象名.属性 // 如果属性名中包含空格或者特殊字符, 则不适用
    // 方式 2: 方括号方式, 更加灵活
    对象名[属性名(字符串, 等效的变量或表达式)]
    ```
    * `Symbol`值作为对象属性名时, 不能用`.`运算符

    如:
    ```js
    var person = {
        name: "Peter",
        gender: "Male",
        "current age": 28,
        2022: "今年",
        displayName: function () {   //
            console.log(this.name);
        }
    };
    person.isDied = true

    console.log(person.name);                 // 输出: Peter
    console.log(person["gender"]);            // 输出: Male
    console.log(person["current " + "age"]);  // 输出: 28
    console.log(person[2021 + 1]);            // 输出: 今年
    console.log(person.isDied);               // 输出: true
    ```
* **修改属性**
    ```js
    对象名.属性 = 新值
    对象名[属性名(字符串, 等效的变量或表达式)] = 新值
    ```
* **删除属性**
    ```js
    delete 对象名.属性
    delete 对象名[属性名(字符串, 等效的变量或表达式)]
    ```
    * 只有删除已存在且不得删除的属性时才返回 `false`
        * 删除不存在的属性时不报错, 且返回 `true`
    * 只能删除本身的属性, 无法删除继承的属性
* **`with`**: 操作同一个对象的多个属性
    ```js
    with (对象) {
        语句;
    }
    ```
    * 仅能操作已存在的属性, 否则会创造一个当前作用域的全局变量
    * 尽量不使用

    如:
    ```js
    var obj = {
        p1: 1,
        p2: 2,
    };
    with (obj) {
        p1 = 4;
        p2 = 5;
    }
    // 等同于
    obj.p1 = 4;
    obj.p2 = 5;
    ```
    ```js
    with (obj1.obj2.obj3) {
        console.log(p1 + p2);
    }
    // 可以写成
    var temp = obj1.obj2.obj3;
    console.log(temp.p1 + temp.p2);
    ```

### 2.12.3. 方法
```js
对象名.方法(实参列表)
对象名[方法(字符串, 等效的变量或表达式)](实参列表)
```

### 2.12.4. 深入理解对象

#### 2.12.4.1. 概述
* 所有的对象都有以下几个属性
    * `constructor`: 对创建对象的函数的引用 (指针)
        * 对于`Object`对象, 该指针指向原始的`Object()`函数
    * `prototype`: 对该对象的对象原型的引用
        * 对于所有的对象, 默认返回 `Object` 对象的一个实例
* `Object` 对象还具有几个方法
    * `hasOwnProperty(property)`: 判断对象是否有某个特定的属性, 必须用字符串指定该属性
    * `isPrototypeOf(object)`: 判断该对象是否为另一个对象的原型
    * `propertyIsEnumerable`: 判断给定的属性是否可以用`for...in`语句进行枚举
    * `toString()`: 返回对象的原始字符串表示, 对于 `Object` 对象, ECMA-262 没有定义这个值, 所以不同的 ECMAScript 实现具有不同的值
    * `valueOf()`: 返回最适合该对象的原始值, 对于许多对象, 该方法返回的值都与 `toString()` 的返回值相同

#### 2.12.4.2. property 对象
* 对象的每个属性都有对应的`attributes`对象, 以描述对象的属性, 控制它的行为
    * 每个`attributes`对象包含 6 个元属性
        * `[[value]]`: `property`的值, 默认为`undefined`
        * `[[writable]]`: 布尔值, 表示`[[value]]`是否可写, 默认为`true`
        * `[[enumerable]]`: 布尔值, 表示该属性是否可枚举, 默认为`true`
            * 如果设为`false`, 某些操作跳过该属性:
                * `for...in`循环: 只遍历对象自身的和继承的可枚举的属性
                * `Object.keys()`: 返回对象自身的所有可枚举的属性的键名
                * `Object.assign()`: 只拷贝对象自身的可枚举的属性
                * `JSON.stringify()`: 只串行化对象自身的可枚举的属性
            * 可以使用 `Object.prototype.propertyIsEnumerable(属性)` 查看`enumerable`
        * `[[configurable]]`: 布尔值, 表示属性的可配置性, 默认为`true`, 如果设为`false`, 将不可改写属性描述对象
            * 比如无法删除该属性, 也不得改变各种元属性 (`value`属性除外)
            * 即: `configurable`属性控制了属性描述对象的可写性
        * `[[get]]`: 函数, 表示该属性的取值函数 (`getter`), 默认为`undefined`
        * `[[set]]`: 函数, 表示该属性的存值函数 (`setter`), 默认为`undefined`

        如
        ```js
        {
            value: 123,
            writable: false,
            enumerable: true,
            configurable: false,
            get: undefined,
            set: undefined
        }
        ```
* `property` 对象的内部方法
    * `[[GetPrototypeOf]]`
    * `[[SetPrototypeOf]]`
    * `[[IsExtensible]]`
    * `[[PreventExtensions]]`
    * `[[GetOwnProperty]]`
    * `[[DefineOwnProperty]]`
    * `[[HasProperty]]`
    * `[[Get]]`
    * `[[Set]]`
    * `[[Delete]]`
    * `[[OwnPropertyKeys]]`
    * `[[Call]]`
    * `[[Construct]]`
* 获取属性描述对象
    * `Object.getOwnPropertyDescriptor()`
    * `Object.getOwnPropertyDescriptors()`
    * `Object.getOwnPropertyNames()`
    * `Object.getOwnPropertySymbols()`
* 修改属性描述对象
    * `Object.defineProperty(对象, 属性名, 属性描述对象)`
    * `Object.defineProperties(对象, 属性名, 属性描述对象)`

    如
    ```js
    var obj = Object.defineProperty({}, 'p', {
        value: 123,
        writable: false,
        enumerable: true,
        configurable: false
    });

    console.log(obj.p)          // 输出: 123
    console.log(obj.p) = 246;   // 修改对象
    console.log(obj.p)          // 输出: 123
    ```
* 存取器 `accessor`
    * `setter` 对应属性描述对象中的 `set` 方法
    * `getter` 对应属性描述对象中的 `get` 方法

    如
    ```js
    var obj = Object.defineProperty({}, 'p', {
        get: function () {
            return 'getter';
        },
        set: function (value) {
            console.log('setter: ' + value);
        }
    });

    obj.p       // "getter"
    obj.p = 123 // "setter: 123"

    // 更常用的写法
    var obj = {
        get p() {   // 不能接受参数
            return 'getter';
        },
        set p(value) {  // 只能接受参数 value
            console.log('setter: ' + value);
        }
    };
    ```
* 修改对象的状态
    * 三种冻结方法:
        * `Object.preventExtensions()`: 最弱, 使无法添加新属性
            * `Object.isExtensible()`: 查看此设置
        * `Object.seal()`: 使既无法添加新属性, 也无法删除旧属性, 但不影响修改某个属性
            * `Object.isSealed()`: 查看此设置
        * `Object.freeze()`: 使无法添加新属性, 无法删除旧属性, 也无法改变属性的值, 使这个对象实际上变成了常量
            * `Object.isFrozen()`: 查看此设置

#### 2.12.4.3. prototype 对象 (原型对象)
* 对象的原型, 被所有实例的对象共享
    * 修改之后, 所有实例对象的属性和方法都跟着变
* [ES6] 读取或设置当前对象的原型对象
    * `__proto__`属性: 读取或设置当前对象的原型对象
    * `Object.setPrototypeOf()`: 设置原型对象
    * `Object.getPrototypeOf()`: 读取原型对象

    如
    ```js
    function Animal(name) {
        this.name = name;
    }
    Animal.prototype.color = 'white';

    var cat1 = new Animal('大毛');
    var cat2 = new Animal('二毛');

    cat1.color  // 'white'
    cat2.color  // 'white'

    Animal.prototype.color = 'yellow';
    cat1.color  // "yellow"
    cat2.color  // "yellow"

    cat1.color = 'black';
    cat1.color  // 'black'
    cat2.color  // 'yellow'
    Animal.prototype.color  // 'yellow'
    ```

### 2.12.5. 元对象
* JavaScript 的所有其他对象都继承自`Object`对象, 都是`Object`的实例
* `Object(值)`: 将值转为对象, 如果参数是一个对象, 它总是返回该对象, 即不用转换
* `new Object(值)`: 构造一个新对象
    ```js
    var 变量 = new Object(参数);    // 不带参数
    // 等价写法
    var 变量 = {};
    ```
* `Object`对象的原生方法
    * 操作对象
        方法                    | 描述
        :---------------------- | :----------------------------
        `Object.create(O, Properties)`      | 用现有对象创建新对象
        `Object.assign(target, ...sources)` | 复制或组合对象
        `Object.fromEntries(iterable)`      | 用可迭代对象创建对象
        `Object.is(value1, value2)`         | 判断两个对象是否相同
    * 遍历对象
        方法                    | 描述
        :---------------------- | :----------------------------
        `Object.entries(O)`     | 遍历对象, 返回 `[属性, 值]` 的数组, 仅包含可枚举的属性
        `Object.keys(O)`        | 遍历对象的属性, 返回数组, 仅包含可枚举的属性
        `Object.values(O)`      | 遍历对象的值, 返回数组, 仅包含可枚举的值
    * `Property`对象相关
        方法                    | 描述
        :---------------------- | :----------------------------
        `Object.defineProperty(O, P, Attributes)`   | 通过描述对象, 添加一个属性
        `Object.defineProperties(O, Properties)`    | 通过描述对象, 添加多个属性
        `Object.getOwnPropertyDescriptor(O, P)`     | 获取`Property`
        `Object.getOwnPropertyDescriptors(O)`       | ^
        `Object.getOwnPropertyNames(O)`             | 遍历对象属性, 返回数组, 包含可枚举的属性和不可枚举的属性
        `Object.getOwnPropertySymbols(O)`           | ^
    * 控制或查看对象状态
        方法                    | 描述
        :---------------------- | :----------------------------
        `Object.preventExtensions(O)`   | 使既无法添加新属性, 也无法删除旧属性, 但不影响修改某个属性
        `Object.isExtensible(O)`        | 判断对象是否可扩展
        `Object.seal(O)`                | 使既无法添加新属性, 也无法删除旧属性, 但不影响修改某个属性
        `Object.isSealed(O)`            | 判断一个对象是否可配置
        `Object.freeze(O)`              | 使无法添加新属性, 无法删除旧属性, 也无法改变属性的值, 使这个对象实际上变成了常量
        `Object.isFrozen(O)`            | 判断一个对象是否被冻结
    * `prototype`对象 (原型链相关)
        方法                    | 描述
        :---------------------- | :----------------------------
        `Object.getPrototypeOf(O)`          | 获取对象的`prototype`
        `Object.setPrototypeOf(O, proto)`   | 设置对象的`prototype`
* `Object`对象的`prototype`对象的属性和方法
    * 属性:
        属性                    | 描述
        :---------------------- | :----------------------------
        `Object.prototype.constructor`  | 原型的构造函数, 其实就是 `Object` 元对象
    * 方法:
        方法                    | 描述
        :---------------------- | :----------------------------
        `Object.prototype.valueOf()`            | 返回当前对象对应的值, 默认情况下返回对象本身
        `Object.prototype.toString()`           | 返回当前对象对应的字符串形式, 可以对其进行改写
        `Object.prototype.toLocaleString([ reserved1 [ , reserved2 ] ])`    | 返回当前对象对应的本地字符串形式
        `Object.prototype.hasOwnProperty(V)`    | 判断某个属性是否为当前对象自身的属性, 还是继承自原型对象的属性
        `Object.prototype.isPrototypeOf(V)`     | 判断当前对象是否为另一个对象的原型
        `Object.prototype.propertyIsEnumerable(V)`  | 判断某个属性是否可枚举
    * 可以被`Object`的实例直接使用, 如
        ```js
        对象变量.toString()
        ```

## 2.13. 错误与异常

### 2.13.1. 错误类型
* 错误大致分三类:
    * **语法错误**: 也称为解析错误, 一般是因为代码存在某些语法错误引起的, 发生语法错误时, 代码会停止运行
    * **运行时错误**: 也称为**异常**, 发生在程序运行期间, 例如调用未定义的方法, 读取不存在的文件等, 发生运行时错误也会终止代码运行
    * **逻辑错误**: 是最难发现的一种错误, 逻辑错误通常是因为代码存在瑕疵, 导致程序输出意外的结果或终止运行

* JavaScript 原生提供`Error`实例对象
    * 属性
        * `message`: 错误提示信息
        * `name` (非标准属性): 错误名称
        * `stack` (非标准属性): 错误的堆栈
    * 支持构造`Error`
        ```js
        var err = new Error('出错了');
        err.message // "出错了"
        ```
    * 原生错误类型:
        错误类型        | 说明
        :-------------- | :---
        `SyntaxError`   | 语法错误
        `ReferenceError`| 参数错误, 引用一个不存在的变量
        `RangeError`    | 范围范围错误
        `TypeError`     | 类型错误, 使用的值不是预期类型, 例如对数字调用字符串方法, 对字符串调用数组方法等
        `URIError`      | URI 错误, URI 相关函数的参数不正确
        `EvalError`     | 使用 `eval()` 函数时发出错误
        `InternalError` | 由 JavaScript 引擎内部错误导致的异常
    * 自定义错误对象
        ```js
        function UserError(message) {
            this.message = message || '默认信息';
            this.name = 'UserError';
        }

        UserError.prototype = new Error();
        UserError.prototype.constructor = UserError;
        ```

### 2.13.2. 异常处理
* 捕捉产生异常的代码, 使整个程序不会因为异常而终止运行, 语法:
    ```js
    try {
        可能会发生异常的代码块
    } catch(Error对象) {    // [ES2019] catch 可以没有参数
        发生异常时要执行的操作
    } finally { // 可选项
        无论是否发生错误, 都会执行的代码块
    }
    ```

    如:
    ```js
    var num = prompt("输入一个 0 到 100 的数字");
    var start = Date.now();
    try {
        if (num > 0 && num <= 100) {
            console.log(Math.pow(num, num));
        } else {
            console.log("输入的值无效!");
        }
    } catch (e) {
        console.log(e.message);
    } finally {
        console.log("代码执行花费了: " + (Date.now() - start) + "ms");
    }
    ```

### 2.13.3. 产生异常
* JavaScript 解释器会自动抛出异常, 用户也可以手动抛出错误
    ```js
    // 某个代码块中
    {
        ...
        throw 异常; // 异常可以是任何类型的值, 如对象, 字符串, 数组等, 推荐使用对象类型
        ...
    }

    ```

    如:
    ```js
    function squareRoot(number) {
        if (number < 0) {
            throw new Error("无法计算负数的平方根！");
        } else {
            console.log(Math.sqrt(number));
        }
    }
    try {
        squareRoot(16);
        squareRoot(625);
        squareRoot(-9);
        // 若抛出错误, 则不会执行下面的行
        squareRoot(100);
        console.log("所有函数都执行成功");
    } catch (e) {
        // 处理错误
        console.log(e.message);
    }
    ```

## 2.14. 模块 (ES6)
* ES6 模块不是对象, 而是通过`export`命令显式指定输出的代码, 再通过`import`命令输入

### 2.14.1. export
* 用于规定模块的对外接口
* 语法
    ```js
    // 方式1
    export var 变量 = 值
    export function 函数(参数列表) { 代码块 };
    export class 类 { 代码块 };
    // 方式2
    export { 变量/函数/类 1, 变量/函数/类 2, ...};
    // 别名
    export {
        变量/函数/类 1 as 别名1,
        变量/函数/类 2 as 别名2,
        ...
        };
    ```
* 输出的接口与其对应的值是动态绑定关系, 即通过该接口可以取到模块内部实时的值, 如
    ```js
    export var foo = 'bar';
    setTimeout(() => foo = 'baz', 500); // 500 ms 后 foo 变成 "baz"
    ```
* 可以出现在模块的任何位置, 只要处于全局作用域即可
* `export default`命令用于指定模块的默认输出, 一个模块只能有一个默认输出
    * 可以导出匿名函数

### 2.14.2. import
* 用于输入其他模块提供的功能
* 语法
    ```js
    import {变量/函数/类 1, 变量/函数/类 2, ...} from 文件路径_字符串;
    import {
        变量/函数/类 1 as 别名1,
        变量/函数/类 2 as 别名2,
        ...
    } from 文件路径_字符串;

    // 导入所有
    import * from 文件路径_字符串;
    import * as 别名 from 文件路径_字符串;
    ```
* `import`的变量的名称须与`export`的相同
    * 对于`export default`的变量或函数, `import`可以使用任意名称导入
* 文件路径可以是相对路径, 也可以是绝对路径
    * 如果不带有路径, 只是一个模块名, 那么必须有配置文件, 告诉 JavaScript 引擎该模块的位置
* `import`命令具有提升效果, 会提升到整个模块的头部
* `import`命令是静态加载
    * `Node.js`使用`require`动态加载
* `import`语句会执行所加载的模块, 因此可以有下面的写法
    ```js
    import 模块;
    ```
    * 即便多次重复执行同一句`import`语句, 也只会执行一次

### 2.14.3. 转发接口
* `export`和`import`的符合写法
* 语法
    ```js
    export {变量/函数/类 1, 变量/函数/类 2, ...} from 文件路径_字符串;
    export {
        变量/函数/类 1 as 别名1,
        变量/函数/类 2 as 别名2,
        ...
    } from 文件路径_字符串;

    export * from 文件路径_字符串;          // 整体输出
    export * as 别名 from 文件路径_字符串;  // 整体输出

    // 可以简单理解为
    import { 变量/函数/类, ... } from 'my_module';
    export { 变量/函数/类, ... };
    ```
* 可以在转发时增加`export`


## 2.15. 输入/输出
* 依赖宿主

## 2.16. 调试
* 调试输出:
    * `console.log(输出内容)`
    * `console.assert(输出内容)`
    * `console.info/debug/warn/error(输出内容)`
    * `console.table(输出内容)`
    * 占位符
        * `%s`: 字符串
        * `%d`: 整数
        * `%i`: 整数
        * `%f`: 浮点数
        * `%o`: 对象的链接
        * `%c`: CSS 格式字符串
* 计时
    * `console.time(输出内容)`
    * `console.timeEnd(输出内容)`
* `debugger` 设置断点, 如
    ```js
    var x = 15 * 5;
    debugger;
    console.log(x);
    ```

## 2.17. 严格模式
* 在脚本或函数的开头添加 `"use strict";`
    * 在脚本开头进行声明, 拥有全局作用域 (脚本中的所有代码均以严格模式来执行)
* 严格模式下
    * 显示报错
        * 只读属性不可写
        * 只设置了取值器 (`getter`) 的属性不可写
        * 禁止扩展的对象不可扩展
        * `eval` 和 `arguments` 不可用作变量
        * 声明函数时, 参数名不允许重名
        * 禁止使用八进制数字
        * 禁止使用八进制转义字符 (`"\OOO"`)
    * 增强的安全措施
        * 全局变量显式声明, 不允许使用未声明的变量
        * 禁止 `this` 关键字指向全局对象
        * 禁止使用 `fn.callee`, `fn.caller`
        * 禁止使用 `arguments.callee`, `arguments.caller`
        * 禁止`delete`变量或函数
    * 静态绑定
        * 禁止使用 `with` 语句
        * 禁止 `eval()` 在其被调用的作用域中创建变量
        * `arguments` 不再追踪参数的变化
    * 向下一个版本过渡
        * 非函数代码块不得声明函数
        * 新增了一些保留字 (`implements`, `interface`, `let`, `package`, `private`, `protected`, `public`, `static`, `yield` 等)

--------------------------------------------------------------------------------
# 3. 面向对象编程

## 3.1. 构造器

### 3.1.1. 构造函数
* 构造函数的特点有两个
    * 函数体内部使用了`this`关键字, 代表了所要生成的对象实例
    * 生成对象的时候, 必须使用`new`命令
        * 否则函数被当作普通函数, `this`代表全局变量, 将造成一些意想不到的结果

    如
    ```js
    var Vehicle = function () { // 为了区分普通函数, 建议首字母大写
        this.price = 1000;
    };

    var v = new Vehicle();
    v.price // 1000
    ```

### 3.1.2. 构造对象的过程
* 使用`new`命令时, 它后面的函数依次执行下面的步骤
    * 创建一个空对象, 作为将要返回的对象实例
    * 将这个空对象的原型, 指向构造函数的`prototype`属性
    * 将这个空对象赋值给函数内部的`this`关键字
    * 开始执行构造函数内部的代码

### 3.1.3. constructor 属性
* 对象的`prototype`对象有一个`constructor`属性, 默认指向`prototype`对象所在的构造函数, 如
    ```js
    function P() { }
    var p = new P();

    p.constructor === P                         // true
    p.constructor === P.prototype.constructor   // true
    p.hasOwnProperty('constructor')             // false
    ```
* `constructor`属性的作用: 可以得知某个实例对象到底是哪一个构造函数产生的
* 有了`constructor`属性就可以从一个实例对象新建另一个实例
    ```js
    function Constr() { }
    var x = new Constr();

    var y = new x.constructor();
    y instanceof Constr // true
    ```
* `constructor`属性表示原型对象与构造函数之间的关联关系, 如果修改了原型对象, 一般会同时修改`constructor`属性, 防止引用的时候出错
    ```js
    // 坏的写法
    C.prototype = {
        method1: function (...) { ... },
        ...
    };

    // 好的写法
    C.prototype = {
        constructor: C,
        method1: function (...) { ... },
        ...
    };

    // 更好的写法
    C.prototype.method1 = function (...) { ... };
    ```

## 3.2. this
* `this`就是属性或方法 "当前" 所在的对象
    * 全局环境中: `this`指向顶层对象
        * 在严格模式下的函数中, `this`指向`undefined`
    * 构造函数中: `this`指向实例对象
        ```js
        function f() {
            return '姓名: ' + this.name;
        }

        var A = {
            name: '张三',
            describe: f
        };

        var B = {
            name: '李四',
            describe: f
        };

        A.describe()    // "姓名: 张三"
        B.describe()    // "姓名: 李四"
        ```
    * 对象的方法中: `this`指向其所在的对象
* 使用注意
    * 避免多层`this`
    * 避免数组处理方法中的 `this`
    * 避免回调函数中的`this`
* 绑定`this`的方法
    * `Function.call(对象[, 参数列表])`: 指定函数内部`this`的指向 (即函数执行时所在的作用域), 然后在所指定的作用域中, 调用该函数
        * 参数应该是一个对象, 参数为空, `null`和`undefined`, 则默认传入全局对象
        * 如果参数是一个原始值, 会自动转成对应的包装对象, 然后传入`call`
    * `Function.apply(对象, 参数数组)`
        * 与`call`方法类似, 也是改变`this`指向, 然后再调用该函数
        * 区别: 接收一个数组作为函数执行时的参数
    * `Function.bind(对象[, 参数列表])`: 将函数体内的`this`绑定到某个对象, 然后返回一个新函数
        * 每运行一次, 就返回一个新函数
        * 结合回调函数使用
        * 结合`call()`方法使用

## 3.3. 继承
* JavaScript 语言的继承通过 "原型对象" (`prototype`) 实现

### 3.3.1. 原型链
* 关于原型链
    * 任何一个对象, 都可以充当其他对象的原型
    * 由于原型对象也是对象, 所以它也有自己的原型
    * 因此, 就会形成一个 "原型链"  (prototype chain): 对象到原型, 再到原型的原型...
* 原型链的尽头
    * 所有对象的原型最终都可以上溯到`Object.prototype`, 即`Object`构造函数的`prototype`属性
        * 也就是说, 所有对象都继承了`Object.prototype`的属性, 这就是所有对象都有`valueOf`和`toString()`方法的原因
    * `Object.prototype`的原型是`null`, 即原型链的尽头就是`null`
        ```js
        Object.getPrototypeOf(Object.prototype) // null
        ```
* 读取对象的某个属性时, JavaScript 引擎先寻找对象本身的属性, 如果找不到, 就到它的原型去找, 如果还找不到, 就到原型的原型去找
    * 如果直到最顶层的`Object.prototype`还是找不到, 则返回`undefined`
* 如果对象自身和它的原型, 都定义了一个同名属性, 那么优先读取对象自身的属性, 这叫做 "覆盖"  (overriding)

### 3.3.2. 构造函数的继承
* 实现分两步
    1. 子类的构造函数中调用父类的构造函数
        ```js
        function Sub(value) {
            Super.call(this);
            this.prop = value;
        }
        ```
    1. 子类的原型指向父类的原型
        ```js
        Sub.prototype = Object.create(Super.prototype);
        Sub.prototype.constructor = Sub;
        Sub.prototype.method = '...';
        ```

### 3.3.3. 多重继承
* JavaScript 不提供多重继承功能, 即不允许一个对象同时继承多个对象, 但可以通过变通方法, 实现这个功能, 如
    ```js
    function M1() {
        this.hello = 'hello';
    }

    function M2() {
        this.world = 'world';
    }

    function S() {
        M1.call(this);
        M2.call(this);
    }

    // 继承 M1
    S.prototype = Object.create(M1.prototype);
    // 继承链上加入 M2
    Object.assign(S.prototype, M2.prototype);
    // 指定构造函数
    S.prototype.constructor = S;

    var s = new S();
    s.hello // 'hello'
    s.world // 'world'
    ```

## 3.4. class (ES6)
* 类不是对象, 只是对象的模板, `class`是 "语法糖"

### 3.4.1. 声明
* 必须在严格模式下, 才能声明
* 语法: `class` 关键词
    ```js
    class 类名 {
        属性 = 值;  // 推荐放在最开始
        constructor(参数列表){
            代码块
        };
        方法 (参数列表){
            代码块
        };
        get 方法 (参数列表){
            代码块
        };
        set 方法 (参数列表){
            代码块
        };
        方法 (参数列表){
            代码块
        };
        static 静态方法 (参数列表){
            代码块
        };
        ...
    }
    ```
* 构造方法
    * 名称必须是`constructor`
    * 例化新对象时自动执行
    * 用于初始化对象属性
        * 类的属性需要用 `this.` 表示
    * 如果没有定义构造方法, JavaScript 会添加一个空的构造方法
* 类方法
    * 创建类方法的语法与对象方法相同
        * 类的属性需要用 `this.` 表示
    * 支持`get`和`set`方法
* 静态方法: `static` 关键词
    * 在类本身上定义的, 不能在对象上调用, 只能用`类.方法`的方式调用
* 类不会被提升

### 3.4.2. 例化
* 语法
    ```js
    对象变量 = new 类名(参数列表)
    ```

### 3.4.3. 继承
* 语法: `extends` 关键词
    ```js
    class 子类 extends 父类 {
        constructor(子类的参数列表){
            super(父类的参数列表);    // 必须调用父类的构造方法
            代码块
        };
        属性: 值;
        方法: 函数;
        static 方法: 函数;
        ...
    }
    ```
* `super`
    * 作为对象, 作用是指向当前对象的原型对象
        * 在静态方法中, 指向父类, 而不是父类的例化对象
    * 作为函数`super()`, 作用是调用父类的构造函数, 只能用在子类的构造函数中

--------------------------------------------------------------------------------
# 4. 高级语法 (ES6)

## 4.1. Generator
* Generator 函数语法
    ```js
    function * 生成器函数名 (参数列表) {
        代码块

        // caller 调用后, 运行到 yield, 返回输出变量, 等到被继续调用, 再次调用后, 从 caller 输入变量

        // 情况 1: 不输出变量, 也不使用接收的变量
        yield
        // 情况 2: 输出变量, 但不使用接收的变量
        yield 输出变量或表达式
        // 情况 3: 不输出变量, 使用接收的变量
        let 输入变量 = yield
        // 情况 4: 输出变量, 也使用接收的变量
        let 输入变量 = yield 输出变量或表达式

        代码块
        return 返回值;
    }
    ```
* 调用
    * `函数对象.next(参数列表)`: 生成器函数执行到下一条`yield`语句或`return`语句, 并返回当前成员的值 (相当于将`yield`替换为一个值)
        * `value`: 当前成员的值
        * `done`: 遍历是否结束
    * `函数对象.throw(错误对象)`: 生成器函数执行到下一条`yield`语句或`return`语句, 并抛出错误 (相当于将`yield`替换`throw(错误对象)`)
    * `函数对象.return()`: 生成器函数执行到下一条`yield`语句或`return`语句, 并返回 (相当于将`yield`替换`return`)
    * `Iterator`方法:
        * 解构赋值
        * 扩展运算符
        * `yield*`
        * 其他场合, 如
            * `for...of`
            * `Array.from()`
            * `Map()`, `Set()`, `WeakMap()`, `WeakSet()`
            * `Promise.all()`
            * `Promise.race()`
* `for...of`循环: 自动调用生成器函数
    * 运行到`done`为`true`就停止, 且不包含该返回对象, 如
        ```js
        function* foo() {
            yield 1;
            yield 2;
            yield 3;
            yield 4;
            yield 5;
            return 6;
        }

        for (let v of foo()) { console.log(v); }
        // 输出
        // 1
        // 2
        // 3
        // 4
        // 5
        ```
* `yield*` 表达式
    * 用来在一个 `Generator` 函数里面执行另一个 `Generator` 函数
        * 实例
            ```js
            function* foo() {
                yield 'a';
                yield 'b';
            }

            function* bar() {
                yield 'x';
                yield* foo();
                yield 'y';
            }

            // 等同于
            function* bar() {
                yield 'x';
                yield 'a';
                yield 'b';
                yield 'y';
            }

            // 等同于
            function* bar() {
                yield 'x';
                for (let v of foo()) {
                    yield v;
                }
                yield 'y';
            }
            ```
    * 任何数据结构只要有`Iterator`接口, 就可以被`yield*`遍历, 如
        ```js
        let read = (function* () {
            yield 'hello';
            yield* 'hello';
        })();

        read.next().value // "hello"
        read.next().value // "h"
        ```
    * 如果被代理的 `Generator` 函数有`return`语句, 那么就可以向代理它的 `Generator` 函数返回数据, 如
        ```js
        function* foo() {
            yield 2;
            yield 3;
            return "foo";
        }

        function* bar() {
            yield 1;
            var v = yield* foo();
            console.log("v: " + v);
            yield 4;
        }

        var it = bar();

        it.next()   // {value: 1, done: false}
        it.next()   // {value: 2, done: false}
        it.next()   // {value: 3, done: false}
        it.next();  // "v: foo"
                    // {value: 4, done: false}
        it.next()   // {value: undefined, done: true}
        ```
* 作为对象属性的 Generator 函数, 可以简写成
    ```js
    let obj = {
        * 生成器方法名(参数列表){代码块};
    };
    ```
* 应用
    * 异步操作的同步化表达
    * 控制流管理
    * 部署 `Iterator` 接口
    * 作为数据结构

## 4.2. Iterator
* 为各种不同的数据结构提供统一的遍历机制, 遍历过程:
    1. 创建一个指针对象, 指向当前数据结构的起始位置
    1. 第一次调用指针对象的`next`方法, 可以将指针指向数据结构的第一个成员
    1. 第二次调用指针对象的`next`方法, 指针就指向数据结构的第二个成员
    1. 不断调用指针对象的`next`方法, 直到它指向数据结构的结束位置
* 默认`Iterator`接口: 部署在数据结构的`Symbol.iterator`属性
    * 一个数据结构只要具有`Symbol.iterator`属性, 就可以认为是 "可遍历的"
    * 原生具备`Iterator`接口的数据结构
        * `Array`
        * `Map`
        * `Set`
        * `String`
        * `TypedArray`
        * 函数的 `arguments` 对象
        * `NodeList` 对象
* 调用`Iterator`接口的场合
    * 解构赋值
    * 扩展运算符
    * `yield*`
    * 其他场合, 如
        * `for...of`
        * `Array.from()`
        * `Map()`, `Set()`, `WeakMap()`, `WeakSet()`
        * `Promise.all()`
        * `Promise.race()`


## 4.3. 异步操作

### 4.3.1. 概述
* 同步任务, 异步任务
* 任务队列和事件循环
* 异步操作的几种模式
    * 回调函数
    * 事件监听
    * "发布/订阅模式" (publish-subscribe pattern) , 又称 "观察者模式" (observer pattern)

### 4.3.2. 定时器
* JavaScript 提供定时执行代码的功能, 叫做定时器 (timer)
    * `setTimeout(函数或代码, 推迟执行的毫秒数)`
        * 指定某个函数或某段代码, 在多少毫秒之后执行
        * 返回一个整数, 表示定时器的编号, 可以用来取消这个定时器
        * `setTimeout(f, 0)`
            * 在下一轮事件循环一开始就执行
    * `setInterval(函数或代码, 推迟执行的毫秒数)`
        * 与`setTimeout`完全一致, 区别仅仅在于`setInterval`指定某个任务每隔一段时间就执行一次, 也就是无限次的定时执行
    * `clearTimeout()` 和 `clearInterval()`
        * 取消对应的定时器

### 4.3.3. Promise 对象
* `Promise` 对象包含生产代码和对消费代码的调用
* 实例
    ```js
    let promise对象 = new Promise(function (成功时的回调函数, 失败时的回调函数) {
        // 生成代码 (运行需要一些时间)

        成功时的回调函数;   // 成功时
        失败时的回调函数;   // 出错时
    });
    // 消费代码 (必须等待一个兑现的承诺)
    promise对象.then(
        function (成功时返回的值) { 成功时的代码 },
        function (失败时返回的错误对象) { 出错时的代码 }
    );
    ```
* `Promise`对象的状态
    * 状态有三个
        * Pending
        * Fulfilled
        * Rejected
    * 状态转移
        * Pending -> Fulfilled
        * Pending -> Rejected
* `Promise`对象支持两个属性
    myPromise.state | myPromise.result
    :-------------: | :---:
    "pending"       | `undefined`
    "fulfilled"     | 结果值
    "rejected"      | `error`对象

    * 用户无法访问 `state` 和 `result`
* `Promise`对象的方法
    * `.then(成功时的回调函数, 失败时的回调函数)`: 添加状态改变时的回调函数
    * `.catch(失败时的回调函数)`: 用于指定发生错误时的回调函数
    * `.finally()`: 不管最后状态如何, 都会执行的操作

### 4.3.4. async 和 await
* Generator 函数的语法糖
    * `async`函数就是将 Generator 函数的星号 (`*`) 替换成`async`, 将`yield`替换成`await`
    * 实例
        ```js
        const fs = require('fs');

        const readFile = function (fileName) {
            return new Promise(function (resolve, reject) {
                fs.readFile(fileName, function (error, data) {
                    if (error) return reject(error);
                    resolve(data);
                });
            });
        };

        // Generator 函数 写法
        const gen = function* () {
            const f1 = yield readFile('/etc/fstab');
            const f2 = yield readFile('/etc/shells');
            console.log(f1.toString());
            console.log(f2.toString());
        };

        // async 和 await 写法
        const asyncReadFile = async function () {
            const f1 = await readFile('/etc/fstab');
            const f2 = await readFile('/etc/shells');
            console.log(f1.toString());
            console.log(f2.toString());
        };
        ```
* `async`函数对 Generator 函数的改进, 体现在以下四点
    * 内置执行器: `async`函数自带执行器 (无需 `co` 模块)
    * 更好的语义: `async`表示函数里有异步操作, `await`表示紧跟在后面的表达式需要等待结果
    * 更广的适用性: `async`函数的`await`命令后面, 可以是 `Promise` 对象和原始类型的值 (数值、字符串和布尔值, 但这时会自动转成立即 resolved 的 Promise 对象)
    * 返回值是 `Promise`: 比 Generator 函数的返回值是 Iterator 对象方便

    如
    ```js
    function timeout(ms) {
        return new Promise(
            (resolve) => { setTimeout(resolve, ms) }
        );
    }
    // 另一种写法
    async function timeout(ms) {
        await new Promise(
            (resolve) => { setTimeout(resolve, ms) }
        );
    }
    async function asyncPrint(value, ms) {
        await timeout(ms);
        console.log(value);
    }

    asyncPrint('hello world', 50);
    ```
* 语法
    * `async`函数返回一个 `Promise` 对象
    * `async`函数内部`return`语句返回的值, 会成为`then`方法回调函数的参数, 如
        ```js
        async function f() {
            return 'hello world';
        }

        f().then(v => console.log(v))   // "hello world"
        ```
    * `async`函数内部抛出错误, 会导致返回的 Promise 对象变为`reject`状态, 抛出的错误对象会被catch`方法回调函数接收到, 如
        ```js
        async function f() {
            throw new Error('出错了');
        }

        f().then(
            v => console.log('resolve', v),
            e => console.log('reject', e)
        )
        //reject Error: 出错了
        ```
    * 正常情况下, `await`命令后面是一个 Promise 对象, 返回该对象的结果, 如果不是 Promise 对象, 就直接返回对应的值
* Promise 对象的状态变化
    * `async`函数返回的 Promise 对象, 必须等到内部所有`await`命令后面的 Promise 对象执行完, 才会发生状态改变, 除非遇到`return`语句或者抛出错误
        * 也就是说, 只有`async`函数内部的异步操作执行完, 才会执行`then`方法指定的回调函数
* 使用注意点
    * `await`命令后面的`Promise`对象, 运行结果可能是`rejected`, 所以最好把`await`命令放在`try...catch`代码块中
    * 多个`await`命令后面的异步操作, 如果不存在继发关系, 最好让它们同时触发
    * `await`命令只能用在`async`函数之中, 如果用在普通函数, 就会报错
    * `async` 函数可以保留运行堆栈

### 4.3.5. 异步遍历器
* 异步遍历器的最大的语法特点, 就是调用遍历器的`next`方法, 返回的是一个 Promise 对象
    ```js
    asyncIterator
        .next()
        .then(
            ({ value, done }) => /* ... */
    );
    ```
* 对象的异步遍历器接口, 部署在`Symbol.asyncIterator`属性上面
* 可用`for await...of`遍历
    * `for await...of`循环也可以用于同步遍历器

## 4.4. 二进制数组
* 由三类对象组成
    * `ArrayBuffer`对象: 代表内存之中的一段二进制数据, 可以通过 "视图" 进行操作。 "视图" 部署了数组接口, 这意味着, 可以用数组的方法操作内存
    * `TypedArray`视图: 共包括 9 种类型的视图, 比如`Uint8Array` (无符号 8 位整数) 数组视图, `Int16Array` (16 位整数) 数组视图, `Float32Array` (32 位浮点数) 数组视图等等
    * `DataView`视图: 可以自定义复合格式的视图, 比如第一个字节是 `Uint8` (无符号 8 位整数) 、第二、三个字节是 `Int16` (16 位整数) 、第四个字节开始是 `Float32` (32 位浮点数) 等等, 此外还可以自定义字节序
* 简单说, `ArrayBuffer`对象代表原始的二进制数据, `TypedArray`视图用来读写简单类型的二进制数据, `DataView`视图用来读写复杂类型的二进制数据
* `TypedArray`视图支持的数据类型一共有 9 种 (`DataView`视图支持除Uint8C以外的其他 8 种)
    数据类型 | 字节长度 | 含义                  | 对应的 C 语言类型
    :------: | :------: | :-------------------- | :----------------
    Int8     | 1        | 8 位带符号整数        | signed char
    Uint8    | 1        | 8 位不带符号整数      | unsigned char
    Uint8C   | 1        | 8 位不带符号整数 (自动过滤溢出) | unsigned char
    Int16    | 2        | 16 位带符号整数       | short
    Uint16   | 2        | 16 位不带符号整数     | unsigned short
    Int32    | 4        | 32 位带符号整数       | int
    Uint32   | 4        | 32 位不带符号的整数   | unsigned int
    Float32  | 4        | 32 位浮点数           | float
    Float64  | 8        | 64 位浮点数           | double

    * 注意, 二进制数组并不是真正的数组, 而是类似数组的对象

--------------------------------------------------------------------------------
# 5. 标准库

## 5.1. 概述
* 全局值
    * `globalThis`
    * `Infinity`
    * `NaN`
    * `undefined`
* 全局函数
    * `eval ( x )`
    * `isFinite ( number )`
    * `isNaN ( number )`
    * `parseFloat ( string )`
    * `parseInt ( string, radix )`
    * URI Handling Functions
        * `decodeURI ( encodedURI )`
        * `decodeURIComponent ( encodedURIComponent )`
        * `encodeURI ( uri )`
        * `encodeURIComponent ( uriComponent )`
* 全局对象 (构建器属性)
    * `Array`, `ArrayBuffer`
    * `BigInt`, `BigInt64Array`, `BigUint64Array`
    * `Boolean`
    * `DataView`
    * `Date`
    * `Error`
    * `EvalError`
    * `Float32Array`, `Float64Array`
    * `Function`
    * `Int8Array`, `Int16Array`, `Int32Array`
    * `Map`
    * `Number`
    * `Object`
    * `Promise`
    * `Proxy`
    * `RangeError`
    * `ReferenceError`
    * `RegExp`
    * `Set`
    * `SharedArrayBuffer`
    * `String`
    * `Symbol`
    * `SyntaxError`
    * `TypeError`
    * `Uint8Array`, `Uint8ClampedArray`, `Uint16Array`, `Uint32Array`
    * `URIError`
    * `WeakMap`
    * `WeakSet`
* 全局对象  (其它属性)
    * `Atomics`
    * `JSON`
    * `Math`
    * `Reflect`

## 5.2. Boolean 对象
* 创建
    ```js
    var 变量 = new Boolean(值); // 创建新对象, typeof(变量) = object
    var 变量 = Boolean(值);     // Boolean() 被当作函数, typeof(变量) = Boolean
    var 变量 = 值;              // typeof(变量) = Boolean
    ```
* 自身属性
    * 无
* 自身方法
    * 无

## 5.3. Number 对象
* 创建
    ```js
    var 变量 = new Number(值);  // 创建新对象, typeof(变量) = object
    var 变量 = Number(值);      // Number() 被当作函数, typeof(变量) = number
    var 变量 = 值;              // typeof(变量) = number
    ```
    * 若参数为非数字的值, 则会尝试将其转换为数字, 若转换失败则会返回 NaN

    如
    ```js
    var a = new Number("123");
    var b = Number("456");
    var c = 789;
    var d = new Number("abc");
    console.log(typeof a);  // 输出: object
    console.log(typeof b);  // 输出: number
    console.log(typeof c);  // 输出: number
    console.log(d);         // 输出: Number (NaN)
    ```
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    Number.MAX_VALUE        | JavaScript 中所能表示的最大值
    Number.MIN_VALUE        | JavaScript 中所能表示的最小值
    Number.MAX_SAFE_INTEGER | 最大安全整数, 即 9007199254740991
    Number.MIN_SAFE_INTEGER | 最小安全整数, 即 -9007199254740991
    Number.POSITIVE_INFINITY| 正无穷, 在溢出时返回
    Number.NEGATIVE_INFINITY| 负无穷, 在溢出时返回
    Number.NaN              | 非数字
    Number.EPSILON          | 表示 1 与 Number 所能表示的大于 1 的最小浮点数之间的差
* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    .parseFloat()           | 将字符串转换成浮点数, 和全局方法 parseFloat() 作用相同
    .parseInt()             | 将字符串转换成整型数字, 和全局方法 parseInt() 作用相同
    .isFinite()             | 是否为有穷数
    .isInteger()            | 是否为整数
    .isNaN()                | 是否为 NaN
    .isSafeInteger()        | 是否为安全整数, 即范围为 -(2^53 - 1)到 2^53 - 1 之间的整数
    .toExponential()        | 转为指数计数法
    .toFixed()              | 转为字符串, 结果的小数点后有指定位数的数字
    .toLocaleString()       | 转为字符串, 使用本地数字格式顺序
    .toPrecision()          | 格式化为指定的长度
    .toString()             | 转为字符串, 使用指定的基数
    .valueOf()              | 返回一个 Number 对象的基本数字值

## 5.4. BigInt
* 创建
    ```js
    var 变量 = BigInt(值);  // Boolean() 被当作函数, typeof(变量) = bigint
    var 变量 = 值n;         // typeof(变量) = bigint
    ```
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    .constructor            | 构造函数
    .prototype              | 向对象中添加属性和方法
    ...                     | ...
* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    .toString               | 把布尔值转换为字符串, 并返回结果
    .valueOf                | 返回 Boolean 对象的原始值
    ...                     | ...

## 5.5. Symbol
* 创建
    ```js
    var 变量 = Symbol(值);  // Boolean() 被当作函数, typeof(变量) = bigint
    ```
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    .description            | Symbol 的描述, 即构造函数中的值
* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    .asyncIterator          | -
    .for ( key )            | -
    .hasInstance            | -
    .isConcatSpreadable     | -
    .iterator               | -
    .keyFor ( sym )         | -
    .match                  | -
    .matchAll               | -
    .prototype              | -
    .replace                | -
    .search                 | -
    .species                | -
    .split                  | -
    .toPrimitive            | -
    .toStringTag            | -
    .unscopables            | -

## 5.6. String 对象
* 创建
    ```js
    var 变量 = new String(数字或字符串); // 创建新对象, typeof(变量) = object
    var 变量 = String(数字或字符串);     // String() 被当作函数, typeof(变量) = string
    var 变量 = "字符串";                 // 直接创建
    ```

    如
    ```js
    var a = new String("123");
    var b = String("456");
    var c = String(0x789);
    console.log("typeof a = " + typeof a, ", a =" + a);  // 输出: typeof a = object , a =123
    console.log("typeof b = " + typeof b, ", b =" + b);  // 输出: typeof b = string , b =456
    console.log("typeof c = " + typeof c, ", c =" + c);  // 输出: typeof c = string , c =1929
    ```
* 访问其中某个字符: `字符串[索引]`
    * 索引从 0 开始
    * 仅能访问, 不能修改
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    .constructor            | 构造函数
    .length                 | 获取字符串的长度
    .prototype              | 向对象中添加属性和方法
* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    .anchor()               | 创建一个 HTML 锚点, 即生成一个 `<a>` 标签, 标签的 name 属性为 `anchor()` 方法中的参数
    .big()                  | 用大号字体显示字符串
    .blink()                | 显示闪动的字符串
    .bold()                 | 使用粗体显示字符串
    .charAt()               | 返回在指定位置的字符
    .charCodeAt()           | 返回指定字符的 Unicode 编码
    .concat()               | 拼接字符串
    .fixed()                | 以打字机文本显示字符串
    .fontcolor()            | 使用指定的颜色来显示字符串
    .fontsize()             | 使用指定的尺寸来显示字符串
    .fromCharCode()         | 将字符编码转换为一个字符串
    .indexOf()              | 检索字符串, 获取给定字符串在字符串对象中首次出现的位置
    .italics()              | 使用斜体显示字符串
    .lastIndexOf()          | 获取给定字符串在字符串对象中最后出现的位置
    .link()                 | 将字符串显示为链接
    .localeCompare()        | 返回一个数字, 并使用该数字来表示字符串对象是大于, 小于还是等于给定字符串
    .match()                | 根据==正则表达式==匹配字符串中的字符
    .matchAll()             | 根据==正则表达式==匹配字符串中的字符
    .replace()              | 替换与==正则表达式==匹配的子字符串
    .search()               | 获取与==正则表达式==相匹配字符串首次出现的位置
    .slice()                | 截取字符串的片断, 并将其返回
    .small()                | 使用小字号来显示字符串
    .split()                | 根据给定字符 (或正则表达式) 将字符串分割为字符串数组
    .strike()               | 使用删除线来显示字符串
    .sub()                  | 把字符串显示为下标
    .substr()               | 从指定索引位置截取指定长度的字符串
    .substring()            | 截取字符串中两个指定的索引之间的字符
    .sup()                  | 把字符串显示为上标
    .toLocaleLowerCase()    | 把字符串转换为小写
    .toLocaleUpperCase()    | 把字符串转换为大写
    .toLowerCase()          | 把字符串转换为小写
    .toUpperCase()          | 把字符串转换为大写
    .toString()             | 返回字符串
    .valueOf()              | 返回某个字符串对象的原始值

## 5.7. Array 对象
* 创建
    ```js
    var 变量 = new Array(数组值);   // typeof(变量) = object
    var 变量 = Array(数组值);       // typeof(变量) = object
    var 变量 = [数组值];            // 直接创建, typeof(变量) = object
    ```
    * 使用`new Array()`定义数组时, 如果只有一个数值实参, 那么此数值将用以表示数组的初始长度
        * 最大长度为 2^32-1 = 4294967295
        * 例如`new Array(5)`表示定义一个长度为 5 的数组
            ```js
            var a = new Array(5);
            console.log(a);     // 输出: (5) […]
            ```
    * 可以在声明后继续添加数组值
    * 允许出现空位
        * 不影响 `.length` 的值
        * 空位可索引, 返回 `undefined`
        * 扩展运算符 (`...`) 也会将空位转为`undefined`
        * `for...of`循环也会遍历空位
    * `Array` 是特殊的对象
        * 默认键名是整数 $[0, 1, 2, ...)$
            > 有些对象 (如 `arguments` 和 `string` 对象) 类似 `Array` , 也使用整数作为键值, 但其不是 `Array`
            >   * 不能使用 `Array` 特有方法
            >   * `类数组对象 instanceof Array` 为 false
        * `in` 可用于 `Array`
            * 空位的键 not `in` `Array` 对象
    * 使用 `delete` 删除一个数组成员 (即便是最后一个元素), 会形成空位, 并且不会影响 `length` 属性

    如:
    ```js
    // 声明数组
    var a = new Array(1, 2.0, '3');
    var b = Array(null, 5, NaN);
    var c = []; // 先声明, 后添加
    c[0] = "a"
    c[1] = function () { console.log('hello') }
    c[5] = undefined        // c 中有空位
    // 数组
    console.log(a);         // 输出: [1, 2, '3']
    console.log(b);         // 输出: [null, 5, NaN]
    console.log(c);         // 输出: ['a', ƒ, …, undefined]
    // 空位不影响 length 的值
    console.log(c.length)   // 输出: 6
    delete c[5]
    console.log(c.length)   // 输出: 6
    // in 操作
    console.log(3 in c);    // 输出: false
    console.log('4' in c);  // 输出: false
    console.log(5 in c);    // 输出: true
    ```
* 访问元素: `数组名[索引]`, 索引从 0 开始
    * 索引本质是键名
    * 索引也可以是可转换位数字的变量或表达式, 如:
        ```js
        var arr = [1, 2, 3.14, '4'];
        console.log(arr[0]);
        console.log(arr['1']);
        console.log(arr[1 + 1]);
        console.log(arr[3.0]);
        ```
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    .constructor            | 构造函数
    .length                 | 设置或返回数组中元素的个数, ==可修改此属性==
    .prototype              | 向对象中添加属性和方法
* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    .concat()               | 拼接数组, 并返回结果
    .copyWithin()           | 从指定位置拷贝元素到数组的另一个指定位置
    .entries()              | 返回数组的可迭代对象
    .every()                | 检测每个元素是否都符合条件
    .fill()                 | 使用一个固定值来填充数组
    .filter()               | 检测数值元素, 并返回符合条件所有元素的数组
    .find()                 | 返回符合传入函数条件的数组元素
    .findIndex()            | 返回符合传入函数条件的数组元素索引
    .forEach()              | 数组每个元素都执行一次回调函数
    .from()                 | 通过给定的对象创建一个数组
    .includes()             | 判断一个数组是否包含一个指定的值
    .indexOf()              | 搜索数组中的元素, 并返回它所在的位置
    .isArray()              | 判断对象是否为数组
    .join()                 | 把数组的所有元素放入一个字符串
    .keys()                 | 返回数组的可迭代对象, 包含原始数组的键 (key)
    .lastIndexOf()          | 搜索数组中的元素, 并返回它最后出现的位置
    .map()                  | 通过指定函数处理数组的每个元素, 并返回处理后的数组
    .pop()                  | 删除数组的最后一个元素并返回删除的元素
    .push()                 | 向数组的末尾添加一个或更多元素, 并返回数组的长度
    .reduce()               | 累加 (从左到右) 数组中的所有元素, 并返回结果
    .reduceRight()          | 累加 (从右到左) 数组中的所有元素, 并返回结果
    .reverse()              | 反转数组中元素的顺序
    .shift()                | 删除并返回数组的第一个元素
    .slice()                | 截取数组的一部分, 并返回这个新的数组
    .some()                 | 检测数组元素中是否有元素符合指定条件
    .sort()                 | 对数组的元素进行排序
    .splice()               | 从数组中添加或删除元素
    .toString()             | 把数组转换为字符串, 并返回结果
    .unshift()              | 向数组的开头添加一个或多个元素, 并返回新数组的长度
    .valueOf()              | 返回数组对象的原始值

## 5.8. Set (ES6)

## 5.9. WeakSet (ES6)

## 5.10. Map (ES6)

## 5.11. WeakMap (ES6)

## 5.12. Math 对象
* 内置对象, 数学中常用的常量值和函数, 如计算平均数, 求绝对值, 四舍五入等
* 创建
    ```js
    // 无须使用 new Math(...) 方式, 可直接访问属性和方法
    var 变量 = Math.属性;          // 当前时间
    var 变量 = Math.函数(参数);    // 1970-01-01 00:00:00 + 毫秒数
    ```
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    Math.E                  | 返回算术常量 e, 即自然对数的底数 (约等于 2.718)
    Math.LN2                | 返回 2 的自然对数 (约等于 0.693)
    Math.LN10               | 返回 10 的自然对数 (约等于 2.302)
    Math.LOG2E              | 返回以 2 为底的 e 的对数 (约等于 1.443)
    Math.LOG10E             | 返回以 10 为底的 e 的对数 (约等于 0.434)
    Math.PI                 | 返回圆周率 π (约等于 3.14159)
    Math.SQRT1_2            | 返回返回 2 的平方根的倒数 (约等于 0.707)
    Math.SQRT2              | 返回 2 的平方根 (约等于 1.414)

* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    Math.abs(x)             | 返回 x 的绝对值
    Math.acos(x)            | 返回 x 的反余弦值
    Math.acosh(x)           | 返回 x 的反双曲余弦值
    Math.asin(x)            | 返回 x 的反正弦值
    Math.asinh(x)           | 返回 x 的反双曲正弦值
    Math.atan(x)            | 返回 x 的反正切值
    Math.atanh(x)           | 返回 x 的反双曲正切值
    Math.atan2(y,x)         | 返回 y/x 的反正切值
    Math.cbrt(x)            | 返回 x 的立方根
    Math.ceil(x)            | 对 x 进行向上取整, 即返回大于 x 的最小整数
    Math.clz32(x)           | 返回将 x 转换成 32 无符号整形数字的二进制形式后, 开头 0 的个数
    Math.cos(x)             | 返回 x 的余弦值
    Math.cosh(x)            | 返回 x 的双曲余弦值
    Math.exp(x)             | 返回算术常量 e 的 x 次方, 即 Ex
    Math.expm1(x)           | 返回 exp(x) - 1 的值
    Math.floor(x)           | 对 x 进行向下取整, 即返回小于 x 的最大整数
    Math.fround(x)          | 返回最接近 x 的单精度浮点数
    Math.hypot([x, [y, [...]]]) | 返回所有参数平方和的平方根
    Math.imul(x, y)         | 将参数 x, y 分别转换位 32 位整数, 并返回它们相乘后的结果
    Math.log(x)             | 返回 x 的自然对数
    Math.log1p(x)           | 返回 x 加 1 后的自然对数
    Math.log10(x)           | 返回 x 以 10 为底的对数
    Math.log2(x)            | 返回 x 以 2 为底的对数
    Math.max([x, [y, [...]]])   | 返回多个参数中的最大值
    Math.min([x, [y, [...]]])   | 返回多个参数中的最小值
    Math.pow(x,y)           | 返回 x 的 y 次幂
    Math.random()           | 返回一个 0 到 1 之间的随机数
    Math.round(x)           | 返回 x 四舍五入后的整数
    Math.sign(x)            | 返回 x 的符号, 即一个数是正数, 负数还是 0
    Math.sin(x)             | 返回 x 的正弦值
    Math.sinh(x)            | 返回 x 的双曲正弦值
    Math.sqrt(x)            | 返回 x 的平方根
    Math.tan(x)             | 返回 x 的正切值
    Math.tanh(x)            | 返回 x 的双曲正切值
    Math.trunc(x)           | 返回 x 的整数部分

## 5.13. Date  对象
* 创建
    ```js
    // 必须使用 new Data(...) 方式,
    var 变量 = new Date();          // 当前时间
    var 变量 = new Date(毫秒值);    // 1970-01-01 00:00:00 + 毫秒数
    var 变量 = new Date(日期字符串);
    var 变量 = new Date(年, 月, 日[, 时, 分, 秒, 毫秒]);
    ```
    * 日期字符串
        * `"YYYY/MM/dd HH:mm:ss"` (推荐): 若省略时间部分, 则对象的时间为 00:00:00
        * `"YYYY-MM-dd HH:mm:ss"`: 若省略时间部分, 则对象的时间为 00:00:00 (加上本地时区)
    * `年月日时分秒`的格式:
        * 年: 推荐使用 4 位数字
        * 月: 0 = 1月, ..., 11 = 12月 (==真变态==)
        * 日: 1 = 1日, ..., 31 = 31日
        * 时: 0 ~ 23
        * 分: 0 ~ 59
        * 秒: 0 ~ 59
        * 毫秒: 0 ~ 999
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    .constructor            | 构造函数
    .prototype              | 向对象中添加属性和方法
* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    .getDate()              | 返回一个月中的某一天 (1 ~ 31)
    .getDay()               | 返回一周中的某一天 (0 ~ 6)
    .getMonth()             | 返回月份 (0 ~ 11)
    .getFullYear()          | 返回四位数字的年份
    .getYear()              | 已废弃, 请使用 getFullYear() 方法代替
    .getHours()             | 返回时 (0 ~ 23)
    .getMinutes()           | 返回分 (0 ~ 59)
    .getSeconds()           | 返回秒 (0 ~ 59)
    .getMilliseconds()      | 返回毫秒(0 ~ 999)
    .getTime()              | 返回 1970 年 1 月 1 日至今的毫秒数
    .getTimezoneOffset()    | 返回本地时间与格林威治标准时间 (GMT) 的分钟差
    .getUTCDate()           | 根据通用时间从 Date 对象返回月中的一天 (1 ~ 31)
    .getUTCDay()            | 根据通用时间从 Date 对象返回周中的一天 (0 ~ 6)
    .getUTCMonth()          | 根据通用时间从 Date 对象返回月份 (0 ~ 11)
    .getUTCFullYear()       | 根据通用时间从 Date 对象返回四位数的年份
    .getUTCHours()          | 根据通用时间返回 Date 对象的小时 (0 ~ 23)
    .getUTCMinutes()        | 根据通用时间返回 Date 对象的分钟 (0 ~ 59)
    .getUTCSeconds()        | 根据通用时间返回 Date 对象的秒钟 (0 ~ 59)
    .getUTCMilliseconds()   | 根据通用时间返回 Date 对象的毫秒(0 ~ 999)
    .parse()                | 返回1970年1月1日午夜到指定日期 (字符串) 的毫秒数
    .setDate()              | 设置 Date 对象中月的某一天 (1 ~ 31)
    .setMonth()             | 设置 Date 对象中月份 (0 ~ 11)
    .setFullYear()          | 设置 Date 对象中的年份 (四位数字)
    .setYear()              | 已废弃, 请使用 setFullYear() 方法代替
    .setHours()             | 设置 Date 对象中的小时 (0 ~ 23)
    .setMinutes()           | 设置 Date 对象中的分钟 (0 ~ 59)
    .setSeconds()           | 设置 Date 对象中的秒钟 (0 ~ 59)
    .setMilliseconds()      | 设置 Date 对象中的毫秒 (0 ~ 999)
    .setTime()              | 以毫秒设置 Date 对象
    .setUTCDate()           | 根据通用时间设置 Date 对象中月份的一天 (1 ~ 31)
    .setUTCMonth()          | 根据通用时间设置 Date 对象中的月份 (0 ~ 11)
    .setUTCFullYear()       | 根据通用时间设置 Date 对象中的年份 (四位数字)
    .setUTCHours()          | 根据通用时间设置 Date 对象中的小时 (0 ~ 23)
    .setUTCMinutes()        | 根据通用时间设置 Date 对象中的分钟 (0 ~ 59)
    .setUTCSeconds()        | 根据通用时间设置 Date 对象中的秒钟 (0 ~ 59)
    .setUTCMilliseconds()   | 根据通用时间设置 Date 对象中的毫秒 (0 ~ 999)
    .toSource()             | 返回该对象的源代码
    .toString()             | 把 Date 对象转换为字符串
    .toTimeString()         | 把 Date 对象的时间部分转换为字符串
    .toDateString()         | 把 Date 对象的日期部分转换为字符串
    .toGMTString()          | 已废弃, 请使用 toUTCString() 方法代替
    .toUTCString()          | 根据通用时间, 把 Date 对象转换为字符串
    .toLocaleString()       | 根据本地时间格式, 把 Date 对象转换为字符串
    .toLocaleTimeString()   | 根据本地时间格式, 把 Date 对象的时间部分转换为字符串
    .toLocaleDateString()   | 根据本地时间格式, 把 Date 对象的日期部分转换为字符串
    .UTC()                  | 根据通用时间返回 1970 年 1 月 1 日 到指定日期的毫秒数
    .valueOf()              | 返回 Date 对象的原始值

## 5.14. RegExp 对象
* 创建
    ```js
    var 变量 = new RegExp(正则表达式, 修饰符);
    var 变量 = /正则表达式/修饰符;
    ```
    * **修饰符**设置字符串的匹配模式
        修饰符  | 描述
        :-----: | :----------------------------
        i       | 执行对大小写不敏感的匹配
        g       | 执行全局匹配 (查找所有的匹配项, 而非在找到第一个匹配项后停止)
        m       | 执行多行匹配
        s       | (ES6) 允许使用`.`匹配换行符
        u       | (ES6) 使用 Unicode 码的模式进行匹配
        y       | (ES6) 执行 "粘性" 搜索, 匹配从目标字符串的当前位置开始

        * 修饰符可组合使用
    * 支持具名组匹配 (Named Capture Groups) (ES6)
        * 基于此可实现结构赋值和替换
        ```js
        const RE_DATE = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/;

        const matchObj = RE_DATE.exec('1999-12-31');
        const year = matchObj.groups.year;   // "1999"
        const month = matchObj.groups.month; // "12"
        const day = matchObj.groups.day;     // "31"
        //
        let {groups: {one, two}} = /^(?<one>.*):(?<two>.*)$/u.exec('foo:bar');
        one  // foo
        two  // bar
        ```

    * 注意: 使用 `new` 创建 RegExp 对象时, 需要将正则表达式中的特殊字符转义, 即在特殊字符前加反斜杠\, 例如\\w+
* 自身属性
    属性                    | 描述
    :---------------------- | :----------------------------
    .constructor            | 返回一个函数, 该函数是一个创建 RegExp 对象的原型
    .global                 | 判断是否设置了修饰符 "g"
    .ignoreCase             | 判断是否设置了修饰符 "i"
    .lastIndex              | 用于规定下次匹配的起始位置
    .multiline              | 判断是否设置了修饰符 "m"
    .source                 | 返回正则表达式的匹配模式
* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    .compile()              | 在 1.5 版本中已废弃, 编译正则表达式
    .exec()                 | 在字符串搜索匹配项, 并返回一个数组, 若没有匹配项则返回 null
    .test()                 | 测试字符串是否与正则表达式匹配, 匹配则返回 true, 不匹配则返回 false
    .toString()             | 返回表示指定对象的字符串

## 5.15. JSON 对象
* 自身方法
    方法                    | 描述
    :---------------------- | :----------------------------
    JSON.stringify()        | 转为 JSON 字符串
    JSON.parse()            | 将 JSON 字符串转换成对应的值

--------------------------------------------------------------------------------
# 6. 其它相关

## 6.1. Node.js
* Node.js 不是一门新的编程语言, 也不是一个 JavaScript 框架, 它是一套 JavaScript 运行环境, 用来支持 JavaScript 代码的执行。用编程术语来讲, Node.js 是一个 JavaScript 运行时 (Runtime)
* Node.js 的组成
    1. **V8 引擎**
        V8 引擎就是 JavaScript 解释器, 它负责解析和执行 JavaScript 代码。
        V8 引擎借鉴了 Java 虚拟机和 C++ 编译器的众多技术, 它将 JavaScript 代码直接编译成原生机器码, 并且使用了缓存机制来提高性能, 这使得 JavaScript 的运行速度可以媲美二进制程序
    1. **标准库**
        本地模块使用 C/C++ 编写, 而 Node.js 面向 JavaScript 开发人员, 所以必须要封装本地模块的 C/C++ 接口, 提供一套优雅的 JavaScript 接口给开发人员, 并且要保持接口在不同平台 (操作系统) 上的一致性
        * 常用标准库
            库              | 说明
            :-------------: | :---
            os              | 与操作系统相关的函数, 如
            path            | 路径
            fs              | 文件
            child_process   | 调用外部程序
            util            | 各种有用的函数, 如 `promisify`

    1. **本地模块**
        Node.js 集成了众多高性能的开源库, 它们使用 C/C++ 语言实现, 比如:

        模块 | 说明
        :--: | :---
        libuv   | 一个跨平台的, 基于事件驱动的异步 I/O 库。但是 libuv 不仅限于 I/O, 它还提供了进程管理, 线程池, 信号处理, 定时器等其它功能, <br/> Linux 中一切皆文件, 这里的 I/O 不仅仅包括文件读写, 还包括数据库读写, 网络通信 (socket) 等
        nmp     | Node.js 包管理器, 可以下载包, 安装包, 卸载包, 更新包, 上传包等
        http_parser | 一款由C语言编写的轻量级 HTTP 解析器, 用以支持 Web 应用开发
        zlib    | 工业级的数据压缩/解压模块, Nodejs 借助 zlib 来创建同步, 异步或者流式的压缩/解压接口
        OpenSSL | 该模块提供了经过严密测试的许多加密/解密功能, 现代 Web 依赖这些功能来实现安全性, 比如 SSL 协议和 https 协议。
        c-ares  | 异步 DNS 查询和解析库

        Node.js 直接在计算机上运行 JavaScript 代码, 并且要赋予 JavaScript 强大的能力, 所以它的本地模块和浏览器中的运行时有很多大区别, 甚至说几乎没有什么关联。Node.js 几乎完全抛弃了浏览器, 自己从头构建了一套全新的 JavaScript 运行时
* `util.promisify` 可以将回调类函数转为 `aync` 函数, 如
    ```js
    const util = require('util');
    const exec = util.promisify(require('child_process').exec);
    async function lsExample() {
        const { stdout, stderr } = await exec('ls');
        console.log('stdout:', stdout);
        console.error('stderr:', stderr);
    }
    lsExample();
    ```