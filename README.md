*http://arcturo.github.com/library/coffeescript/02_syntax.html*

# Comment 注释
// 单行注释
```cs
# One line comment
```

// 多行注释
```cs
###
First line comment//
Second line comment
###
```

# Variable and scope 变量和空间
// 定义局域变量
```cs
hello = "world"
```
> [JS]

```js
var hello
hello = 'world'
```

// 定义全局变量
```cs
window.hello = "world"
```
> 或  

```cs
myGlobal = this
myGlobal.hello = "world"
```

> [JS]

```js
var myGlobal;
myGlobal = this;
myGlobal.hello = 'world'
```

# Functions 函数
// 定义一个函数
```cs
foo = -> "bar"
```

> [JS]

```js
var foo;
foo = function() {
  return 'bar';
}
```

// 定义一个多行函数
```cs
foo = ->
  # comment here
  hello = "world"
  hello  // 自动在最后一行代码前加上return, 也可以提前写上return
```

> [JS]

```js
var foo;
foo = function() {
  // comment here
  var hello;
  hello = 'world';
  return hello;
}
```

// 定义一个带有参数的函数
```cs
double = (num) -> num*2
```

> [JS]

```js
var double;
double = function(num) {
  return num*2;
}
```

// 给函数参数赋予默认值
```cs
double = (num=3) -> num*2
```

> [JS]

```js
var double;
double = function(num) {
  if (num == null) {
    num = 3;
  }
  return num*2;
}
```

// 定义一个匿名函数
```cs
(arg) -> alert arg
```

// 使用省略号来多参数赋值 ?

# Function invocation 函数调用

*[EN] parens 括弧*  

// 使用括弧调用
```cs
    hello = "world"
    alert(hello)
```

> [JS]

```js
    var hello;
    hello = 'world';
    alert(hello);
```

// 无括弧调用
```cs
hello = "world"
alert hello
```

// 无括弧多个函数调用
```cs
func arg  // func(arg)
func1 func2()  // func1(func2())
func1 func2 arg  // func1(func2(arg))
func1 func2(arg)  // 建议
func1 func2 func3(arg1, func4 func5(arg2))  // func1(func2(func3(arg1, func4(func5(arg2)))));
```

# Function context 函数域

*[EN] rife 普遍的*  
*[EN] variation 变种*  

// 使用'=>'让后面的函数块在本地域中执行:
```cs
this.localFunc = -> alert 'local func'
ele.addEventListener 'click', (e) -> this.localFunc(e)  // click触发的绑定函数会在ele域中执行
ele.addEventListener 'click', (e) => this.localFunc(e)  // click触发的绑定函数会在本地(this)域中执行 类似jQuery的proxy()
```

# Object & Array 对象和数组
## 定义一个对象
// 使用括弧
```cs
object1 = {foo: 'bar', hello: 'world'}
```

// 省略括弧
```cs
object2 = foo: 'bar', hello: 'world'
```

// 使用间距缩进
```cs
object3 =
  foo: 'bar'
  hello: 'world'
```

// 逗号','连接连续的foo: 'bar'这种形式会被编译成一个对象
```cs
a1: 'b1', a2: 'b2', a3: 'b3', a4: 'b4'
```

> [JS]

```js
{a1: 'b1', a2: 'b2', a3: 'b3', a4: 'b4'}
```

// 逗号','连接连续的foo: 'bar'这种形式被打断会被编译成3个变量
```cs
a1: 'b1', a2: 'b2', c1, a3: 'b3', a4: 'b4'
```

> [JS]

```js
{a1: 'b1', a2: 'b2'}, c1, {a3: 'b3', a4: 'b4'}
```

## 将对象传递给函数
```cs
func({name: 'John'})
func(name: 'John')
```

## 定义一个数组
```cs
arr1 = [a, b, c]
arr1 = [a, b, c,]  // 结尾存在逗号不报错
arr1 = [
  a
  b
  c
]
```

# Flow control 流程控制
// 单行 if 语句
```cs
if user.login == true then "User logged in" else "User is not login"
```

// 多行 if 语句
```cs
if user.login == true
  "User is loged in"
```

// if 置后
```cs
alert "It's cold!" if heat < 5
```

// not 关键词
```cs
if !login then "Sorry!"
if not login then "Sorry!"  // 替代 ! 符号
```

// unless 关键词
```cs
unless login then "Sorry!"  // if 的反义词
```

// is 关键词
```cs
if login === true then "Welcome!"
if login is true then "Welcome!"  // is 等于 === 全等于符号
```

// isnt 关键词
```cs
if login !== true then "Sorry!"
if login isnt true then "Sorry!"  // isnt 等于 !== 不全等于符号
```

> CoffeeScript 将 == 操作符转换为 ===, 将 != 操作符转换为 !==

# String 字符串连接
```cs
name = "Shallker Wang"
age = 22
introduce = "My name is #{name}
  and I'm #{age} years old.
  Thank you.
"
```

# Loops 循环和遍历
// for 循环
```cs
people = ["Jack", "John", "Peter"]
for name in people
  alert "Hi, #{name}"  // 前面至少有一个空格 不能与 for 段落并齐
```

// for 循环 获取当前索引
```cs
people = ["Jack", "John", "Peter"]
for name, i in people
  alert "Hi, #{name}, you're number #{i}"  // i 从0开始
```

// 一行 for 循环
```cs
alert name for name in ["Jack", "John", "Peter"]
```

// for 循环中的过滤 when 关键词
```cs
alert name for name in ["Jack", "David", "Peter"] when name[0] is "D"
```

// for of 遍历对象
```cs
user = {name: 'Jack', age: 22, sex: 1}
alert "#{attr}: #{val}" for attr, val of user
```

// while 关键词 ?

# 数组遍历
