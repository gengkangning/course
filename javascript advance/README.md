# JS数据类型、值与类型转换

## JS的数据类型

### 两类

* 基本（原始）数据类型：Number,String,Boolean,Null,Undefined ，定义为基本类型的函数局部变量分配在栈区

* 引用（对象）数据类型：Object（Array、Function、Date、Error等），定义为引用类型的变量，其引用分配在栈区或堆区，引用的对象分配在堆区

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

### 函数参数的数量问题

#### JS函数调用时实参数量可以与形参不一致

* 实参数量大于形参的情况（通过函数对象属性arguments获得所有实参、类数组对象）

* 实参数量小于形参的情况（少的参数值为undefined、可使用| |来给出默认值）

### 参数类型与传递方式（值，引用）

* 基本（原始）类型（Number、String、Boolean、Null、Undefined）

* 引用（对象）类型（Object（Array、Function、Date、Error等）

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
