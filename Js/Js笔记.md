### JS红宝书

#### 一，变量
1. var与let的区别

   - var声明的变量是函数作用域，let声明的变量是块级作用域。
   - var声明的变量存在变量提升特性，let没有。
   - var允许重复声明相同的变量，后者会覆盖前者，let不能重复声明相同的变量。
   - 如果在全局作用域中用var声明变量，变量会默认称为window的一个属性，let声明的变量则不会添加到window对象中。

2. const与let

   - const在声明变量时必须同时初始化变量，let可以只声明不初始化。

3. typeof null = object?

   - 逻辑上讲，null值表示一个空对象指针，这也是给typeof传一个null会返回object的原因。
   - 原理上讲，变量机器码的低1-3位存储类型信息，null和object都为000。

4. Number和parseInt的区别？https://www.jianshu.com/p/dcde6e808055

   - Number有较为复杂的转换规则。

     ```
     如果是boolean值，true和false将分别转换为十进制数值
     如果是数字值，只是简单的传入与返回
     如果是null， 返回0
     如果是undefined ，返回NaN
     如果是字符串，遵循下列原则：
     
     1.只包含数字，八进制的数值将会被忽略前面的0，直接显示为十进制 如：“011” 应为 ‘9’但只能转换为‘11’；
     2.浮点数可以转换为对应的浮点数值
     3.如果是十六进制会转换为十进制值
     4.如果字符串为空转换为0
     5.其他转为NaN
     ```

   - parseInt()在转换字符是更看其是否符合数值模式。它会忽略字符串前面的空格，知道找到第一个非空格字符。它是逐个解析字符的。

   - parseInt()同样不具有解析八进制的能力，所以可以给parseInt()加入第二个参数表示进制。

5. toString()和String()

   - toString()方法可用于数值，布尔值，对象和字符串值。null和undefined没有该方法。
   - String()转型函数：如果有toString()，返回该方法结果，如果是null返回“null”，undefined返回“undefined”。

6. for...of和for...in的区别

   - for...in遍历的是一对键值对的键名，而for...of遍历的是键值。

   - for...of可以遍历可迭代对象（数组，Map，Set，String，arguments等），不可以遍历普通对象的属性。而for...in可以用来遍历普通对象的可枚举属性。
   - for...in循环只遍历可枚举属性（包括它的原型链上的可枚举属性），Object.keys()不包括原型方法和属性。

7. JavaScript数据类型：

   - 基本数据类型（原始类型）Null, Undefined, String, Number, Boolean, Symbol
   - 复杂数据类型（对象类型）Object

<img src="https://www.runoob.com/wp-content/uploads/2013/08/Javascript-DataType.png" alt="img" style="zoom:50%;" />
