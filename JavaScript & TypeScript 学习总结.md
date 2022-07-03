# JavaScript & TypeScript 学习总结

## JavaScript

### 一、简介

**JavaScript 是属于 HTML 和 Web 的编程语言。**

### 二、使用方法

1. 内部书写：书写在<script></script> 内部
2. 外部引用:应用外部的JS文件

```html
<!DOCTYPE html>
<html>
<!--2.外部引用-->
<script src="../js/register.js"></script>
<script src="https://mingcheng.js"></script>
    
<head>
<!--1.内部书写-->
<script>
function myFunction() {
    document.getElementById("demo").innerHTML = "段落被更改。";
}
</script>
</head>
<body>
</body>
</html>
```

### 三、语法基础

#### 1. 输出

- 使用 `window.alert()` 写入警告框

```html
<script>
window.alert(5 + 6);
</script>
```

- 使用 `document.write()` 写入 HTML 输出

​        	  1) 方法仅用于测试,

​			  2) 如果在文档已完成加载后执行 `document.write`，整个 HTML 页面将被**覆盖**,**删除所有已有的 HTML**

```html
<!--实例-->
<!DOCTYPE html>
<html>
<body>
<button onclick="myFunction()">点我</button>

<script>
function myFunction() {
    document.write(Date());
}
</script>
</body>
</html>
```

- 使用 `innerHTML` 写入 HTML 元素

​			 请使用 "id" 属性来标识 HTML 元素，并 innerHTML 来获取或插入元素内容

```html
<script>
document.getElementById("demo").innerHTML = "段落已修改。";
</script>
```



- 使用 `console.log()` 写入浏览器控制台

```html
<script>
a = 5;
b = 6;
c = a + b;
console.log(c);
</script>
```

#### 2. 声明变量

- 声明变量的方式 : **var**		**let**		**const** 

##### **全局作用域**

​		1) **全局**变量可以在 JavaScript 程序中的**任何位置**访问

```js
/****
var全局作用域的声明
****/
var  num = 1; 

// 外部可以使用num

function myFunction() {
  // 此处函数内部也可以使用外部的num
}
```

```js
/****
let全局作用域的声明
****/
let  num = 1; 

// 外部可以使用let

function myFunction() {
  // 此处函数内部也可以使用外部的num
}
```

##### **函数作用域**

​			1）*局部*（函数内）声明的变量拥有**函数作用域**

​			2）局部变量只能在它们被声明的**函数内**访问

```js
/****
var 函数作用域
****/
function myFunction() {
  var num = 1;
  // 函数内部可以使用num
}
// 函数外部不可以使用num
```

```js
/****
let 函数作用域
****/

function myFunction() {
  let num = 1;
  // 函数内部可以使用num
}
// 函数外部不可以使用num
```

##### **块作用域**

​			1) 在块 *{}* 内声明的变量可以从块之外进行访问

```js
{ 
  var num = 10; 
}
// 此处可以使用 num
```

```js
{ 
  let x = 10;
}
// 此处不可以使用 x
```

##### **重声明变量**

```js
/* 问题： var 在块中重新声明变量也将重新声明块外的变量*/
var num = 10;
// 此处 num 为 10
{ 
  var num = 6;
  // 此处 num 为 6
}
// 此处 num 为 6
```

```js
/* 
	1. 使用 let 关键字重新声明变量可以解决这个问题
	2. 在块中重新声明变量不会重新声明块外的变量
*/
var num = 10;
// 此处 num 为 10
{ 
  let num = 6;
  // 此处 num 为 6
}
// 此处 num 为 10
```

##### 循环作用域

```js
var i = 7;
for (var i = 0; i < 10; i++) {
  // 一些语句
}
// 此处，i 为 10
```

```js
let i = 7;
for (let i = 0; i < 10; i++) {
  // 一些语句
}
// 此处 i 为 7
```



#### 3. 计算赋值

- 常用运算符

| 运算符 | 描述         |
| ------ | ------------ |
| +      | 加法         |
| -      | 减法         |
| *      | 乘法         |
| /      | 除法         |
| %      | 取模（余数） |
| ++     | 递加         |
| --     | 递减         |
| =      | 赋值等于     |
| ==     | 等值比较     |
| ===    | 等值等型比较 |
| ！     | 取非         |
| &&     | 与运算       |
| \|\|   | 或运算       |

#### 4. 数据类型

##### 声明数据类型

```js
var length = 7;                             // 数字
var lastName = "Gates";                      // 字符串
var cars = ["Porsche", "Volvo", "BMW"];         // 数组
var x = {firstName:"Bill", lastName:"Gates"};    // 对象
```

##### **查看数据类型**

| 运算符     | 描述                                         |
| ---------- | -------------------------------------------- |
| typeof     | 确定 JavaScript 变量的数据类型 typeiof(数据) |
| instanceof | 返回 true，如果对象是对象类型的实例。        |

##### 具体数据类型

| 数据类型名称 | 描述              |
| ------------ | ----------------- |
| string       | 字符串            |
| number       | 数值              |
| boolean      | 布尔值            |
| object       | 对象              |
| function     | 函数              |
| undefined    | 未定义            |
| null         | 空值 （属于对象） |

##### 数据类型转换

| 方法        | 描述           |
| ----------- | -------------- |
| `Number()`  | **转换数值**   |
| `String()`  | **转换字符串** |
| `Boolean()` | **转换布尔值** |

#### 5. 字符串

##### 字符串方法

| 方法名                        | 描述                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| **str.length**                | 返回字符串的长度                                             |
| **indexOf(str)**              | 返回字符串中指定文本*首次*出现的索引（位置） 未找到文本返回-1 **不可用正则表达式** |
| **lastIndexOf(str)**          | 回指定文本在字符串中*最后*一次出现的索引  未找到文本返回-1   |
| **search(str)**               | 搜索特定值的字符串，并返回匹配的位置   **可用正则表达式**    |
| **slice(*start*, *end*)**     | 提取字符串的某个部分并在新字符串中返回被提取的部分 可以用**负数索引**从**字符串结尾计算位置** 提取字符串，可以必须要end表示裁剪字符串的**剩余部分** |
| **substring(*start*, *end*)** | `substring()` 类似于 `slice()`。不同之处在于 `substring()` 无法接受负的索引 |
| **substr(*start*, *length*)** | `substr` 类似于` slice()`，第二个参数规定被提取部分的*长度*  接受负的索引 |
| **match(regexp)**             | 根据正则表达式在字符串中搜索匹配项，并将匹配项作为 Array 对象返回 |
| **includes()**                | 如果字符串包含指定值**返回 true**                            |

##### 字符串模板

- 使用方法 反引号 (``)  

```js
let text = `Hello World!`
```

- 字符串插值 $

```js
/*
1. 使用${表达式}
2. 使用${变量名}
*/

let price = 10;
let VAT = 0.25;

let total = `Total: ${(price * (1 + VAT)).toFixed(2)}`;

```

#### 6. 数组

##### 创建数组

```js
/***
1. 直接数组文本
2. 直接Array对象创建
注意：效果一样  简洁、可读性和执行速度上第一种更好
***/

var cars = ["Saab", "Volvo", "BMW"];

var cars = new Array("Saab", "Volvo", "BMW");
```

##### 数组常用方法

| 方法名                      | 描述                                                         |
| --------------------------- | ------------------------------------------------------------ |
| **toString()**              | 把数组转换为数组值（逗号分隔）的字符串                       |
| **join(str)**               | 将所有数组元素结合为一个字符串,并且将str作为分隔符           |
| **pop()**                   | 删除数组最后一个元素 并返回“被删除”的值                      |
| **push(parame)**            | 在数组结尾处 向数组添加一个新的元素parame                    |
| **shift()**                 | 删除**首个数组元素**，并把所有其他元素“位移”到更低的索引  **返回被“位移出”的字符串** |
| **unshift()**               | 向**数组开头**添加新元素，并“反向位移”旧元素   **返回新数组的长度** |
| **length**                  | 返回数组的长度                                               |
| **splice(start,num,p1,p2)** | 向数组添加新项 (start:添加新元素位置  num：应删除的元素数量  p1,p2:要添加的新元素) **返回处理以后的数组** |
| **concat(str1,str2,str3)**  | 不会更改现有数组 返回一个拼接过后的**新数组**                |
| **slice()**                 | 用数组的某个片段切出新数组                                   |

##### 数组迭代

- foreach()

```js
<!--
接收三个参数： 项目值 项目索引 数组本身
-->
var txt = "";
var numbers = [45, 4, 9, 16, 25];
numbers.forEach(myFunction);

function myFunction(value, index, array) {
  txt = txt + value + "<br>"; 
}
```



#### 6. 函数

- 通过**function**定义

```js
function name(参数 1, 参数 2, 参数 3) {
    要执行的代码
}
```



#### 7. 对象

- 创建对象

```js
var car = {type:"porsche", model:"911", color:"white"};
```

- 对象方法

```js
var person = {
  firstName: "Bill",
  lastName : "Gates",
  id       : 678,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```

- 访问对象属性

```js
1. objectName.propertyName
2. objectName["propertyName"] 
```

### 四、JS DOM

#### 1. 操作元素方法

##### 获取元素

| 方法名                                  | 描述                   |
| --------------------------------------- | ---------------------- |
| document.getElementById(*id*)           | 通过元素 id 来查找元素 |
| document.getElementsByTagName(*name*)   | 通过标签名来查找元素   |
| document.getElementsByClassName(*name*) | 通过类名来查找元素     |
| document.querySelectorAll(name);        | 通过CSS选择器查找元素  |

##### 改变元素内容

| 方法名                                     | 描述                   |
| ------------------------------------------ | ---------------------- |
| element.innerHTML = *new html content*     | 改变元素的 inner HTML  |
| element.attribute = *new value*            | 改变 HTML 元素的属性值 |
| element.setAttribute(*attribute*, *value*) | 改变 HTML 元素的属性值 |
| element.style.property = *new style*       | 改变 HTML 元素的样式   |



##### 删除或添加元素

| 方法名                            | 描述             |
| --------------------------------- | ---------------- |
| document.createElement(*element*) | 创建 HTML 元素   |
| document.removeChild(*element*)   | 删除 HTML 元素   |
| document.appendChild(*element*)   | 添加 HTML 元素   |
| document.replaceChild(*element*)  | 替换 HTML 元素   |
| document.write(*text*)            | 写入 HTML 输出流 |



##### 添加事件处理

| 方法名                                                   | 描述                            |
| -------------------------------------------------------- | ------------------------------- |
| document.getElementById(id).onclick = function(){*code*} | 向 onclick 事件添加事件处理程序 |

#### 2.  表单验证

```js
function validateForm() {
  let x = document.forms["myForm"]["fname"].value;
  if (x == "") {
    alert("Name must be filled out");
    return false;
  }
}
```

```html
<form name="myForm" action="/action_page.php" onsubmit="return validateForm()" method="post">
Name: <input type="text" name="fname">
<input type="submit" value="Submit">
</form>
```

#### 3. DOM事件

##### 基本事件

- 鼠标事件

```html
<!--
1. onmousedown, onmouseup 以及 onclick 事件构成了完整的鼠标点击事件。
2. 首先当鼠标按钮被点击时，onmousedown 事件被触发；然后当鼠标按钮被释放时，onmouseup 事件被触发；最后，当鼠标点击完成后，onclick 事件被触发。
-->
<!DOCTYPE html>
<html>
<body>

<div onmousedown="mDown(this)" onmouseup="mUp(this)"
style="background-color:#D94A38;width:90px;height:20px;padding:40px;">
点击鼠标</div>

<script>
function mDown(obj) {
  obj.style.backgroundColor = "#1ec5e5";
  obj.innerHTML = "松开鼠标";
}

function mUp(obj) {
  obj.style.backgroundColor="#D94A38";
  obj.innerHTML="谢谢您";
}
</script>

</body>
</html>
```

- onload 和 onunload 事件

```html
<!--
1. 当用户进入后及离开页面时，会触发 onload 和 onunload 事件
2. onload 和 onunload 事件可用于处理 cookie
-->

<body onload="checkCookies()">
```

- onchange 事件

```html
<!--
1. onchange 事件经常与输入字段验证结合使用
-->

<input type="text" id="fname" onchange="upperCase()">
```



- onmouseover 和 onmouseout 事件

```html
<!--
1. onmouseover 和 onmouseout 事件可用于当用户将鼠标移至 HTML 元素上或移出时触发某个函数
-->
<!DOCTYPE html>
<html>
<body>

<div onmouseover="mOver(this)" onmouseout="mOut(this)" 
style="background-color:#D94A38;width:120px;height:20px;padding:40px;">
请把鼠标移上来</div>

<script>
function mOver(obj) {
  obj.innerHTML = "谢谢您"
}

function mOut(obj) {
  obj.innerHTML = "请把鼠标移上来"
}
</script>

</body>
</html>
```

##### 事件监听

- 语法

```js
// 1.addEventListener() 方法为指定元素指定事件处理程序
// 2.addEventListener() 方法为元素附加事件处理程序而不会覆盖已有的事件处理程序。
element.addEventListener(event, function, useCapture);
```

- 向相同元素添加多个事件处理程序

```js
element.addEventListener("click", myFunction);
element.addEventListener("click", mySecondFunction);
```

- 向 Window 对象添加事件处理程序

```js
window.addEventListener("resize", function(){
    document.getElementById("demo").innerHTML = sometext;
});
```

- 事件冒泡与事件捕获

```js
// 1.在 addEventListener() 方法中，你能够通过使用“useCapture”参数来规定传播类型：
// 2. 默认值是 false，将使用冒泡传播，如果该值设置为 true，则事件使用捕获传播

document.getElementById("myP").addEventListener("click", myFunction, true);
document.getElementById("myDiv").addEventListener("click", myFunction, true);

```

- removeEventListener() 方法

```js
element.removeEventListener("mousemove", myFunction);
```

## TypeScript

### 一、简介

- TypeScript 是一种给 JavaScript 添加特性的语言扩展。增加的功能包括
- 它对JS进行了扩展，向JS中引入了类型的概念，并添加了许多新的特性
- TS代码需要通过编译器编译为JS，然后再交由JS解析器执行。
- TS完全兼容JS，换言之，任何的JS代码都可以直接当成JS使用。
- 相较于JS而言，TS拥有了静态类型，更加严格的语法，更强大的功能；TS可以在代码执行前就完成代码的检查，减小了运行时异常的出现的几率；TS代码可以编译为任意版本的JS代码，可有效解决不同JS运行环境的兼容问题；同样的功能，TS的代码量要大于JS，但由于TS的代码结构更加清晰，变量类型更加明确，在后期代码的维护中TS却远远胜于JS。

### 二、开发环境的搭建

- npm安装

```
npm install -g typescript
```

- 查看版本

```
$ tsc -v
Version 3.2.2
```

- 将 TypeScript 转换为 JavaScript 代码

```
tsc app.ts
```

### 三、基本类型

##### 1. 类型声明

- 类型声明是TS非常重要的一个特点
- 通过类型声明可以指定TS中变量（参数、形参）的类型
- 指定类型后，当为变量赋值时，TS编译器会自动检查值是否符合类型声明，符合则赋值，否则报错
- 简而言之，类型声明给变量设置了类型，使得变量只能存储某种类型的值
- 语法：

```tsx
let 变量: 类型;

let 变量: 类型 = 值;

function fn(参数: 类型, 参数: 类型): 类型{
    ...
}
```

##### 2.  自动类型判断

- TS拥有自动的类型判断机制

- 当对变量的声明和赋值是同时进行的，TS编译器会自动判断变量的类型

- 所以如果你的变量的声明和赋值时同时进行的，可以省略掉类型声明

- 有些情况下，变量的类型对于我们来说是很明确，但是TS编译器却并不清楚，此时，可以通过类型断言来告诉编译器变量的类型，断言有两种形式：

  - ```tsx
    // 第一种
    let someValue: unknown = "this is a string";
    let strLength: number = (someValue as string).length;
    ```

  - ```tsx
    // 第二种
    let someValue: unknown = "this is a string";
    let strLength: number = (<string>someValue).length;
    ```

##### 3. 类型

| 类型    | 例子              | 描述                           |
| ------- | ----------------- | ------------------------------ |
| number  | 1, -33, 2.5       | 任意数字                       |
| string  | 'hi', "hi", `hi`  | 任意字符串                     |
| boolean | true、false       | 布尔值true或false              |
| 字面量  | 其本身            | 限制变量的值就是该字面量的值   |
| any     | *                 | 任意类型                       |
| unknown | *                 | 类型安全的any                  |
| void    | 空值（undefined） | 没有值（或undefined）          |
| never   | 没有值            | 不能是任何值                   |
| object  | {name:'孙悟空'}   | 任意的JS对象                   |
| array   | [1,2,3]           | 任意JS数组                     |
| tuple   | [4,5]             | 元素，TS新增类型，固定长度数组 |
| enum    | enum{A, B}        | 枚举，TS中新增类型             |

- number

```tsx
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
let big: bigint = 100n;
```

- boolean

```tsx
let isDone: boolean = false;
```

- string

```tsx
let color: string = "blue";
color = 'red';

let fullName: string = `Bob Bobbington`;
let age: number = 37;
let sentence: string = `Hello, my name is ${fullName}.

I'll be ${age + 1} years old next month.`;
```

- 字面量

```tsx
// 也可以使用字面量去指定变量的类型，通过字面量可以确定变量的取值范围
let color: 'red' | 'blue' | 'black';
let num: 1 | 2 | 3 | 4 | 5;
```

- any

```tsx
let d: any = 4;
d = 'hello';
d = true;
```

- unknown

```tsx
let notSure: unknown = 4;
notSure = 'hello';
```

- void

```tsx
let unusable: void = undefined;
```

- never

```tsx
function error(message: string): never {
  throw new Error(message);
}
```

- array

```tsx
let list: number[] = [1, 2, 3];
let list: Array<number> = [1, 2, 3];
```

- tuple

```tsx
let x: [string, number];
x = ["hello", 10]; 
```

- enum

```tsx
enum Color {
  Red,
  Green,
  Blue,
}
let c: Color = Color.Green;

enum Color {
  Red = 1,
  Green,
  Blue,
}
let c: Color = Color.Green;

enum Color {
  Red = 1,
  Green = 2,
  Blue = 4,
}
let c: Color = Color.Green;
```

#### 四、面向对象

##### 1. 类

​	要想面向对象，操作对象，首先便要拥有对象，那么下一个问题就是如何创建对象。要创建对象，必须要先定义类，所谓的类可以理解为对象的模型，程序中可以根据类创建指定类型的对象，举例来说：可以通过Person类来创建人的对象，通过Dog类创建狗的对象，通过Car类来创建汽车的对象，不同的类可以用来创建不同的对象。

- 定义类

```tsx
class 类名 {
	属性名: 类型;
	
	constructor(参数: 类型){
		this.属性名 = 参数;
	}
	
	方法名(){
		....
	}

}
```

- 示例

```tsx
class Person{
    name: string;
    age: number;

    constructor(name: string, age: number){
        this.name = name;
        this.age = age;
    }

    sayHello(){
        console.log(`大家好，我是${this.name}`);
    }
}

```

- 使用类

```tsx
const p = new Person('孙悟空', 18);
p.sayHello();
```

##### 2. 面向对象的特点

###### 封装

- 对象实质上就是属性和方法的容器，它的主要作用就是存储属性和方法，这就是所谓的封装


- 默认情况下，对象的属性是可以任意的修改的，为了确保数据的安全性，在TS中可以对属性的权限进行设置
  - 只读属性（readonly）：

    - 如果在声明属性时添加一个readonly，则属性便成了只读属性无法修改


- TS中属性具有三种修饰符：

  - public（默认值），可以在类、子类和对象中修改
    - protected ，可以在类、子类中修改
    - private ，可以在类中修改


- 示例：

  - public

    - ```tsx
      class Person{
          public name: string; // 写或什么都不写都是public
          public age: number;
      
          constructor(name: string, age: number){
              this.name = name; // 可以在类中修改
              this.age = age;
          }
      
          sayHello(){
              console.log(`大家好，我是${this.name}`);
          }
      }
      
      class Employee extends Person{
          constructor(name: string, age: number){
              super(name, age);
              this.name = name; //子类中可以修改
          }
      }
      
      const p = new Person('孙悟空', 18);
      p.name = '猪八戒';// 可以通过对象修改
      ```

  - protected

    - ```tsx
      class Person{
          protected name: string;
          protected age: number;
      
          constructor(name: string, age: number){
              this.name = name; // 可以修改
              this.age = age;
          }
      
          sayHello(){
              console.log(`大家好，我是${this.name}`);
          }
      }
      
      class Employee extends Person{
      
          constructor(name: string, age: number){
              super(name, age);
              this.name = name; //子类中可以修改
          }
      }
      
      const p = new Person('孙悟空', 18);
      p.name = '猪八戒';// 不能修改
      ```

  - private

    - ```typescript
      class Person{
          private name: string;
          private age: number;
      
          constructor(name: string, age: number){
              this.name = name; // 可以修改
              this.age = age;
          }
      
          sayHello(){
              console.log(`大家好，我是${this.name}`);
          }
      }
      
      class Employee extends Person{
      
          constructor(name: string, age: number){
              super(name, age);
              this.name = name; //子类中不能修改
          }
      }
      
      const p = new Person('孙悟空', 18);
      p.name = '猪八戒';// 不能修改
      ```

- 属性存取器

  - 对于一些不希望被任意修改的属性，可以将其设置为private

  - 直接将其设置为private将导致无法再通过对象修改其中的属性

  - 我们可以在类中定义一组读取、设置属性的方法，这种对属性读取或设置的属性被称为属性的存取器

  - 读取属性的方法叫做setter方法，设置属性的方法叫做getter方法

  - 示例：

    - ```typescript
      class Person{
          private _name: string;
      
          constructor(name: string){
              this._name = name;
          }
      
          get name(){
              return this._name;
          }
      
          set name(name: string){
              this._name = name;
          }
      
      }
      
      const p1 = new Person('孙悟空');
      console.log(p1.name); // 通过getter读取name属性
      p1.name = '猪八戒'; // 通过setter修改name属性
      ```

- 静态属性

  - 静态属性（方法），也称为类属性。使用静态属性无需创建实例，通过类即可直接使用

  - 静态属性（方法）使用static开头

  - 示例：

    - ```typescript
      class Tools{
          static PI = 3.1415926;
          
          static sum(num1: number, num2: number){
              return num1 + num2
          }
      }
      
      console.log(Tools.PI);
      console.log(Tools.sum(123, 456));
      ```

- this

  - 在类中，使用this表示当前对象

###### 继承

- 继承时面向对象中的又一个特性

- 通过继承可以将其他类中的属性和方法引入到当前类中

  - 示例：

    - ```typescript
      class Animal{
          name: string;
          age: number;
      
          constructor(name: string, age: number){
              this.name = name;
              this.age = age;
          }
      }
      
      class Dog extends Animal{
      
          bark(){
              console.log(`${this.name}在汪汪叫！`);
          }
      }
      
      const dog = new Dog('旺财', 4);
      dog.bark();
      ```

- 通过继承可以在不修改类的情况下完成对类的扩展

- 重写

  - 发生继承时，如果子类中的方法会替换掉父类中的同名方法，这就称为方法的重写

  - 示例：

    - ```typescript
      class Animal{
          name: string;
          age: number;
      
          constructor(name: string, age: number){
              this.name = name;
              this.age = age;
          }
      
          run(){
              console.log(`父类中的run方法！`);
          }
      }
      
      class Dog extends Animal{
      
          bark(){
              console.log(`${this.name}在汪汪叫！`);
          }
      
          run(){
              console.log(`子类中的run方法，会重写父类中的run方法！`);
          }
      }
      
      const dog = new Dog('旺财', 4);
      dog.bark();
      ```

    - 在子类中可以使用super来完成对父类的引用

###### 抽象类（abstract class）

- 抽象类是专门用来被其他类所继承的类，它只能被其他类所继承不能用来创建实例

- ```typescript
  abstract class Animal{
      abstract run(): void;
      bark(){
          console.log('动物在叫~');
      }
  }
  
  class Dog extends Animals{
      run(){
          console.log('狗在跑~');
      }
  }
  ```

- 使用abstract开头的方法叫做抽象方法，抽象方法没有方法体只能定义在抽象类中，继承抽象类时抽象方法必须要实现

##### 3. 接口（Interface）

​	接口的作用类似于抽象类，不同点在于接口中的所有方法和属性都是没有实值的，换句话说接口中的所有方法都是抽象方法。接口主要负责定义一个类的结构，接口可以去限制一个对象的接口，对象只有包含接口中定义的所有属性和方法时才能匹配接口。同时，可以让一个类去实现接口，实现接口时类中要保护接口中的所有属性。

- 示例（检查对象类型）：

  - ```typescript
    interface Person{
        name: string;
        sayHello():void;
    }
    
    function fn(per: Person){
        per.sayHello();
    }
    
    fn({name:'孙悟空', sayHello() {console.log(`Hello, 我是 ${this.name}`)}});
    ```

- 示例（实现）

  - ```typescript
    interface Person{
        name: string;
        sayHello():void;
    }
    
    class Student implements Person{
        constructor(public name: string) {
        }
    
        sayHello() {
            console.log('大家好，我是'+this.name);
        }
    }
    ```

##### 4. 泛型（Generic）

​	定义一个函数或类时，有些情况下无法确定其中要使用的具体类型（返回值、参数、属性的类型不能确定），此时泛型便能够发挥作用

- 举个例子：

  - ```typescript
    function test(arg: any): any{
    	return arg;
    }
    ```

    上例中，test函数有一个参数类型不确定，但是能确定的时其返回值的类型和参数的类型是相同的，由于类型不确定所以参数和返回值均使用了any，但是很明显这样做是不合适的，首先使用any会关闭TS的类型检查，其次这样设置也不能体现出参数和返回值是相同的类型

- 使用泛型：

- ```typescript
  function test<T>(arg: T): T{
  	return arg;
  }
  ```

- 这里的```<T>```就是泛型，T是我们给这个类型起的名字（不一定非叫T），设置泛型后即可在函数中使用T来表示该类型。所以泛型其实很好理解，就表示某个类型。

- 那么如何使用上边的函数呢？

  - 方式一（直接使用）：

    - ```typescript
      test(10)
      ```

    - 使用时可以直接传递参数使用，类型会由TS自动推断出来，但有时编译器无法自动推断时还需要使用下面的方式

  - 方式二（指定类型）：

    - ```typescript
      test<number>(10)
      ```

    - 也可以在函数后手动指定泛型

- 可以同时指定多个泛型，泛型间使用逗号隔开：

  - ```typescript
    function test<T, K>(a: T, b: K): K{
        return b;
    }
    
    test<number, string>(10, "hello");
    ```

  - 使用泛型时，完全可以将泛型当成是一个普通的类去使用

- 类中同样可以使用泛型：

  - ```typescript
    class MyClass<T>{
        prop: T;
    
        constructor(prop: T){
            this.prop = prop;
        }
    }
    ```

- 除此之外，也可以对泛型的范围进行约束

  - ```typescript
    interface MyInter{
        length: number;
    }
    
    function test<T extends MyInter>(arg: T): number{
        return arg.length;
    }
    ```

  - 使用T extends MyInter表示泛型T必须是MyInter的子类，不一定非要使用接口类和抽象类同样适用。

