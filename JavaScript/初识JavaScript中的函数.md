**前言**：本文将详细的介绍JS中函数的相关概念，总结函数中比较容易理解错的坑，让我们更加全面的认识函数。最后会简单介绍一下传说中的作用域和闭包（暂不细说）。部分概念与代码参考[阮一峰JS教程](http://javascript.ruanyifeng.com/grammar/function.html)。

---

## 1、什么是函数

>函数是一段可以反复调用的代码块。函数还能接受输入的参数，不同的参数会返回不同的值。

函数的本质就是对象，或者说可以执行代码的对象就是函数。
因此我们甚至可以使用写纯对象的方式来写一个函数，让我们更了解函数的本质：
```
var fn = {} ;
fn.params = ['x','y'] ; // 参数
fn.fbody = 'console.log(1)' ; //函数体
fn.call = function(){
	eval(fn.fbody)
}
fn.call() ; // 调用函数的call方法来执行函数
// 1
```
如上述代码，fn作为一个对象，使用`call()`方法执行的效果和执行函数是一样的，当然fn只是个长得像函数的对象，只是为了便于我们理解函数的本质。

注：上面代码中使用了`eval()` 方法，那么就在这里提一下：
 `eval`命令的作用是，将字符串当作语句执行。`eval()` 方法是`window`的全局对象。
如`eval('var a = 1;'); a // 1`
一般情况下尽量避免使用该方法。

## 2、函数的五种声明方法

注：函数体内部的`return`语句，表示返回。JavaScript 引擎遇到`return`语句，就直接返回`return`后面的那个表达式的值，后面即使还有语句，也不会得到执行。也就是说，`return`语句所带的那个表达式，就是函数的返回值。`return`语句不是必需的，如果没有的话，该函数就不返回任何值，或者说返回`undefined`。

- 具名函数的声明
 ```
 function fn1() {
    return undefined; // 如果不写return ，浏览器默认添加
}  
```

- 匿名函数的声明
`var fn2 = function() {}`

- 结合上面两种方式(谨慎使用)
 `var fn3 = function fn4() {}`

- 使用`Function`函数对象来声明
```
var fn5 = new Function(
  'x',
  'y',
  'return x + y'
);
```
其中`new Function()` 中，最后一个参数表示函数体，前面的参数表示传入函数的参数。

- 最酷炫的声明方法：箭头函数
`var fn6 = (x,y) => {return x+y}`箭头前面表示传入函数的参数，箭头后面表示函数体。
如果只有一个参数，参数的圆括号可以省略：
` var fn7 = x => {return x*2} `
如果函数体只有一句话，可以同时省略函数体的大括号及`return`：
` var fn8 = x => x*x `


## 3、函数的调用

众所周知，函数的调用很简单，比如有这样一个函数
`function fn (){ return undefined; }` 
我们只需` fn(); ` 即可执行该函数。

但是作为初学者，更建议使用`call()`方法，比如有函数：
`function fn(x,y){ return x+y; }`
就可以这么调用：`fn.call(undefined,1,2) // 结果为3` 等价于这么写`fn(1,2)`
之所以建议初学者使用`call()`方法，因为这么写更便于理解`this`和`arguments`
比如上面的那句调用，`call()`的第一个参数就是`this`，后面的参数就是`arguments`

## 4、函数的常用属性和方法

- `name` 属性
每一个函数都有`name`属性，你以为`name`属性就真的是表示函数的名字而且很好理解吗？
明显答案是否定的，使用不同的函数声明方式，其`name`属性的值可能就不是你想象中的样子。下面举例说明：
```
// 具名函数的name属性 ，表示函数的名字
function fn1() {} 
fn1.name // "fn1"

// 匿名函数的name属性，指的是接收函数的变量名
var fn2 = function () {} 
fn2.name // "fn2"

// 下面这种声明方法，在外部获取不到fn4函数
// 注：fn3.name返回函数表达式的名字。注意，真正的函数名还是fn3，而fn4这个名字只在函数体内部可用。
var fn3 = function fn4(){} 
fn3.name // "fn4"

// 使用Function() 方法构造函数，函数的name属性值为"anonymous"
var fn5 = new Function()
fn5.name // "anonymous"

// 箭头函数的name属性，指的也是接收该函数的变量名
var fn6 = () => {}
fn6.name // "fn6"

```

- `length` 属性
函数的`length`属性返回函数预期传入的参数个数，即函数定义之中的参数个数。
如：
```
function f(a, b) {}
f.length // 2
```
上面代码定义了空函数f，它的length属性就是定义时的参数个数。不管调用时输入了多少个参数，length属性始终等于2。
注：`length`属性提供了一种机制，判断定义时和调用时参数的差异，以便实现面向对象编程的”方法重载“（overload）。

- `toString()` 方法
函数的`toString`方法返回一个字符串，内容是函数的源码，包括函数中的注释也会被打印出来。如：
```
function f() {
  var a = 1
/*  这是一个
  多行注释*/
}

f.toString()
//   "function f() {
//     var a = 1
//   /*  这是一个0
//     多行注释*/
//   }"
```

- `call()` 方法 见“ 3、函数的调用 ”小节

## 5、函数中的`this` 和 `arguments`
（本文只介绍this和arguments是什么，暂时不介绍他们的用法）
首先举个例子：
声明 `function fn(x,y){ return x+y }`
调用 ` fn.call( undefined , 1 ,2 ) `
其中 ，`undefined` 指的就是函数fn的`this` ，`1,2` 指的就是函数的`arguments`
注意：在普通模式下，this是undefined时，浏览器会将其变为`window`
在严格模式下，`this` 是 `undefined` ，打印出来的就是`undefined` 
举例：
```
// 普通模式下：
function f(){
    console.log(this)
}
f.call(1)  // Number {1}

// 严格模式下：
function f(){
    'use strict'
    console.log(this)
}
f.call(1)  // 1
```
即，**普通模式下，浏览器会把`this` 转化为对象，严格模式下会禁止这样的转换**。


## 6、call stack 调用栈
>"调用栈"（call stack）表示函数或子例程像堆积木一样存放，以实现层层调用。
举个函数嵌套调用的例子：
```
function a(){
    console.log('a1')
    b.call()
    console.log('a2')
  return 'a'  
}
function b(){
    console.log('b1')
    c.call()
    console.log('b2')
    return 'b'
}
function c(){
    console.log('c')
    return 'c'
}
a.call()
console.log('end')
```
其执行顺序如图所示：
![](https://upload-images.jianshu.io/upload_images/11827773-cad795aa0189b508.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下面是嵌套调用和递归调用时，函数的执行顺序：
*   [嵌套调用](http://latentflip.com/loupe/?code=ZnVuY3Rpb24gYSgpewogICAgY29uc29sZS5sb2coJ2ExJykKICAgIGIuY2FsbCgpCiAgICBjb25zb2xlLmxvZygnYTInKQogIHJldHVybiAnYScgIAp9CmZ1bmN0aW9uIGIoKXsKICAgIGNvbnNvbGUubG9nKCdiMScpCiAgICBjLmNhbGwoKQogICAgY29uc29sZS5sb2coJ2IyJykKICAgIHJldHVybiAnYicKfQpmdW5jdGlvbiBjKCl7CiAgICBjb25zb2xlLmxvZygnYycpCiAgICByZXR1cm4gJ2MnCn0KYS5jYWxsKCkKY29uc29sZS5sb2coJ2VuZCcp!!! "null")
*   [递归调用](http://latentflip.com/loupe/?code=ZnVuY3Rpb24gc3VtKG4pewogICAgaWYobj09MSl7CiAgICAgICAgcmV0dXJuIDEKICAgIH1lbHNlewogICAgICAgIHJldHVybiBuICsgc3VtLmNhbGwodW5kZWZpbmVkLCBuLTEpCiAgICB9Cn0KCnN1bS5jYWxsKHVuZGVmaW5lZCw1KQ%3D%3D!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D "null")


## 7、作用域

> 作用域（scope）指的是变量存在的范围。在 ES5 的规范中，Javascript 只有两种作用域：一种是全局作用域，变量在整个程序中一直存在，所有地方都可以读取；另一种是函数作用域，变量只在函数内部存在。ES6 又新增了块级作用域。

规则：
**按照语法树，就近原则**
**注意：我们只能确定变量是哪个变量，但是不能确定变量的值**

在判断作用域时，还要注意函数作用域内部会产生的“变量提升”现象。var命令声明的变量，不管在什么位置，变量声明都会被提升到函数体的头部。

## 8、什么是闭包
（本节只介绍闭包的概念，暂不深入，这里提供[方方的一篇介绍闭包的文章](https://zhuanlan.zhihu.com/p/22486908)用于深入了解）

如果一个函数使用了它范围外的变量，那么**（这个函数和这个变量）**就叫做**闭包**。

闭包（closure）是 Javascript 语言的一个难点，也是它的特色，很多高级应用都要依靠闭包实现。
理解闭包，首先必须理解变量作用域。前面提到，JavaScript 有两种作用域：全局作用域和函数作用域。函数内部可以直接读取全局变量。


## 9、一些易错的坑
看了这么多概念，觉得函数貌似也不太难呢？嘿嘿，那么请继续，下面将写一些函数中易错的坑。
- 题目1：求f1.call()的结果
```
var a = 1
function f1(){
    alert(a) // 是多少
    var a = 2
}
f1.call()
```

- 题目2：
 ```
var a = 1
function f1(){
    var a = 2
    f2.call()
}
function f2(){
    console.log(a) // 是多少
}
f1.call()
```

- 题目3：点击第3个 li 时，打印 2 还是打印 6？
```
var liTags = document.querySelectorAll('li')
for(var i = 0; i<liTags.length; i++){
    liTags[i].onclick = function(){
        console.log(i) // 点击第3个 li 时，打印 2 还是打印 6？
    }
}
```

- 题目4：这两个代码块的结果一样吗？
```
function f(){
    console.log(this)
}
f.call(1)
```
```
function f(){
    'use strict'
    console.log(this)
}
f.call(1)
```

- 题目5：下面的几个代码块，a的值分别为什么
```
var a = console.log(1);
```
```
function f(){
    return 1
}
a = f
```
```
function f(){
    return 1
}
var a = f.call()
```

- 题目6：下面的几个代码块，a的值分别为什么
```
var a = 1,2
```
```
var a = (1,2)
```
```
var a = (1, console.log(2))
```

- 题目7：
```
function f(){
    return function f2(){}
}
var a = f.call()
```
```
function f(){
    return function f2(){}
}
var a = f.call()
var b = a.call()
```
```
function f(){
    return function f2(){}
}
var a = f.call().call()
```

- 题目8：
```
function f1(){
    console.log(this)
    function f2(){

    }
}
var obj = {name: 'obj'}
f1.call( obj )
```
```
function f1(){

    function f2(){
        console.log(this)
    }
    f2.call()
}
var obj = {name: 'obj'}
f1.call( obj )
```

- 题目9：
```
function f1(){
    console.log(this) // 第一个 this
    function f2(){
        console.log(this) // 第二个 this
    }
    f2.call()
}
var obj = {name: 'obj'}
f1.call( obj )
为什么两个 this 值不一样？
```
本题答案：

=>每个函数都有自己的 this，为什么会一样？

=>this 就是 call 的第一个参数，第一个 this 对应的 call 是 f1.call(obj)，第二个 this 对应的 call 是 f2.call()

=>this 和 arguments 都是参数，参数都要在函数执行（call）的时候才能确定



