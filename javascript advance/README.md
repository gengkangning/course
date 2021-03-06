# JS数据类型、值与类型转换

## JS的数据类型

### 两类

* 基本（原始）数据类型：Number,String,Boolean,Null,Undefined ，定义为基本类型的函数局部变量分配在栈区

* 引用（对象）数据类型：Object（Array、Function、Date、Error等），定义为引用类型的变量，其引用分配在栈区或堆区，引用的对象分配在堆区

### 函数不属于数据，但是在JS中可以用typeof方法

### 数据类型检测方法（typeof、instanceof）

### 基本类型与引用类型的区别 
* 赋值时不同（赋值、赋地址、深拷贝与浅拷贝）

* 判等时的不同

1. 值类型是判断变量的值是否相等（值比较）, == 比较数值是否相等,===判断数值和数据类型是否都相等

2. 引用类型是判断所指向的内存空间是否相同（引用比较）, ==,===都需要判断是否指向同一空间

## 数据类型转换

* 其他类型转换为Boolean类型, Boolean（）、value？true：false、！！value

* 其他类型转换为Number类型,Number（）、+value、parseFloat、parseInt

* 其他类型转换为String类型,String（）、‘’+value、 value.toString()

# JS语法、表达式及语句

* ES5中的块（ES5中没有块作用域，所以带来了很多问题）

## JS严格模式

*  针对整个脚本文件使用 'use strict'  针对函数使用 'use strict'

1. 严格模式下全局变量需显式声明

2. 一般函数中的this（严格模式）为undefined，非严格下为全局变量（window）

3. 严格模式下禁止删除不可改变的属性和未定义的变量

4. 严格模式下禁止函数参数重名

## switch详解

1. case在比较时使用的是全等操作符比较,因此不会发生类型转换

2. case 后可以是一个表达式（如 i<60）(使用switch(true)可以达到if-else的效果)

## for...in

1. for...in常用来遍历对象

2. for...in遍历数组（忽略空缺）

# JS运算符

## 赋值运算符

* 注意=与==（表达式要发反写，有什么好处）

## 算数运算符

* ` var x = "1";console.log(++x); //2 注意++和--的隐式类型转换var x = "1";console.log(x+=1);//11 `

## 逻辑运算符

### 最常见情况（运算符两边的操作数都是布尔类型）

1. 对于&&来说， 除了两侧都为真时为真，其他情况都为假

2. 对于 | | 来说，除了两侧都为假时为假，其他情况都为真

### 当逻辑运算符&&和||两侧的操作数不是布尔类型时

1. 首先将左操作数转换成布尔类型

2. 对转换后的左操作数进行逻辑判断（true or false）

3. 根据短路原则返回原始左操作数或原始右操作数

* 短路原则

1. 对于&&，转换后的左操作数若为true，则直接返回原始右操作数，若为false则  直接返回原始左操作数

2. 对于| |，转换后的左操作数若为true，则直接返回原始左操作数，若为false则直  接返回原始右操作数

3. 通过短路原则，可以用&&和| |来实现复杂的条件语句来代替if-else

### &&与||在实际中的应用

* 遵循短路特性，使用&&和||可用来实现条件语句

* 使用||来设置函数参数的默认值

1. 函数定义时可以给参数指定默认值，调用时若未传参数则该参数的值取它定义时的默认值

2. JS（ES6之前）不能直接为函数的参数指定默认值，可以通过 | | 来实现

* sum函数的问题及完善

1. 若实参转换为布尔类型为false，返回值则可能不是预期结果，如sum(1,0,0)为10

2. 增加判断，确保实参转换为布尔类型时为true

# 函数

## JS函数及函数对象

### 定义：三种方式

* 通过函数声明的形式来定义（要有函数名）

* 通过函数表达式的形式来定义（可以是没有函数名的匿名函数，有名的话方便调用栈追踪）

* 通过Function构造函数实例化的形式来定义（JS中函数也是对象，函数对象）

### 函数调用的四种方法

* 作为函数直接调用（非严格模式下this为全局对象，严格模式下为undefined）

* 作为方法调用（this为调用此方法的对象）

* 通过call( )和apply( )间接调用（this为函数对象的call/apply方法的首个参数，移花接木）

* 作为构造函数调用（this为实例化出来的对象）

### 函数方法调用三种方法(调用对象的函数属性)：

* 方法调用(调用对象的函数属性) robot.say_hello(); 

* 构造函数调用(相当于类的用法,用来生成对象)

* 动态访问对象的函数 ，对象的函数属性依然是函数 `  var robot = {
                            x   : 2,
                    say_hello   : function(){ console.log( "Hello!" ); }
             };
 robot["say_hello"](); //等价于 robot.say_hello(); `

### this引用的指向

* 无任何前缀的函数调用时，this指向顶层对象或者叫全局对象，浏览器里是window（nodejs里是global）。

* 方法调用的时候，this指向方法所在的对象

* 构造函数里，this指向新生成的实例

* apply/call调用的时候，this指向apply/call方法中的第一个参数

### 例子

` var robot = {
    name : "cup",
    say : function() { console.log( "Hi, I'm " + this.name + "."); }
}
var fn = robot.say;
// 将robot.say引用的函数赋值给全局变量 fn.

fn()                        // 打印结果为 Hi, I'm .
// 执行函数(全局的方法),this引用了全局对象,由于全局对象没有name属性,所以没有取到值. `

` var robot = {
    name : "cup",
    say : function() { console.log( "Hi, I'm " + this.name + "."); }
}
var fn = robot.say;
//将robot.say引用的函数赋值给全局变量 fn.
//相当于给全局对象定义了一个属性fn,并赋予robot.say所指代的函数.

var name = "bower",
//相当于给全局对象定义了一个属性name,赋值为"bower"，在浏览器里，上面这行代码等价于 window.name = "bower";

fn()                    // 打印结果为 Hi, I'm bower.
//执行函数fn(相当于调用全局对象的fn方法),执行时this引用了全局对象.所以this.name的值是"bower". `

### 函数的apply与call方法

* 而apply和call的功能是，通过传参的方式，强制函数内的this指定某一对象。this引用的会被指向apply/call的第一个参数。

* 对于apply来说,剩余的参数将通过数组来传递,而call是直接按参数列表传递.

1. ` say.apply({name:"cup"}, [12, "boy"]) ` 

2. ` say.call({name:"cup"}, 12, "boy") `  

* 在实际的编程过程中，我们有时会为了函数回调而使用apply或call调用

### 函数参数的数量问题

#### JS函数调用时实参数量可以与形参不一致

* 实参数量大于形参的情况（通过函数对象属性arguments获得所有实参、类数组对象）

* 实参数量小于形参的情况（少的参数值为undefined、可使用| |来给出默认值）

### 参数类型与传递方式（值，引用）

* 基本（原始）类型（Number、String、Boolean、Null、Undefined）

* 引用（对象）类型（Object（Array、Function、Date、Error等）

### 面向对象

* JavaScript是一种没有类的，面向对象的语言。它使用原型继承来代替类继承。

* 那么，原型prototype在哪里呢？其实任何一个函数都有prototype属性。

* 当我们得到一个实例之后，访问实例的原型,使用__proto__属性.

* avascript对象(如robot)拥有自有属性(如通过构造函数this.name=name设置的属性)和继承属性(例如代理自Robot.prototype的属性)两种。

* 在查询对象robot的属性age时，先查找robot中自有属性的age属性，如果没找到，则查找robot继承属性(也就是robot的原型对象:robot.__proto__)中的age属性，直到查找到age或者一个原型是null的对象为止.

* 可以使用in 或者 hasOwnProperty 来判断对象中是否存在属性或者是否存在自有属性。

### 函数对象

### 函数对象的属性

* 函数对象属性之arguments 实参集合（类似数组的一个对象）

* 函数对象属性之length 形参个数 

* 函数对象属性之caller 获取调用当前函数的函数。

1. 如果函数是从 JavaScript 程序的顶层调用的，则caller包含null。

2. 如果在字符串上下文中使用 caller 属性，则其结果和 functionName.toString 相同，也就是说，将显示函数的反编译文本

3. 函数对象属性之caller 获取调用当前函数的函数。

* 函数对象属性之callee 返回正被执行的 Function 对象，即指定的 Function 对象的正文
callee 属性是 arguments 对象的一个成员，该属性仅当相关函数正在执行时才可用。通常这个属性被用来递归调用匿名函数。优点，可以是匿名函数

* 函数对象属性之 constructor 获取创建某个对象的构造函数。可以用来判断对象是哪一类

* 函数对象属性之 prototype

1. 获取对象的原型。每一个构造函数都有一个prototype属性，指向另一个对象。

2. 这个对象的所有属性和方法，都会被构造函数的实例继承。

## 原型链

1. 总共三类对象(蓝色大框)

2. 实例对象（通过new XX() 所得到的实例），跟原型链相关的只有 __proto__ 属性，指向其对应的原型对象 *.prototype 。

3. 构造函数对象分原生和自定义两类。跟原型链相关的有 __proto__ 属性，除此之外还有 prototype 属性。它们的 __proto__ 属性都是指向 Function.prototype 这个原型对象的。prototype 也是指向对应的原型对象。

4. 原型对象除了一样拥有 __proto__ 外，也拥有独有的属性 constructor 。它的__proto__ 指向的都是 Object.prototype ，除了 Object.prototype 本身，它自己是指向 null 。而 constructor 属性指向它们对应的构造函数对象。

5. 原型链是基于 __proto__ 的。实例只能通过其对应原型对象的 constructor 才能访问到对应的构造函数对象。构造函数只能通过其对应的 prototype 来访问相应的原型对象。

### 例子

` unction Robot(name){this.name = name;};        //自定义构造函数
Robot.prototype = {age:12, sex:"boy"};
var robot = new Robot("bower");
//通过__proto__寻找原型链的关系:
//假设
//robot的原型对象是a.
//Robot的原型对象是b.
//Robot.prototype和Function.ptototype的原型对象都是c.
//Object.prototype的原型对象是d. `

` unction Robot(name){this.name = name;};    //自定义构造函数
Robot.prototype = {age:12, sex:"boy"};        //设置将会被集成的原型对象
var robot = new Robot("bower");            //通过构造函数实例化一个对象
//通过__proto__寻找原型链的关系:            //所有的__proto__属性均会指向该实例对象所继承到的原型对象即*.prototype
//robot的原型对象是Robot.prototype,即默认情况下Robot.prototype与robot.__proto__是同一个对象.
//Robot的原型对象是Function.prototype.
//Robot.prototype和Function.ptototype的原型对象都是Object.prototype.
//Object.prototype的原型对象是null. `

### 函数对象的方法

* 函数对象方法之 call 调用一个普通函数或对象的方法时，用另一个对象替换当前对象

1. call([thisObj[, arg1[, arg2[, [, argN]]]]])

2. 它允许您将函数的 this 对象从初始上下文变为由 thisObj 指定的新对象。

3. 如果没有提供 thisObj 参数，则 global 对象被用作 thisObj。
4.  与apply方法不同的地方是，apply的第二个参数类型必须是Array，
5. 而call方法是将所有的参数列举出来，用逗号分隔

* 函数对象方法之 apply

1. functionName.apply([thisObj[,argArray]])

2. 与call方法不同的地方是，apply的第二个参数类型必须是Array

* 函数对象方法之 bind 硬绑定

1. function.bind(thisArg[,arg1[,arg2[,argN]]])

2. 在绑定功能中，this对象解析为传入的对象。

3. 返回一个与 function 函数相同的新函数，只不过函数中的this对象和参数不同。

* bind 参数的问题

1. 该绑定函数将 bind 方法中指定的参数用作第一个参数和第二个参数。
2. 在调用该绑定函数时，指定的任何参数将用作第三个、第四个参数（依此类推） 

* 函数对象方法之 toString与valueOf 继承自Object.prototype的方法

1. 返回对象的字符串表示形式。objectname.toString([radix])
2. 关于toString与valueOf的详细内容参见JS对象相关章节

## JS预解析（声明提升）

### 预解析主要工作（变量声明和函数声明提升）

* 当有同名函数和变量同时声明时，忽略到变量声明。当有同名变量声明时，后边的覆盖前边的。

*  解析器在执行代码前的进行代码扫描（var、function）  

*  将变量和函数声明在当前作用域（全局、函数）内进行提升（提升到当前作用域最顶端，会冲破块作用域）

* ES5中函数及变量声明重复的话，相当于覆盖

* 同时有var和function关键字时

1. 情形1：函数表达式 当function前有运算符的话，认定为表达式，不提升

2. 情形2：变量名同函数名

## JS变量作用域

* JS采用的是静态词法作用域，代码完成后作用域链就已形成，与代码的执行顺序无关

* 词法作用域不会被函数从哪里调用等因素影响，与调用形式无关（体现了静态性）

` var name = "Jack";
function echo() {
    console.log(name);
}
function foo() {
    var name = "Bill";
    echo();
}
foo();//Jack
 `
* JS无块作用域，但是有函数作用域

### 无块作用域的问题（变量污染、变量共享问题）

* 解决方案IIFE（更多内容参见IIFE部分）
 
## JS执行上下文 (当前函数作用域内)

* 执行上下文指代码执行时的上下文环境（包括局部变量、相关的函数、相关自由变量等）

* JS运行时会产生多个执行上下文，处于活动状态的执行上下文环境只有一个

## 调用栈（Call Stack）

* 代码执行时JS引擎会以栈的方式来处理和追踪函数调用（函数调用栈 Call Stack）

* 栈底对应的是全局上下文环境，而栈顶对应的是当前正在执行的上下文环境

 ## 作用域链
 
* 如果有多个文具店和多个银行，那么执行就有多种可能，形成不同的链式关系

* 作用域链与执行上下文

1. 执行时，当前执行上下文，对应一个作用域链环境来管理和解析变量和函数（动态性）

2. 变量查找按照由内到外的顺序（遵循词法作用域），直到完成查找，若未查询到则报错

3.  当函数执行结束，运行期上下文被销毁，此作用域链环境也随之被释放

# JS中的IIFE模式（立即执行的函数表达式
）

* 作用：建立函数作用域，解决ES5作用域缺陷所带来的问题，如：变量污染、变量共享等问题

## 写法：

### 使用小括号的写法

1. (function foo( x,y){ ... }(2,3));  //2,3为传递的参数

2.  (function foo(x,y){ ... })(2,3); 

### 与运算符结合的写法（先执行函数，再进行运算）

1. var i = function( ){ return 10; }( ); //i为10

2.  true && function( ){  ... }( );

3. ~function(arg1,arg2){ ... }(x,y); //x,y为传递参数 位运算非操作符

4. !function( ){ ...  }( );//思考 !function(){return 2; }( ); 与 !function(){return 0; }( );

# 闭包

* 闭包是由函数和与其相关的引用环境组合而成的实体

* 闭包是词法作用域中的函数和其相关变量的包裹体
* 自由变量常驻内存，局部变量不常驻内存
