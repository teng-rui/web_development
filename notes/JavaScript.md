# JavaScript 用法

```javascript
/*change element content*/
//如果不被事件触发，必须在定义demo标签之后，否则被demo本身内容覆盖
document.getElementById("demo").innerHTML = "Hello JavaScript";
document.getElementById('demo').innerHTML = 'Hello JavaScript';

/*change attribute value*/
document.getElementById('myImage').src='pic_bulboff.gif'
<button onclick="document.getElementById('myImage').src='pic_bulboff.gif'">
/*change style*/
document.getElementById("demo").style.fontSize = "35px";
```



# JavaScript位置

Note：Putting your scripts at the bottom of the page body lets the browser load the page first. Or use `defer="true"` in the script tag.

## Internal JavaScript

HTML 中的脚本必须位于 < script> 与 < /script> 标签之间。

脚本可被放置在 HTML 页面的 < body> 和 < head> 部分中。

```html
<head>
<script>
function myFunction() {
  document.getElementById("demo").innerHTML = "Paragraph changed.";
}
</script>
</head>

<body>
<h2>Demo JavaScript in Head</h2>

<p id="demo">A Paragraph</p>
<button type="button" onclick="myFunction()">Try it</button>

</body>
```

## External JavaScript

外部 JavaScript 文件的文件扩展名是 .js。

```javascript
function myFunction()
{
    document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
}
//外部 javascript 文件不使用 <script> 标签，直接写 javascript 代码。
```

如需使用外部文件，请在 <script> 标签的 "src" 属性中设置该 .js 文件,src的value可为url或路径：

```html
<body>
<script src="https://www.w3schools.com/js/myScript.js"></script>
</body> 放在head也行
```

使用多个script标签来使用多个script外部文件

```html
<script src="myScript1.js"></script>
<script src="myScript2.js"></script>
```



# JavaScript 输出

JavaScript 可以通过不同的方式来输出数据：

- 使用 **window.alert()** 弹出警告框。In JavaScript, the **window** object is the **global scope object.** This means that variables, properties, and methods by default belong to the window object. This also means that specifying the `window` keyword is optional:

```html
<script>
window.alert(5 + 6);
alert(5 + 6);
</script>
```

- 使用 **document.write()** 方法将内容写到 HTML 文档中。The document.write() method should **only be used for testing**.

```html
<script>
document.write(Date());
</script>
Using document.write() after an HTML document is loaded, will delete all existing HTML:
不能用在函数中，会覆盖整个页面
<button type="button" onclick="document.write(5 + 6)">Try it</button>
html is already loaded, if we click button now, the document will be overrided.
```

- 使用 **innerHTML** 写入到 HTML 元素。

```html
<p id="demo">我的第一个段落</p>

<script>
document.getElementById("demo").innerHTML = "段落已修改。";
</script>
```

- 使用 **console.log()** 写入到浏览器的控制台。

```html
<script>
    a = 5;
    b = 6;
    c = a + b;
    console.log(c);
</script>
```

# JavaScript 语法

`;`结束一句statement, 可以直接断开一句statement到两行，只看分号在哪结束。

`//` `/* */` 注释

JavaScript 使用 Unicode 字符集。

您可以在**文本字符串中**使用反斜杠 \ 对代码行进行换行

## JavaScript **Literals**字面量

在编程语言中，一般固定值称为字面量，如 3.14。

**数字（number）字面量** 可以是整数或者是小数，或者是科学计数(e) 123e5。

**字符串（string）字面量** 可以使用单引号或双引号: "John Doe" 'John Doe'

**表达式字面量** 用于计算：5 + 6

**数组（Array）字面量** 定义一个数组：[40, 100, 1, 5, 25, 10]

**对象（Object）字面量** 定义一个对象：{firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}

**函数（Function）字面量** 定义一个函数：function myFunction(a, b) { return a * b;}

## JavaScript 变量

在编程语言中，变量用于存储数据值。Identifiers变量名

- Identifiers必须以字母开头
- Identifiers也能以 $ 和 _ 符号开头（不过我们不推荐这么做）
- Identifiers, 关键字都对大小写敏感（y 和 Y 是不同的变量）
- **camelCase**

JavaScript 使用关键字 **var** **let** 来declare变量， 使用等号来为变量assign value：var x; x = 5;

const 声明常量，不能被更改，`const` variables must be assigned a value when they are declared。

```javascript
var lastname="Doe", age=30, job="carpenter";

var lastname="Doe",
age=30,
job="carpenter"; //代码也可横跨多行：

var x,y,z=1; //x,y 为 undefined， z 为 1。

//let const变量不能被重新声明 in the same block，var variable can be redeclared in any where. 如果重新声明 var声明的变量，该变量的值不会丢失：变量 carname 的值依然是 "Volvo"：
var carname="Volvo";
var carname;
```

**局部 JavaScript 变量**

在 JavaScript 函数内部声明的变量（使用 var）是*局部*变量，所以只能在函数内部访问它。（该变量的作用域是局部的）。

函数参数只在函数内起作用，是局部变量。

您可以在不同的函数中使用名称相同的局部变量，因为只有声明过该变量的函数才能识别出该变量。

------

**全局 JavaScript 变量**

在函数外声明的变量是*全局*变量，**网页上的所有脚本和函数**都能访问它。

With JavaScript, the global scope is the JavaScript environment. In HTML, the default **global object** is the HTML page itself, In a browser the page object is the **browser window.**

Global variables defined with the `var` keyword belong to the global object(window). window.variablename;

Global variables can be used (and changed) by all other scripts in the page. So dont use global variable. they can be changed by any function.

如果变量在函数内没有声明（没有使用 var 关键字），该变量为全局变量。

```javascript
// 此处可调用 carName 变量
function myFunction() {
    carName = "Volvo";
    // 此处可调用 carName 变量
}
```

------

**Block Scope**

let const provide **Block Scope** in JavaScript.Variables declared inside a { } block cannot be accessed from outside the block:

局部变量和block scope 变量会覆盖全局变量。

```js
{
  let x = 2;
}
// x can NOT be used here
```

**JavaScript 变量的生存期**

JavaScript 变量的生命期从它们被声明的时间开始。

局部变量会在函数运行以后被删除。

全局变量会在页面关闭后被删除。

**const array and const object**

const does not define a constant value. It defines a constant reference to a value.Because of this you can NOT: Reassign a constant variables, but you can, change the elements of constant array, change the properties of constant object.

```js
// You can create a constant array:
const cars = ["Saab", "Volvo", "BMW"];

// You can change an element:
cars[0] = "Toyota";

// You can create a const object:
const car = {type:"Fiat", model:"500", color:"white"};

// You can change a property:
car.color = "red";

// You can add a property:
car.owner = "Johnson";
```



## JavaScript 操作符

算术运算符 Arithmetic Operators 

```
+ - * / %（division remainder） ++ --
The + operator performs concatenation operation when one of the operands is of string type.
5+'s' -> '5s'
5+5+'s' ->'10s'
```

赋值运算符 

```
= += -= *= /= %= **=
```

位运算符

条件运算符 Comparison Operators

```js
== != > < >= <= //(comparison of value without considerng type)
=== //(compares equality with type) 
！== //不绝对等于（值和类型有一个不相等，或两个都不相等）
?	//ternary operator 三元运算:variablename=(condition)?value1:value2
??  //Nullish Coalescing Operator: variablename=value1??value2, if value1 is null or undefiend, return value 2, otherwise return value1
```

逻辑运算符

```
&& || !
```

类型运算符

```js
typeof	Returns the type of a variable: typeof 3.14 
instanceof	Returns true if an object is an instance of an object type
```





# JavaScript 数据类型

**值类型(基本类型 primitive, no property or method)**：字符串（string）、数字(number)、布尔(boolean)、未定义（undefined）、对空（Null）、symbol、bigint。

**引用数据类型**：对象(Object)、数组(Array)、函数(Function),Date, Regex,Set Map。

- JavaScript vairbales has dynamic types. This means that the same variable can be used to hold different data types.

- 布尔（逻辑）只能有两个值：true 或 false

- undefiend is not empty value. 

  - let car = "";  // The value is "", the typeof is "string"
  - let car; or let car = undefined; // Value is undefined, type is undefined 

- JavaScript引擎在遇到声明语句时，会在栈中申请一个空间，当给这个变量赋值时，会有两种情况：

  - 如果值的类型是Boolean、Null、Undefined、Number，那么直接把这个值保存在栈中，以后可以更改
  - 如果是其他类型的值，JavaScript引擎会在堆中申请一个内存空间，然后把这个值保存在堆中，再将这个值在堆中的引用赋值给这个值在栈中的内存空间

  - object array function类型可以重新赋值，即重新开创堆里的内存，将新地址赋给栈。但最好用const,不可以改变地址，不能重赋值，只能改变堆内存的内容（改变成员）。
  - string 重新赋值时重新开创堆里的内存，并将新地址赋给string在栈中的内存，不能将原 堆地址改变值。https://juejin.cn/post/6844904200002863118
  - 不同block或局部变量的同名变量，不属于重新赋值，是不同变量

- Primitive values, like "John Doe", cannot have properties or methods (because they are not objects).

  But with JavaScript, **methods and properties are also available to primitive values**, because JavaScript treats primitive values as objects when executing methods and properties.

-  JavaScript has object versions of the primitive data types `String`, `Number`, and `Boolean`. But there is no reason to create complex objects. primitive values are much faster:

  Use string literals `""` instead of `new String()`.

  Use number literals `50` instead of `new Number()`.

  Use boolean literals `true / false` instead of `new Boolean()`.

  Also using literal to create object array function is faster:

  Use object literals `{}` instead of `new Object()`.

  Use array literals `[]` instead of `new Array()`.

  Use pattern literals `/()/` instead of `new RegExp()`.

  Use function expressions `() {}` instead of `new Function()`.

## Javascript Function

```
function myFunction(a, b=2) {
    return a * b;                                // 返回 a 乘以 b 的结果
}

var myVar=myFunction(2，3);
document.getElementById("demo").innerHTML=myFunction(2，3);

//单独使用return使程序退出函数，无返回值
```

- A function expression can be stored in a variable:**anonymous function** (a function without a name).They are always invoked (called) using the variable name.

```
const x = function (a, b) {return a * b}; 
let z = x(4, 3);
```

-  JavaScript functions can be called before they are declared. 

- **Arrow Function**

  - Arrow functions  `this` always represent the object that define it (window). They are not suited for defining **object methods**.
  - Arrow functions are not hoisted. They must be defined **before** they are used.
  - Using `const` is safer than using `var`, because a function expression is always constant value.
  - You can only omit the `return` keyword and the curly brackets if the function is a single statement. Because of this, it might be a good habit to always keep them

  ```
  // ES5
  var x = function(x, y) {
    return x * y;
  }
  
  // ES6
  const x = (x, y) => x * y;
  const x = (x, y) => { return x * y };
  ```

### **Parameters**

- JavaScript functions have a built-in object called the **arguments** object. The argument object contains an array of the arguments used when the function was called (invoked).

- 基本类型和引用类型（object function)都可以作为参数。
- 基本类型传递值，不改变原值。引用类型传递地址（reference），改变原值。

```js
x = sumAll(1, 123, 500, 115, 44, 88);

function sumAll() {
  let sum = 0;
  for (let i = 0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  return sum;
}

//...treat indefinite number of parameters as array
function sum(...args) {
  let sum = 0;
  for (let arg of args) sum += arg;
  return sum;
}

let x = sum(4, 9, 16, 25, 29, 100, 66, 77);
```

### **Invocation**

- The () Operator Invokes the Function

Using the example above, `myFunction` refers to the function object, and `myFunction()` refers to the function result. Accessing a function without () will return the function object instead of the function result.

- Self-Invoking Functions

```
(function () {
  let x = "Hello!!";  // I will invoke myself
})(); 
//Function expressions will execute automatically if the expression is included in () and followed by ().
```

- **What is this?**

In JavaScript, the `this` keyword refers to an **object**.

Which object depends on how `this` is being invoked (used or called).

The `this` keyword refers to different objects depending on how it is used:

| In an object method, `this` refers to the **object**.        |
| ------------------------------------------------------------ |
| Alone, `this` refers to the **global object**. In a web browser the global object is the browser window. |
| In a function, `this` refers to the **global object**.       |
| In a function, in strict mode, `this` is `undefined`.        |
| In an event, `this` refers to the **element** that received the event. |
| Methods like `call()`, `apply()`, and `bind()` can refer `this` to **any object**. |

- Invoking a Function as a Method

```
const myObject = {
  firstName:"John",
  lastName: "Doe",
  fullName: function () {
    return this.firstName + " " + this.lastName;
  }
}
myObject.fullName();         // Will return "John Doe"
```

- Invoking a Function with a Function **Constructor**

```
// This is a function constructor:
function myFunction(arg1, arg2) {
  this.firstName = arg1;
  this.lastName  = arg2;
}

// This creates a new object
const myObj = new myFunction("John", "Doe");
```

### **Call() Apply() Bind()**

call() 方法是预定义的 JavaScript 方法。通过 call()，您能够使用属于另一个对象的方法。

```javascript
var person = {
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
}
var person1 = {
    firstName:"Bill",
    lastName: "Gates",
}
person.fullName.call(person1);  // 将返回 "Bill Gates"
```

call() 方法可接受参数：

```javascript
var person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}
var person1 = {
  firstName:"Bill",
  lastName: "Gates"
}
person.fullName.call(person1, "Seattle", "USA");
```

The difference between call() and apply() is:

The `call()` method takes arguments **separately**.The `apply()` method takes  **array** arguments.

```
person.fullName.call(person1, ["Seattle", "USA"]);
```

`bind()` create a variable that is a function object, which borrow a function from one object to another object.

**call() apply()可以用于一般function到object，bind()必须用于object的method到另一个object.**

```js
const person = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}

const member = {
  firstName:"Hege",
  lastName: "Nilsen",
}

let fullName = person.fullName.bind(member);

document.getElementById("demo").innerHTML = fullName(); //bind必须先声明
```

### Closures

If counter is global variable, its not protected, and function can change counter; if counter is local inside a function, it will be declared to be 0 every time.

Closure solves this problem. the self-invoking function runs once and return a function express to add. Then when add is invoked, counter will increment. So counter can only be changed by calling add().

 The "wonderful" part is that the returnd function can access the counter in the parent scope.This is called a JavaScript **closure.** It makes it possible for a function to have "**private**" variables and does not loss it through time. A closure is a function having access to the parent scope, even after the parent function has closed.

```js
<button type="button" onclick="myFunction()">Count!</button>

<p id="demo">0</p>

<script>
const add = (function () {
  let counter = 0;
  return function () {counter += 1; return counter;}
})();

function myFunction(){
  document.getElementById("demo").innerHTML = add();
}
</script>
```



## Javascript Object

It is a common practice to declare objects with the **const** keyword.

Use number boolean string as 基本类型， do not use new String() etc. to declare them. Slow!

Object has **properties** and **methods**. 

```js
const person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
    
  fullname() {
    return this.firstName + " " + this.lastName;
  } //省略 : function 效果一样
};
```

re-assign a object change its reference.

```javascript
let student1={no:1,name:'a'};
let student3=student1; //student3 points to the location of student1
console.log(student3);
student1={no:2,name:'b'}; //student1 change location,
console.log(student3); //student3 doesn't change
```



### Create object

There are different ways to create new objects:

- Create a single object, using an object literal.
- Create a single object, with the keyword `new`.
- Define an object constructor, and then create objects of the constructed type.
- Create an object using `Object.create()`.

```js
1. //person.propertyname person[declared variable]
const person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
or
const person = {"firstName":"John", lastName:"Doe", age:50, eyeColor:"blue"};
//firstName 属性名，非已定义的变量
or
const person = {};
person.firstName = "John";
let aproperty='name';
person[aproperty]='John Doe';//同下
person['name']='John Doe';
person.name='John Doe'; //同下

person.name; =>'John Doe'
person[aproperty]; =>'John Doe'

2.const person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";

3.// Constructor function for Person objects
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
  this.name = function() {
    return this.firstName + " " + this.lastName;
  };
}
// Create a Person object
const myFather = new Person("John", "Doe", 50, "blue");

//JavaScript has built-in constructors for native objects:
new String()    // A new String object
new Number()    // A new Number object
new Boolean()   // A new Boolean object
new Object()    // A new Object object
new Array()     // A new Array object
new RegExp()    // A new RegExp object
new Function()  // A new Function object
new Date()      // A new Date object


```



### Properties and Methods

```js
//access properties
*objectName.propertyName*
*objectName["propertyName"]*
*objectName[variable]* //variable="propertyName"
    
//access property in loop
const person = {
  fname:" John",
  lname:" Doe",
  age: 25
};

for (let x in person) {
  txt += (x+' '+person[x]+' ');
}

//add new property
person.location="aaaaa"

//delete property, the delete operator is designed to be used on object properties. It has no effect on variables or functions.
delete person.age;

//property can be object(nested object)
myObj = {
  name:"John",
  age:30,
  cars: {
    car1:"Ford",
    car2:"BMW",
    car3:"Fiat"
  }
}
myObj.cars.car2;

```

```js
//access methods
*objectName.methodName()*

//add a method
person.name = function () {
  return this.firstName + " " + this.lastName;
};
```

**Note**:**display** object properties(person.firstname) or convert object to value array (`Object.values(person)`, including methods) or string(`JSON.stringify(person)`, //ignore methods), not the object (will present: [object Object]).

**Accessors**: getter and setter, makes equal syntax for property and method.

```js
const person = {  
    firstName: "John",  
    lastName : "Doe",  
    fullName : function() {    
        return this.firstName + " " + this.lastName;
    }
    setlang: function(lang){
        this.lang=lang;
    }
};
person.fullname()
person.setlang("en")

const person = {  
    firstName: "John",  
    lastName : "Doe",  
    get fullName(){    
        return this.firstName + " " + this.lastName;
    }
    set language(lang){
        this.lang=lang;
    }
};

person.fullname
person.language = "en";

```

### Prototypes

All JavaScript objects inherit properties and methods from a prototype:

- `Date` objects inherit from `Date.prototype`
- `Array` objects inherit from `Array.prototype`
- `Person` objects inherit from `Person.prototype`

The `Object.prototype` is on the top of the prototype inheritance chain:

`Date` objects, `Array` objects, and `Person` objects inherit from `Object.prototype`.

we cannot add property and method to object constructor, but we can add then to prototype, then any object can inherit it. *Only modify your **own** prototypes. Never modify the prototypes of standard JavaScript objects.*

```js
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

Person.prototype.nationality = "English";
Person.prototype.name = function() {
  return this.firstName + " " + this.lastName;
};
```



## Javascript Array

Arrays are a special kind of objects, with numbered indexes.

**create and access array**

```js
//array literal
const cars = ["Saab", "Volvo", "BMW"];

const cars = [];
cars[0]= "Saab";
cars[1]= "Volvo";
cars[2]= "BMW";

//new an Array object, The example do exactly the same as above.
const cars = new Array("Saab", "Volvo", "BMW");

//use index to access and change array element
cars[0]='AK'

//output the full array, it shows withoud [] like:
Saab,Volvo,BMW

//you can have variables of different types in the same Array.
myArray[0] = Date.now;
myArray[1] = myFunction;// an object
myArray[2] = myCars;
```

**Properties and Methods**

| Properties                          |                                                              |
| ----------------------------------- | ------------------------------------------------------------ |
| length                              | cannot use negative index in array, use array[array.length-n] |
| **Methods**                         |                                                              |
| .toString()                         | 'Banana,Orange,Apple,Mango' 在html里显示结果和本身没啥区别吧 |
| .join("symbol")                     | fruits.join(" * "); ->'Banana * Orange * Apple * Mango'      |
| .keys()                             | returns an Array Iterator object with the keys of an array   |
| .entries()                          | returns an Array **Iterator**(use for of to iterate) object with key/value pairs: |
| **change array item**               |                                                              |
| .pop()                              | returns the value that was "popped out":<br>let fruit = fruits.pop(); <br>fruits删除Mango, fruit 为Mango. |
| .push(item)                         | returns the new array length                                 |
| .shift()                            | removes the first array element and "shifts" all other elements to a lower index. returns the value that was "shifted out": |
| .unshift()                          | adds a new element to an array (at the beginning), and "unshifts" older elements, returns the new array length. |
| **return a new array**              |                                                              |
| .concat(array,array,array...)       | creates a **new array** by merging (concatenating) existing arrays:does not change the existing arrays. It always returns a new array. |
| .slice()                            | slices a piece of an array into a new array.<br>let a=fruits.slice(1,3); a->['Orange', 'Apple'] |
| **sort**                            | does not create new array                                    |
| .sort()                             | sorts an array alphabetically,                               |
| .reverse()                          | reverses the elements                                        |
| .sort(function(a, b){return a - b}) | sort for a array with number items, ascendingly. <br>function(a, b){return a - b} is compare function, for each oair of items a b, the compare function return a value, if its positive, a behind b , otherwise b behind a. |
| .sort(function(a, b){return b - a}) | descendingly                                                 |
| **iterate**                         |                                                              |
| .forEach(function)                  | calls a function (a callback function) once for each array element<br>let txt='';<br>const fruits=['apple','banana'];<br>function myFunction(value, index, array) { txt += value + "  ";}<br>fruits.forEach(myFunction); |
| .map(function)                      | creates a new array by performing a function on each array element.<br>const numbers1 = [45, 4, 9, 16, 25]; <br>const numbers2 = numbers1.map(myFunction);<br>function myFunction(value, index, array) {  return value * 2; } |
| .reduce(function)                   | runs a function on each array element to produce (reduce it to) a single value. |
| .filter(function)                   | creates a new array with array elements that pass a test     |
| .every(function)                    | checks if all array values pass a test.                      |
| .some(function)                     | checks if some array values pass a test.                     |
| .find(function)                     | returns the value of the first array element that passes a test function. |
| .findIndex(function)                | returns the index of the first array element that passes a test function. |
|                                     |                                                              |
|                                     |                                                              |
|                                     |                                                              |
| **search**                          |                                                              |
| .includes(*search-item*)            | check if an element is present in an array                   |
| .indexOf(item, *start*)             | return index                                                 |
| .lastIndexOf(item, *start*)         |                                                              |
| **Array static methods**            |                                                              |
| Array.isArray(anydata);             | recognize if a varibale is array, typeOf(array1) ->object, so we need this method |
| Array.from(object)                  | create a array                                               |
|                                     |                                                              |



## Javascript Date

There are **4 ways** to create a new date object:

```js
new Date() //the current date and time

new Date(year, month, day, hours, minutes, seconds, milliseconds) 
const d = new Date(2018, 11, 24, 10, 33, 30, 0);
//with the specified date and time, cannot omit year month.

new Date(milliseconds)
//Zero time is January 01, 1970 00:00:00 UTC.
const d = new Date(-100000000000);//October 31 1966

new Date(date string)
//ISO Date
const d = new Date("2015-03-25");
const d = new Date("2015-03");
const d = new Date("2015");
const d = new Date("2015-03-25T12:00:00Z");
//short date
const d = new Date("03/25/2015");
//long date
const d = new Date("Mar 25 2015");
```

JavaScript will (by default) output dates in full text string format, ( automatically converted with toString())

```
const d=new Date();
d.toString();//Tue Oct 18 2022 02:20:20 GMT+0300 (东欧夏令时间)
d.toUTCString();
d.toDateString();
d.toISOString();
```

**Properties and Methods**

| Date static method |                                                              |
| ------------------ | ------------------------------------------------------------ |
| Date.parse()       | returns the number of milliseconds between the date and January 1, 1970 |
| Date.now()         | Return the current date/time in milliseconds since January 1, 1970 |
|                    |                                                              |
|                    |                                                              |
|                    |                                                              |
| **Methods**        |                                                              |
| .getFullYear()     |                                                              |
| .getMonth()        | also available for getDate(),getHours(),getMinutes(),getSeconds(),getMilliseconds(), |
| .getDay()          | Get the **weekday** as a number (0-6)                        |
| .getTime()         | Get the **time** (milliseconds since January 1, 1970)        |
|                    |                                                              |
| .setFullYear()     |                                                              |
| .setMonth()        | also available for setDate(),setHours(),setMinutes(),setSeconds(),setMilliseconds(), |
| .setTime()         | Set the **time** (milliseconds since January 1, 1970)        |
|                    |                                                              |

## Javascript Set

**create set**

```
const letters = new Set(["a","b","c"]);

// Create a Set
const letters = new Set();

// Add Values to the Set
letters.add("a");
letters.add("b");
letters.add("c");
```

**methods** 

| property:size              |                       |
| -------------------------- | --------------------- |
| .add(value/variable)       |                       |
| .forEach(callbackfunction) |                       |
| .values()                  | return a **Iterator** |
| .has()                     |                       |
| .delete()                  |                       |



## Javascript Map

**create**

```js
// Create a Map by passing an Array to the new Map() constructor
//Keys can be any datatype
const fruits = new Map([
  ["apples", 500],
  ["bananas", 300],
  ["oranges", 200]
]);

//// Create a Map
const fruits = new Map();
// Set Map Values
fruits.set("apples", 500);
fruits.set("bananas", 300);
fruits.set("oranges", 200);
```

**methods**

| property        |                                                  |
| --------------- | ------------------------------------------------ |
| size            |                                                  |
| **methods**     |                                                  |
| .set(key,value) |                                                  |
| .get(key)       |                                                  |
| .delete(key)    |                                                  |
| .has(key)       |                                                  |
|                 |                                                  |
| .foreach()      | pass value,key to callback function              |
| .entries()      | eturns an iterator object with the [key, values] |



## Javascript RegExp

正则表达式是由一个字符序列形成的搜索模式。

在 JavaScript 中，正则表达式通常用于两个字符串方法 : search() 和 replace()。

**search() 方法** 用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串，并返回子串的起始位置。

**replace() 方法** 用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。

```html
<!--
/pattern/modifiers(optional);

var patt = /runoob/i

/runoob/i  是一个正则表达式。
runoob  是一个正则表达式主体 (用于检索)。
i  是一个修饰符 (搜索不区分大小写)。
-->


<button onclick="myFunction()">点我</button>
<p id="demo">Visit Microsoft!</p>
<script>
    
var str = "Visit Runoob!"; 
var n = str.search(/Runoob/i); //return 6
    
function myFunction() {
    var str = document.getElementById("demo").innerHTML; 
    var txt = str.replace(/microsoft/i,"Runoob");
    document.getElementById("demo").innerHTML = txt;
}
</script>
```

| 正则表达式修饰符  |                                                          |
| ----------------- | -------------------------------------------------------- |
| i                 | 执行对大小写不敏感的匹配。                               |
| g                 | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。 |
| m                 | 执行多行匹配。                                           |
| 正则表达式pattern |                                                          |
| [abc]             | 查找方括号之间的任何字符。                               |
| [0-9]             | 查找任何从 0 至 9 的数字。                               |
| (x\|y)            | 查找任何以 \| 分隔的选项。                               |
| 元字符            |                                                          |
| \d                | 查找数字。                                               |
| \s                | 查找空白字符。                                           |
| \b                | 匹配单词边界。                                           |
| \uxxxx            | 查找以十六进制数 xxxx 规定的 Unicode 字符。              |
| 量词              |                                                          |
| n+                | 匹配任何包含至少一个 *n* 的字符串。                      |
| n*                | 匹配任何包含零个或多个 *n* 的字符串。                    |
| n?                | 匹配任何包含零个或一个 *n* 的字符串。                    |

**使用 test()**

test() 方法是一个正则表达式方法。

test() 方法用于检测一个字符串是否匹配某个模式，如果字符串中含有匹配的文本，则返回 true，否则返回 false。

以下实例用于搜索字符串中的字符 "e"：

```javascript
var patt = /e/;
patt.test("The best things in life are free!"); //true

/e/.test("The best things in life are free!") //true
```



## --------primitive-----------

## Javascript String

A string can be defined with literal or as an object, but donot use object string!

```
let x = "John";
let y = new String("John");
let z = new String("John");
let v=y;

x==y true
x===y false
y==z false
y===z false
y===v true

```

**Operator and string**

- Except for `+`, other arthimethic operator automatically convert string to number or NaN: '100'-10 ->90; '100'+10->'10010';'as'-10->NaN;
- Comparing two string is alphabetical comparison : '2'>'12' -> true
- Comparing s tring and a number , automatically convert the string to number. '2'>12->false;'2'==2 ->true;
- Non-numeric string will be converted to NaN, so any comparison is false. 'as'>12->false



**Properties and methods**

| Properties                   |                                                              |
| ---------------------------- | ------------------------------------------------------------ |
| .length                      | length of a string                                           |
| **Methods**                  | does not change the string it is called on but returns a new string. |
| .slice(*start*, *end*)       | 正从0开始，反从-1开始，包含start，不含end                    |
| .substring(*start*, *end*)   | start and end values less than 0 are treated as 0            |
| .substr(*start*, *length*)   | the second parameter specifies the **length** of the extracted part. |
| .replace()                   | let text = "Please visit Microsoft!";<br/>let newText = text.replace("Microsoft", "W3Schools");<br/>case sensitive. replace the first match. regular express |
| .toUpperCase()               |                                                              |
| .toLowerCase()               |                                                              |
| .concat(string)              | let text3 = text1.concat(" ", text2);                        |
| .trim()                      |                                                              |
| .trimStart()                 |                                                              |
| .trimEnd()                   |                                                              |
| .padStart(number,string)     | .padStart(4,'ef')                                            |
| .padEnd(number,string)       |                                                              |
| .charAt(*position*)          |                                                              |
| .charCodeAt(*position*)      | returns a UTF-16 code                                        |
| [position]                   | let a="asdf";let b=a[0]; read only                           |
| .split("symbol")             | convert a string to array, split the string on the symbol or empty"" |
| **search method**            |                                                              |
| .indexOf("string",start)     | the `first` occurrence of a specified text after start position, return -1 for not found. cannot take powerful search values (regular expressions). |
| .lastIndexOf("string",start) | **last** occurrence of a specified text before start position,return -1 for not found |
| .search("string")            | take powerful search values (regular expressions).           |
| .match(*regexp*)             | returns the matches, as an Array object.                     |
| .includes("string",start)    | return true/false                                            |
| .startsWith("string",start)  | return true/false, check if the string strat with a value from the position |
| .endsWith("string",length)   | return true/falsecheck if the string end with a value to the position |
|                              |                                                              |

**Template Literals** use back-ticks (``) rather than the quotes ("") to define a string:

```js
let text = `Hello World!`;

let text =
`The quick
brown fox
jumps over
the lazy dog`;
// do not need / to split string

//Template Literals allow string interpolation and expressions in strings:
let firstName = "John";
let lastName = "Doe";
let text = `Welcome ${firstName}, ${lastName}!`;

let price = 10;
let VAT = 0.25;
let total = `Total: ${(price * (1 + VAT)).toFixed(2)}`;
```

Escape character:

| \ '  | '                    |
| ---- | -------------------- |
| \ "  | "                    |
| \ \  | \                    |
| \b   | Backspace            |
| \f   | Form Feed            |
| \n   | New Line             |
| \r   | Carriage Return      |
| \t   | Horizontal Tabulator |
| \v   | Vertical Tabulator   |



## Javascript Number

- JavaScript has only one type of number (**64-bit** Floating Point). 
- Numbers can be written with or without decimals orscientific (exponent) notation.
- I**ntegers** (numbers without a period or exponent notation) are accurate up to **15 digits**.
- The maximum number of **decimals is 17**.
- **NaN** (not a number) is a number, that indicates that a number is not a legal number.

```
let x=100 / "Apple"; //x is NaN

isNaN('apple');
isNaN(NaN); // BOTH return true,You can use the global JavaScript function isNaN() to find out if a value is a not a number.

typeof NaN; //return number.
```

- `Infinity` (or `-Infinity`) is the value JavaScript will return if you calculate a number outside the largest possible number. They are number type.
- JavaScript interprets numeric constants as **hexadecimal** if they are preceded by 0x.: let x= 0xff;

**Properties and Methods**

| **Properties**                                               | Number properties belongs to the JavaScript's number object wrapper called **Number**. cannot be used on varibales |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Number.MAX_VALUE                                             | largest number possible in JavaScript                        |
| Number.MIN_VALUE;                                            |                                                              |
| Number.POSITIVE_INFINITY;                                    |                                                              |
| Number.NEGATIVE_INFINITY;                                    |                                                              |
| Number.NaN;                                                  |                                                              |
| **Methods**                                                  | used on variables                                            |
| .toString(n)                                                 | default n (base) is 10. can be other base: 2,8,16,,,         |
| .toExponential()                                             | returns a string, with a number rounded and written using exponential notation. |
| .toFixed(n)                                                  | return a string, remain n digits after decimals              |
| .valueOf()                                                   | convert a object numbe rto primitive number.                 |
|                                                              |                                                              |
| **JavaScript global methods can be used on all JavaScript data types.:** |                                                              |
| Number()                                                     | Number(true) ->1<br>Number(false) ->0<br>Number("1.3") -> 1.3<br/>Number("apl")->NaN |
| parseInt()                                                   | parseInt("-10.33")->-10<br/>parseInt("10 6")->10<br/>parseInt("10 years")->10<br/>parseInt("years 10")->Nan<br/> |
| parseFloat()                                                 | parseFloat("10")->10<br/>parseFloat("10.33")->10.33<br/>parseInt("10 6")->10<br/>parseInt("10 years")->10<br/>parseInt("years 10")->Nan<br/> |



## Javascript Boolean

static methods:
Boolean(compare expression/value)

0, null, empty string, undefined,false, NaN, is false; other values are true.(1, 'false',(1+1),,,)

## Javascript Symbol

It represents a unique "hidden" identifier that no other code can accidentally access.

```
const person = {
  firstName: "John",
};

let id = Symbol('string');
person[id] = 140353;
// Now person[id] = 140353
// but person.string is still undefined
```

Symbols are always unique.

If you create two symbols with the same description they will have different values.

```
Symbol("id") == Symbol("id") // false
```



## Javascript Static Object Math

Static object has no constructor. All methods and properties can be used without creating a Math object first.

```js
//properties
Math.E        // returns Euler's number
Math.PI       // returns PI
Math.SQRT2    // returns the square root of 2
Math.SQRT1_2  // returns the square root of 1/2
Math.LN2      // returns the natural logarithm of 2
Math.LN10     // returns the natural logarithm of 10
Math.LOG2E    // returns base 2 logarithm of E
Math.LOG10E   // returns base 10 logarithm of E

//Methods
//round a number to an integer
Math.round(x)	//Returns x rounded to its nearest integer
Math.ceil(x)	//Returns x rounded up to its nearest integer
Math.floor(x)	//Returns x rounded down to its nearest integer
Math.trunc(x)	//Returns the integer part of x (new in ES6)

//single parameter
Math.sign(x) //returns if x is negative, null or positive:
Math.pow(x, y) //returns the value of x to the power of y
Math.sqrt(x) //returns the square root of x
Math.abs(x) //returns the absolute (positive) value of x
Math.log(x) //returns the natural logarithm of x
Math.log2(x) //returns the base 2 logarithm of x
Math.log10(x) //returns the base 10 logarithm of x
Math.sin(x) //returns the sine (a value between -1 and 1) of the angle x
Math.cos(x) //returns the cosine (a value between -1 and 1) of the angle x

//multiple arguments
Math.min() and Math.max() can be used to find the lowest or highest value in a list of arguments// use ... to expand a array to multiple arguments
Math.max(1,2,3)
let a=[1,2,3];
Math.max(...a)

//no argument
Math.random() //returns a random number between 0 (inclusive), and 1 (exclusive)
Math.floor(Math.random() * (max - min) ) + min; //returns a random number between min (included) and max (excluded)
Math.floor(Math.random() * (max - min + 1) ) + min //returns a random number between min and max (both included)
```

# --------------------------------------

# Javascript Class

Class is **template** for JavaScript objects.

Syntax:

```
class ClassName {
  constructor() { ... }
  method_1() { ... }
  method_2() { ... }
}

class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age() {
    let date = new Date();
    return date.getFullYear() - this.year;
  }
}
```

## Class Inheritance

A class created with a class inheritance inherits all the methods (can override) from another class:

```js
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  present() {
    return 'I have a ' + this.carname;
  }
}

class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this.present() + ', it is a ' + this.model;
  }
}

let myCar = new Model("Ford", "Mustang");
document.getElementById("demo").innerHTML = myCar.show();
```

## Getter and Setter

```js
class Car {
  constructor(brand) {
    this._carname = brand;
  }
  get carname() {
    return this._carname;
  }
  set carname(x) {
    this._carname = x;
  }
}

let myCar = new Car("Ford");
myCar.carname = "Volvo"; //donot use()
document.getElementById("demo").innerHTML = myCar.carname; //it is good use _ to specify property and corresponding getter setter.
```

## Static Methods

```
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello() {
    return "Hello!!";
  }
}

// You can call 'hello()' on the Car Class:
document.getElementById("demo").innerHTML = Car.hello();

```

# ----内置函数----------

# JavaScript If and switch

- **if 语句** - 只有当指定条件为 true 时，使用该语句来执行代码
- **if...else 语句** - 当条件为 true 时执行代码，当条件为 false 时执行其他代码
- **if...else if....else 语句**- 使用该语句来选择多个代码块之一来执行
- **switch 语句** - Switch cases use **strict** comparison (===),  switch 语句会使用恒等计算符(===)进行比较:

```javascript
if (time<10)
{
    document.write("<b>早上好</b>");
}
else if (time>=10 && time<20)
{
    document.write("<b>今天好</b>");
}
else
{
    document.write("<b>晚上好!</b>");
}


var d=new Date().getDay();
switch (d)
{
    case 6:x="今天是星期六";
    break;
    case 0:x="今天是星期日";
    break;
    default:
    x="期待周末";
}
document.getElementById("demo").innerHTML=x;
```



# JavaScript Loop

- **for** - 循环代码块一定的次数
- **for in** - iterate properties of an object or item of array
- **for Of** -loops through the values of an **iterable** object (string array set map,,,)
- **while** - 当指定的条件为 true 时循环指定的代码块
- **do/while** - 同样当指定的条件为 true 时循环指定的代码块
- var does not have blocl level, so variable declared with var inside loop (or at expression one) is visible outside loop.
  let has block level, so variable declared with let inside loop (or at expression one) is not visible afetr the loop.
- for (let i=0;i<5;i++) 在每次循环时，i都是重新声明并赋值的，作用域仅在当次循环。解决循环内的闭包问题（闭包里使用的i参数不会被循环改变）和循环里的异步问题（异步时间到的时候,var i早被改了）。

For循环

```javascript
for (var i=0,len=cars.length; i<len; i++)
{ 
    document.write(cars[i] + "<br>");
}

//语句 1 是可选的，（比如在循环开始前已经设置了值时）
//您可以在语句 1 中初始化任意（或者多个）值

//语句 2 用于评估初始变量的条件。语句 2 同样是可选的。
//如果您省略了语句 2，那么必须在循环内提供 break。否则循环就无法停下来

//语句 3 也可以省略（比如当循环内部有相应的代码时）
for(;;){}

var a=[];
for(var i=0;i<10;i++){
    a[i]=function(){console.log(i);};
}
a[6]();//10

for(let i=0;i<10;i++){
    a[i]=function(){console.log(i);};
}
a[6]();//6
```

For/In循环

```javascript
var person={fname:"Bill",lname:"Gates",age:56}; 
let txt=''
 
for (let x in person)  // x 为属性名
{
    txt=txt + person[x];
}

const numbers = [45, 4, 9, 16, 25];

let txt = "";
for (let x in numbers) {
  txt += numbers[x]; //x is index
}
```

for Of

```js
for (declaration variable of iterable) {
  // code block to be executed
}

const cars = ["BMW", "Volvo", "Mini"];

let text = "";
for (let x of cars) {
  text += x;
}

let language = "JavaScript";

let text = "";
for (let x of language) {
text += x;
}
```



While

```javascript
let i=0;
while (i<5)
{
    x=x + "The number is " + i + "<br>";
    i++;
}
```

do/while 循环

```javascript
let i=0;
do
{
    x=x + "The number is " + i + "<br>";
    i++;
}
while (i<5);
```

**Break/Continue and labels**

break 语句用于跳出循环，可用于循环和switch

continue 用于跳过循环中的一个迭代,只能用在循环

通过标签引用，continue可以跳到指定循环的下一次，break 语句可用于跳出任何 JavaScript code block：

```javascript
cars=["BMW","Volvo","Saab","Ford"];
list: 
{
    document.write(cars[0] + "<br>"); 
    document.write(cars[1] + "<br>"); 
    document.write(cars[2] + "<br>"); 
    break list;
    document.write(cars[3] + "<br>"); 
    document.write(cars[4] + "<br>"); 
    document.write(cars[5] + "<br>"); 
}
```



# Typeof

返回string类型的类型名称

```javascript
//primitive
typeof "John"                // 返回 string
typeof 3.14                  // 返回 number
typeof NaN                    // 返回 number
typeof false                 // 返回 boolean
typeof typeof 3				//return string
typeof undefined             // undefined

//object
typeof [1,2,3,4]             // 返回 'object' Array是一种特殊的对象类型
typeof new Date()             // 返回 object Date 也是对象类型
typeof {name:'John', age:34} // 返回 object
typeof null                  // object
typeof function myFunc(){}   // Returns "function"
//当使用完一个比较大的对象时，需要对其进行释放内存时，设置为 null。
let person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
person = null;    // Now value is null, but type is still an object
person = undefined;   // Now both value and type is undefined

null === undefined           // false
null == undefined            // true
```

JavaScript objects, variables, properties, and methods can be `undefined`.

In addition, empty JavaScript objects can have the value `null`.

 to test if an object is empty:

```
if (typeof myObj !== "undefined" && myObj !== null) 
```





# Void

void 函数，执行其中代码，但返回undefined , often used to obtain the undefined primitive value, using "void(0)".

```
<a href="javascript:void(0);">
  Useless link
</a>

<a href="javascript:void(document.body.style.backgroundColor='red');">
  Click me to change the background color of body to red
</a>
```



# JavaScript 类型转换

others->字符串

```javascript
//全局方法 String() 可以将number,boolean,date,undefiend,null,,转换为字符串。该方法可用于任何类型的数字，字母，变量，表达式：
String(x)         // 将变量 x 转换为字符串并返回
String(123)       // 将数字 123 转换为字符串并返回
String(100 + 23)  // 将数字表达式计算为123转换为字符串并返回
String(false)        // 返回 "false"
String(true)         // 返回 "true"
String(null)  //"null"
String(undefined) //"undefined"
var a = new Date();
typeof String(a) //'string'

// 非static方法 toString() 也是有同样的效果。
x.toString()
(123).toString()
(100 + 23).toString()
false.toString()     // 返回 "false"
true.toString()      // 返回 "true"
date.toString()
array.toString()

```

others->数字

```javascript
//全局方法 Number()
//空字符串转换为 0。其他的字符串会转换为 NaN

Number("3.14")    // 返回 3.14
Number(" ")       // 返回 0
Number("")        // 返回 0
Number("99 88")   // 返回 NaN
Number(false)     // 返回 0
Number(true)      // 返回 1
Number(null)      //0
Number(undefined)  //NaN
d = new Date();
Number(d)      // 返回 1404568027739
d.getTime()        // 返回 1404568027739
```

others->boolean 见Boolean static 方法

**Note:** 当你尝试输出一个对象或一个变量时 JavaScript 会自动调用变量的 toString() 方法：



# JavaScript 错误 - throw、try 和 catch

**try** 语句测试代码块的错误。

**catch** 语句处理错误。许我们定义当 try 代码块发生错误时，所执行的代码块。**try** 和 **catch** 是成对出现的。

**throw** 语句创建自定义错误。

**finally** 语句在 try 和 catch 语句之后，无论是否有触发异常，该语句都会执行。

```
try {
    ...    //异常的抛出
} catch(e) {
    ...    //异常的捕获与处理
} finally {
    ...    //结束处理
}
```

当错误发生时，当事情出问题时，JavaScript 引擎通常会停止，并生成一个错误消息。

描述这种情况的技术术语是：JavaScript 将**抛出**一个错误。

```javascript
try { 
    if(x == "") throw "值是空的"; //throw 语句允许我们创建自定义错误。throw exception
    
    if(isNaN(x)) throw "值不是一个数字";
    x = Number(x);
    if(x > 10) throw "太大";
    if(x < 5) throw "太小";
  }
  catch(err) {
    message.innerHTML = "错误: " + err + ".";
  }
  finally {
    document.getElementById("demo").value = "";
  }
```

Javascript has build-in error, which has two properties: name, message; these build-in errors donot need throw exception.

```js
try{

}
catch(err){
aaaaaaaa.innerHTML=err.message}
finally{

}
```

# -----------Tips------------

# Hoistint 变量提升

Hoisting is JavaScript's default behavior of moving all **declaration**s to the top of the current scope (to the top of the current script or the current function).

let const 不可以

```javascript
x=5;
function(x){
return x+2;
}
var x;
//var x 会被解释器提升到相应的最顶部


var x = 5; // 初始化 x
elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x + " " + y;           // 此时y声明,=7没被提升被提升了，因此y=undefined
var y = 7; // 初始化 y

```

# 严格模式(use strict)

严格模式通过在脚本或函数的头部添加 "use strict"; 表达式来声明。

在函数内部声明是局部作用域 (只在函数内使用严格模式)；在block里声明，只有block level好用。

# This keyword

**What is this?**

In JavaScript, the `this` keyword refers to an **object**.

**Which** object depends on how `this` is being invoked (used or called).

The `this` keyword refers to different objects depending on how it is used:

| In an object method, `this` refers to the **object**.        |
| ------------------------------------------------------------ |
| Alone, `this` refers to the **global object**.               |
| In a function, `this` refers to the **global object**.       |
| In a function, in strict mode, `this` is `undefined`.        |
| In an event, `this` refers to the **element** that received the event. |
| Methods like `call()`, `apply()`, and `bind()` can refer `this` to **any object**. |

To determine which object `this` refers to; use the following precedence of order.

| Precedence | Object             |
| ---------- | ------------------ |
| 1          | bind()             |
| 2          | apply() and call() |
| 3          | Object method      |
| 4          | Global scope       |

# Modules

export

```js
export const name = "Jesse";//In-line individually
export const age = 40;

const name = "Jesse";
const age = 40;
export {name, age};//at once at the bottom

const message = () => {
const name = "Jesse";
const age = 40;
return name + ' is ' + age + 'years old.';
};

export default message;//You can only have one default export in a file
```

import

```js
import message, * as modulename, { name, age as age1 } from "./person.js"; 
//Named exports are constructed using curly braces.
//default export does not need braces
//* means all exports from a js file, use modulename.exports to use exports
```

# JavaScript JSON

JSON 是用于存储storing 和传输transporting数据的格式。

JavaScript Object Notation，是一种轻量级的数据交换格式lightweight data interchange format，通常用于服务端向网页传递数据 。

* JSON 使用 JavaScript 语法，但是 JSON 格式仅仅是一个文本。 文本可以被任何编程语言读取及作为数据格式传递 language-independent。

* JSON 格式在语法上与创建 JavaScript 对象代码是相同的。由于它们很相似，所以 JavaScript 程序可以很容易的将 JSON 数据转换为 JavaScript 对象。

* It is a common mistake to call a JSON object literal "a JSON object".

  JSON cannot be an object. JSON is a string format.

  The data is only JSON when it is in a string format. When it is converted to a JavaScript variable, it becomes a JavaScript object.

* JSON 语法规则

  * 数据为 键/值 对。"name":"Runoob"
  * *keys* must be strings, written with double quotes:"name"
  * value 可以是数字，字符串（double quotes），boolean，null，数组，对象
  * 数据由逗号分隔。
  * 大括号保存对象 {"name":"Runoob", "url":"www.runoob.com"}
  * 方括号保存数组 {"sites":[    {"name":"Runoob", "url":"www.runoob.com"},     {"name":"Google", "url":"www.google.com"}] } 

```javascript
var text = '{ "sites" : [' +
    '{ "name":"Runoob" , "url":"www.runoob.com" },' +
    '{ "name":"Google" , "url":"www.google.com" },' +
    '{ "name":"Taobao" , "url":"www.taobao.com" } ]}';

var obj = JSON.parse(text);
//内置函数JSON.parse将json数据转换成javascript对象
// obj此时是对象，可以obj.sites[1].name
```

| JSON.parse()     | 用于将一个 JSON 字符串转换为 JavaScript 对象。 |
| ---------------- | ---------------------------------------------- |
| JSON.stringify() | 用于将 JavaScript 值转换为 JSON 字符串。       |



# ------------Async------------

# JS Callback

A callback is a function passed as an argument to another function。将函数作为参数传递时，请记住不要使用括号。

```javascript
function myDisplayer(some) {
  document.getElementById("demo").innerHTML = some;
}

function myCalculator(num1, num2, myCallback) {
  let sum = num1 + num2;
  myCallback(sum);
}

myCalculator(5, 5, myDisplayer);
```

# JS Asynchronous

- Asynchronous task: setTimeout, Promise.then(), XMLhttprequest,....
- Javascript 是单线程的，但是web api提供了异步方法如setTimeout.
- 函数执行方式为call stack,(函数层层嵌套，先进后出)。
- 遇到setTimeout,进入callback queue，遇到promise.then() 进入job quque
- 执行一个jsp文件时，同步任务先依次入栈完成后,栈free了，检查callback queue和job queue有没有任务。先清空job queue 再执行一个callback任务，再循环检查call stack, job queue,callback queue....
- setTimeout的时间参数只是进入callback queue的时间，进去后依旧排队。
- new Promise 为同步任务，只有promise.then()进入job queue
- 也可以理解，callback queue里的为宏任务，job queue的为微任务，call stack空的时候，先优先清微观任务，再清宏观任务。

![image-20221020192113611](C:\Users\TENGR\AppData\Roaming\Typora\typora-user-images\image-20221020192113611.png)

回调最常与异步函数一起使用。

一个典型的例子是 setTimeout()。

```javascript

function myFunction() {
  document.getElementById("demo").innerHTML = "I love You !!";
}

//等待超时
setTimeout(myFunction, 3000);
//myFunction 被用作回调。函数名作为参数传递给 setTimeout()。
//3000 是超时前的毫秒数，所以 3 秒后会调用 myFunction()。

//等待间隔
setInterval(myFunction, 1000);//一秒一次

//等待文件
//加载一个 HTML 文件 (mycar.html)，并在文件完全加载后在网页中显示该 HTML 文件：
function myDisplayer(some) {
  document.getElementById("demo").innerHTML = some;
}

function getFile(myCallback) {
  let req = new XMLHttpRequest();
  req.open('GET', "mycar.html");
  req.onload = function() {
    if (req.status == 200) {
      myCallback(this.responseText);
    } else {
      myCallback("Error: " + req.status);
    }
  }
  req.send();
}

getFile(myDisplayer);
```

# JS Promise

- "Producing code" is code that can take some time
- "Consuming code" is code that must wait for the result
- A Promise is a JavaScript object that **links producing code and consuming code**.
- A promise object has property: status and result, when status is pending, res is undefined; when its fulfilled, res is a value; when its failed, res is an error. We must use promise.then() to access these property.
- new Promise(function(function1,function2){code;}); 对象可以理解成构造了Promise.resolve()或Promise.reject()，而其中的value需要其.then()来操作。
- .then()实际也返回一个Promise对象，因此.then()可以链式传递下去（.then()如果返回值，则Promise.resolve(value),无返回值则返回Promise.resolve(undefined),生成错误会返回Promise.reject(error))

```js
let myPromise = new Promise(function(myResolve, myReject) {
// "Producing Code" (May take some time)

  myResolve(); // when successful,can be anyname
  myReject();  // when error
});

// "Consuming Code" (Must wait for a fulfilled Promise)
myPromise.then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);
//

let myPromise = new Promise(function(myResolve, myReject) {
  let req = new XMLHttpRequest();
  req.open('GET', "mycar.htm");
  req.onload = function() {
    if (req.status == 200) {
      myResolve(req.response);
    } else {
      myReject("File not Found");
    }
  };
  req.send();
});

myPromise.then(
  function(value) {myDisplayer(value);},
  function(error) {myDisplayer(error);}
);
```



# JS Async/Await

*"async and await make promises easier to write"*

**async** makes a function return a Promise. If async function return a normal value(non-Promise), it will be converted to Promise.resolve(value)

**await** makes a function wait for a Promise，

```js
async function myFunction() {
  return "Hello";
}

function myFunction() {
  return Promise.resolve("Hello");
}

//they are the same

myFunction().then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);

```

```js
async function myDisplay() {
  let myPromise = new Promise(function(resolve, reject) {
    resolve("I love You !!");
  });
  document.getElementById("demo").innerHTML = await myPromise;
}
myDisplay();

//await是一个运算符，如果await等到的不是Promise对象，运算的值就是该值；如果等的是Promise对象，他会等Promise做完，然后运算结果为Promise的值，
//因此await必须在async里使用，因为等待 这一行为会堵塞后面的代码，而async将后面代码函数封装在.then()中异步执行。
//await使promise代码更简单，不需要promise.then(function(value){}),可以直接处理Promise的值如下：
function function1(n=1){
    console.log(n);
    return n+1;    
}
async function example(){
    const a=await function1();
    const b=await function1(a);
    await function1(b);
}

//async中，await 之前的代码是同步任务，await之后的可以理解为包装到then()，异步,如下
async function example(){
    Promise.resolve(function1())
    .then(function(value){return function1(value)}))
    .then(value=>function1(value))
}

```



# ----------DOM-----------

# Document Object Model

DOM（web api 之一） 定义了访问文档的标准：

> “W3C 文档对象模型（DOM）是中立于平台和语言的接口，它允许程序和脚本动态地访问、更新文档的内容、结构和样式。”

The HTML DOM is a standard **object** model and **programming interface** for HTML. It defines:

- The HTML elements as **objects**
- The **properties** of all HTML elements，（ value that you can get or set (like changing the content of an HTML element).
- The **methods** to access all HTML elements （action you can do）
- The **events** for all HTML elements

The programming interface is the properties and methods of each object.

当网页被加载时，浏览器会创建页面的文档对象模型（*D*ocument *O*bject *M*odel）。

*HTML DOM* 模型被结构化为*对象树*：

![DOM HTML tree](https://www.w3schools.com/js/pic_htmltree.gif)

通过这个对象模型，JavaScript 获得创建动态 HTML 的所有力量：

- JavaScript 能改变页面中的所有 HTML 元素内容， 属性， CSS 样式
- JavaScript 能删除，添加已有的 HTML 元素和属性
- JavaScript 能对页面中所有已有的 HTML 事件作出反应
- JavaScript 能在页面中创建新的 HTML 事件



# Document

The document object represents your web page.

If you want to access any element in an HTML page, you always start with accessing the document object.

| 查找元素                                | 描述                                                         |
| :-------------------------------------- | :----------------------------------------------------------- |
| document.getElementById(*id*)           | 通过元素 id 来查找元素                                       |
| document.getElementsByTagName(*name*)   | 通过标签名来查找元素, return a live HTMLCollection           |
| document.getElementsByClassName(*name*) | 通过类名来查找元素，return a live HTMLCollection             |
| document.querySelectorAll("p.intro")    | 通过 CSS 选择器，本例返回 class="intro" 的所有 < p> 元素列表 |
| document.forms[name];                   | by HTML Object Collections                                   |

```js
const x = document.getElementById("main");
const y = x.getElementsByTagName("p");
//finds all <p> elements inside "main", return a HTML collection
//HTML collection and NOdelist can be accessed by index (starting from 0), have length property.
```



| 改变 HTML 元素                             |                        |
| ------------------------------------------ | ---------------------- |
| element.innerHTML = *new html content*     | 改变元素的 inner HTML  |
| element.attribute = *new value*            | 改变 HTML 元素的属性值 |
| element.setAttribute(*attribute*, *value*) | 改变 HTML 元素的属性值 |
| element.style.property = *new style*       | 改变 HTML 元素的样式   |

| 添加和删除元素                         | 描述             |
| :------------------------------------- | :--------------- |
| document.createElement("nodeName")     | 创建 HTML 元素   |
| document.createTextNode("string")      |                  |
| element.removeChild(*element*)         | 删除子 HTML 元素 |
| element.appendChild(*element*)         | 添加子 HTML 元素 |
| element.replaceChild(element，element) | 替换 子HTML 元素 |
| document.write(*text*)                 | 写入 HTML 输出流 |
| element.remove()                       | 删除该元素       |

| 添加事件处理程序                                     | 描述                            |
| :--------------------------------------------------- | :------------------------------ |
| document.getElementById(id).onclick = functionname() | 向 onclick 事件添加事件处理程序 |

# DOM事件

HTML DOM 允许您使用 JavaScript 向 HTML 元素分配事件：

```html
<script>
document.getElementById("myBtn").onclick = displayDate;
</script> 
```

| onload      | <body onload="checkCookies()"> | triggered when the user enters the page.                     |
| ----------- | ------------------------------ | ------------------------------------------------------------ |
| onunload    |                                | triggered when the user leaves the page.                     |
| onchange    |                                | triggered when any operation on the element (leave,press enter,,,) often used in combination with validation of input fields |
| onmouseover |                                | 类似hover                                                    |
| onmouseout  |                                |                                                              |
|             |                                |                                                              |
| onmousedown |                                | 当鼠标按钮被点击时，onmousedown 事件被触发                   |
| onmouseup   |                                | 当鼠标按钮被释放时，onmouseup 事件被触发                     |
| onclick     |                                | 最后，当鼠标点击完成后，onclick 事件被触发                   |
|             |                                |                                                              |

# Event Listener

- You can add **many event handlers of the same type** to one element, i.e two "click" events.
- You can add event listeners to any DOM object not only HTML elements. i.e the window object.
- When using the `addEventListener()` method, the JavaScript is separated from the HTML markup, for better readability and allows you to add event listeners even when you do not control the HTML markup.
- You can easily remove an event listener by using the `removeEventListener()` method.

```js
element.addEventListener(event, function, useCapture);
//omit'on' for evetn,
//useCapture is optional: true or false; true:bubbling, handle outer moset element first; false:defult, capturing, handle innner most element first.

//1
element.addEventListener("click", function(){ alert("Hello World!"); });

//2
element.addEventListener("click", myFunction);
function myFunction() {
  alert ("Hello World!");
}

//3 add many events to the same element, without overwriting existing events
element.addEventListener("click", myFunction);
element.addEventListener("click", mySecondFunction);

//4 add event listeners on any HTML DOM object such as HTML elements, the HTML document, the window object, or other objects that support events, like the xmlHttpRequest object
window.addEventListener("resize", function(){
  document.getElementById("demo").innerHTML = sometext;
});

//5
element.removeEventListener("mousemove", myFunction);
```

# Navigation

![pic_htmltree](C:\Users\TENGR\Downloads\pic_htmltree.gif)

Note: A common error in DOM processing is to expect an element node to contain text.

```
<title id="demo">DOM Tutorial</title>
```

The element node `<title>` (in the example above) does **not** contain text.

It contains a **text node** with the value "DOM Tutorial".



You can use the following node properties to navigate between nodes with JavaScript:

- `parentNode`
- `childNodes[*nodenumber*]`, returns a live NodeList.
- `firstChild`
- `lastChild`
- `nextSibling`
- `previousSibling`

And following property of node:

- nodeName
- nodeTyoe
- nodeValue(for text node, nodeValue is the text, for others nodeValue is null.)





# ----------BOM----------

# Window

The `window` object is supported by all browsers. It represents the browser's window.

All global JavaScript objects, functions, and variables automatically become members of the window object, including window.screen, windoe.location,,,,,

| window                                                       |                                                              |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| window.innerWidth                                            |                                                              |                                                              |
| window.innerHeight;                                          |                                                              |                                                              |
| window.open()                                                |                                                              | open a new window                                            |
| window.close()                                               |                                                              | close the current window                                     |
| window.moveTo()                                              |                                                              | move the current window                                      |
| window.resizeTo()                                            |                                                              | resize the current window                                    |
| **window.screen**                                            |                                                              |                                                              |
| `screen.width`                                               |                                                              |                                                              |
| `screen.height`                                              |                                                              |                                                              |
| `screen.availWidth`                                          |                                                              |                                                              |
| `screen.availHeight`                                         |                                                              |                                                              |
| `screen.colorDepth`                                          |                                                              |                                                              |
| `screen.pixelDepth`                                          |                                                              |                                                              |
| **window.location**                                          |                                                              |                                                              |
| location.href                                                |                                                              | returns the href (URL) of the current page                   |
| location.hostname                                            |                                                              | returns the domain name of the web host                      |
| location.pathname                                            |                                                              | returns the path and filename of the current page            |
| location.protocol                                            |                                                              | returns the web protocol used (http: or https:)              |
| location.assign()                                            |                                                              | loads a new document                                         |
| **window.history**                                           |                                                              |                                                              |
| history.back()                                               |                                                              |                                                              |
| history.forward()                                            |                                                              |                                                              |
| history.go(n)                                                |                                                              | can be negative number                                       |
| **window.navigator**                                         |                                                              |                                                              |
| `navigator.cookieEnabled`                                    |                                                              | returns true if cookies are enabled                          |
| `navigator.platform`                                         |                                                              | (operating system)                                           |
| navigator.javaEnabled()                                      |                                                              | returns true if [Java](https://www.w3schools.com/java/default.asp) is enabled |
| **Popup Box**                                                |                                                              |                                                              |
| window.alert("*sometext*");                                  |                                                              |                                                              |
| window.confirm("*sometext*");                                |                                                              | When a confirm box pops up, the user will have to click either "OK" or "Cancel" to proceed.If the user clicks "OK", the box returns **true**. If the user clicks "Cancel", the box returns **false**. |
| let person = prompt("Please enter your name:", "Harry Potter"); |                                                              |                                                              |
| **Timing Events**                                            |                                                              |                                                              |
| `setTimeout(*function, milliseconds*`)                       |                                                              |                                                              |
| `setInterval(*function, milliseconds*`)                      |                                                              |                                                              |
| clearTimeout()                                               | myVar = setTimeout(*function*, *milliseconds*);<br/>clearTimeout(myVar); |                                                              |
| clearInterval(*timerVariable*)                               |                                                              |                                                              |
|                                                              |                                                              |                                                              |
|                                                              |                                                              |                                                              |
|                                                              |                                                              |                                                              |

# Cookie

JavaScript can create, read, and delete cookies with the `document.cookie` property.\

```js
//create
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2013 12:00:00 UTC; path=/";
//overwrite
document.cookie = "username=John Smith; expires=Thu, 18 Dec 2013 12:00:00 UTC; path=/";
//read,document.cookie will return all cookies in one string much like: cookie1=value; cookie2=value; cookie3=value;
let x = document.cookie;
let decodedCookie=decodeURIComponent(x);
let ca = decodedCookie.split(';');
//add
document.cookie="key:value"; // does not oberwirte other cookies, just add this cookie.
//delete set the expires parameter to a past date:
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
//
```



# ----------Browser API----------

# Forms API

| Validation DOM Methods        |                                                              |      |
| ----------------------------- | ------------------------------------------------------------ | ---- |
| checkValidity()               | Returns true if an input element contains valid data.        |      |
| setCustomValidity()           | Sets the validationMessage property of an input element.     |      |
| **Validation DOM Properties** |                                                              |      |
| validity                      | Contains boolean properties related to the validity of an input element. |      |
| validationMessage             | Contains the message a browser will display when the validity is false. |      |
| willValidate                  | Indicates if an input element will be validated.             |      |

# Storage API

Should check support typeof(Storage)!==undefined;

With web storage, web applications can store data locally within the user's browser.

Unlike cookies, the storage limit is far larger (at least 5MB) and information is never transferred to the server.

HTML web storage provides two objects for storing data on the client:

- `window.localStorage` - stores data with no expiration date

- `window.sessionStorage` - stores data for one session (data is lost when the browser tab is closed)

| method                                    |      |                                  |
| ----------------------------------------- | ---- | -------------------------------- |
| localStorage.setItem("name", "John Doe"); |      |                                  |
| localStorage.getItem("name");             |      |                                  |
| .removeItem(*keyname*)                    |      | Empty all key out of the storage |
| .clear()                                  |      |                                  |

- ```html
  <head>
  <script>
  function clickCounter() {
    if (typeof(Storage) !== "undefined") {
      if (localStorage.clickcount) {
        localStorage.clickcount = Number(localStorage.clickcount)+1;
      } else {
        localStorage.clickcount = 1;
      }
      document.getElementById("result").innerHTML = "You have clicked the button " + localStorage.clickcount + " time(s).";
    } else {
      document.getElementById("result").innerHTML = "browser not support web storage";
    }
  }
  </script>
  </head>
  <body>
  <p><button onclick="clickCounter()" type="button">Click me!</button></p>
  <div id="result"></div>
  </body>
  ```

# Worker API

Should check support typeof(Storage)!==undefined;

A web worker is a JavaScript running in the background, independently of other scripts, without affecting the performance of the page. You can continue to do whatever you want: clicking, selecting things, etc., while the web worker runs in the background.

```javascript
1. create a script that counts. The script is stored in the "demo_workers.js" file

var i = 0;

function timedCount() {
  i = i + 1;
  postMessage(i);
  setTimeout("timedCount()",500);
}

timedCount();

<!--the postMessage() method - which is used to post a message back to the HTML page.-->
```

```html
<script>
<!--2.checks if the worker already exists, if not - it creates a new web worker object and runs the code in "demo_workers.js" -->

if (typeof(w) == "undefined") {
  w = new Worker("demo_workers.js");
}

<!--3.Then we can send and receive messages from the web worker.Add an "onmessage" event listener to the web worker.-->
w.onmessage = function(event){
  document.getElementById("result").innerHTML = event.data;
};

<!--4. terminate a web worker-->
w.terminate();
w = undefined;
</script>
```

```html
<p>Count numbers: <output id="result"></output></p>
<button onclick="startWorker()">Start Worker</button>
<button onclick="stopWorker()">Stop Worker</button>

<script>
var w;

function startWorker() {
  if (typeof(Worker) !== "undefined") {
    if (typeof(w) == "undefined") {
      w = new Worker("demo_workers.js");
    }
    w.onmessage = function(event) {
      document.getElementById("result").innerHTML = event.data;
    };
  } else {
    document.getElementById("result").innerHTML = "Sorry! No Web Worker support.";
  }
}

function stopWorker() {
  w.terminate();
  w = undefined;
}
</script>
```

# Geolocation API

# ----------AJAX----------

# AJAX **A**synchronous **J**avaScript **A**nd **X**ML.

- 不刷新页面更新网页
- 在页面加载后从服务器请求数据
- 在页面加载后从服务器接收数据
- 在后台向服务器发送数据

AJAX 并非编程语言。AJAX 仅仅组合了：

- 浏览器内建的 XMLHttpRequest 对象（从 web 服务器请求数据）
- JavaScript 和 HTML DOM（显示或使用数据）

Ajax 是一个令人误导的名称。Ajax 应用程序可能使用 XML 来传输数据，但将数据作为纯文本或 JSON 文本传输也同样常见。

Ajax 允许通过与场景后面的 Web 服务器交换数据来异步更新网页。这意味着可以更新网页的部分，而不需要重新加载整个页面。

出于安全原因，现代浏览器不允许跨域访问。This means that both the web page and the XML file it tries to load, must be located on the same server.

xttp也是对象，事件触发的函数中，this指该xttp

**AJAX 如何工作**

- \1. An event occurs in a web page (the page is loaded, a button is clicked)
- \2. An XMLHttpRequest object is **created** by JavaScript
- \3. The XMLHttpRequest object **sends a request** to a web server
- \4. The server processes the request
- \5. The server sends a response back to the web page
- \6. The **response is read** by JavaScript
- \7. Proper action (like page update) is performed by JavaScript

```javascript
var xhttp;
//为了应对所有浏览器，包括 IE5 和 IE6，请检查浏览器是否支持 XMLHttpRequest 对象
if (window.XMLHttpRequest) {
    xhttp = new XMLHttpRequest();
    } else {
    // 老版本的 Internet Explorer（IE5 和 IE6）使用 ActiveX 对象：
     xhttp = new ActiveXObject("Microsoft.XMLHTTP");
}
```



**XMLHttpRequest 对象方法**

| 方法                                           | 描述                                                         |
| :--------------------------------------------- | :----------------------------------------------------------- |
| const xttp=new XMLHttpRequest()                | 创建新的 XMLHttpRequest 对象                                 |
|                                                |                                                              |
| xhttp.open("GET", "ajax_info.txt");            |                                                              |
| .open(*method*, *url*, *async*, *user*, *psw*) | 规定请求method：请求类型 GET 或 POST<br/>url：文件位置<br/>async：true（异步）或 false（同步 default）<br/>user：可选的用户名称<br/>psw：可选的密码 |
| xhttp.send();                                  | 将请求发送到服务器，用于 GET 请求                            |
| xhttp.send(*string*)                           | 将请求发送到服务器，用于 POST 请求                           |
|                                                |                                                              |
| .abort()                                       | 取消当前请求                                                 |
| .getAllResponseHeaders()                       | 返回头部信息                                                 |
| .getResponseHeader()                           | 返回特定的头部信息                                           |
| .setRequestHeader()                            | 向要发送的报头添加标签/值对                                  |
|                                                |                                                              |

**XMLHttpRequest 对象属性**

| 属性                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| xhttp.onload = function() {<br/> // What to do when the response is ready<br/>} | the code to execute when the response is ready.              |
| onreadystatechange                                           | 定义当 readyState 属性发生变化时被调用的函数                 |
| readyState                                                   | 保存 XMLHttpRequest 的状态。<br>0：请求未初始化<br/>1：服务器连接已建立<br/>2：请求已收到<br/>3：正在处理请求<br/>4：请求已完成且响应已就绪 |
| responseText                                                 | 以字符串返回响应数据                                         |
| responseXML                                                  | 以 XML 数据返回响应数据                                      |
| status                                                       | 200: "OK"<br/>403: "Forbidden"<br/>404: "Page not found"     |
| statusText                                                   | Returns the status-text (e.g. "OK" or "Not Found")           |

```js
const xhttp = new XMLHttpRequest();
xhttp.onload = function() {
  const xmlDoc = this.responseXML; //receive XML data
  const x = xmlDoc.getElementsByTagName("ARTIST");
  let txt = "";
  for (let i = 0; i < x.length; i++) {
    txt = txt + x[i].childNodes[0].nodeValue + "<br>";
  }
  document.getElementById("demo").innerHTML = txt;
}
xhttp.open("GET", "cd_catalog.xml");
xhttp.send();
```

```js
function loadDoc() {
  const xhttp = new XMLHttpRequest();
    //trigger function when state is 4.
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      document.getElementById("demo").innerHTML =
      this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt");
  xhttp.send();
}
```



