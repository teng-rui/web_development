# React

React is a JavaScript **library** for building user interfaces, is a frontend JavaScript framework

React allows us to create reusable UI components.

Instead of manipulating the browser's DOM directly, React **creates a virtual DOM in memory**, where it does all the necessary manipulating, before making the changes in the browser DOM.

React finds out what changes have been made, and changes **only** what needs to be changed.

**Notes:**

- Varibale, literals other than string (number, boolean object,,,,) used as property value should be coverd by {}.
- Any link to internal page should use <Link to=""> rather than <a href="">
- Logistics operator (&& ||) and 三元运算 can be used inside JSX HTML.

```jsx
<h1>{i == 1 ? 'True!' : 'False'}</h1>
{cars.length > 0 &&
        <h2>
          You have {cars.length} cars in your garage.
        </h2>
      } //when cars.length>0, a <h2> element will be generated.
```

- Event and css property should be named as camelCase: onClick, backgroundColor

# 创建项目

React是个包，用node的npm执行create-react-app，会生成react项目。该项目由浏览器运行。

node和npm的关系：node.js是js的一个运行环境，是jsp和服务端的jsp的运行环境的组合。

npm是node的包管理器。node中包含有npm，安装好node后，也会发现npm已安装。

VS code 是开发环境。

创建项目后，自动生成package.json, 内部定义了各种script代表的命令。



1. 在C:\Users\TENGR\NodeJS\nodejs 安装node （https://nodejs.org/en/）
2. 添加系统变量C:\Users\TENGR\NodeJS\nodejs  到Path
3. 在gitbash检查 node -v  和npm -v ,都有版本号代表安装成功
4. **npm install -g create-react-app**( 如果要更新create-react-app, 先运行npm uninstall -g create -react-app, 再安装)
5. cd C:\Users\TENGR\NodeJS\programs
6. **npx create-react-app demo**
7. cd demo
8. npm start (项目会在浏览器localhost:3000运行)
9. 建好项目后，在vs code 修改src代码

note: 

1. 3,4,9可能在powershell不可以 试试gitbash
2. start 之后如果 package json 不匹配，在vscode打开package json，ctrl s保存，重新start
3. some already running on 3000. 之前的项目没stop,在任务管理器结束bash,node
5. vscode 被拒绝修改文件：右击demo 安全 打开users权限

(无npm: https://nodejs.org/zh-cn/download/releases/ 查看node版本对应的npm版本

http://npm.taobao.org/mirrors/npm/ 下载npm的zip 解压到C:\Program Files\nodejs\node_modules 解压后文件夹命名为npm

将npm下的bin下的npm,npm.cmd复制到node根目录下)



# Render HTML

`ReactDOM.render()` function takes two arguments, **HTML code** and an H**TML element.**

The purpose of the function is to display the specified HTML code inside the specified HTML element.

```jsx
ReactDOM.render(
    <p>Hello</p>,
    document.getElementById('root')
);

//JSX allows you to write HTML tags inside the JavaScript code.


//React 元素都是不可变的。当元素被创建之后，你是无法改变其内容或属性的。
const element = (<h1>Hello,world!</h1>);
ReactDOM.render(
    element,
    document.getElementById('example')
);

//更新界面的唯一办法是创建一个新的元素，然后将它传入 ReactDOM.render() 方法：
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>现在是 {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(
    element,
    document.getElementById('example')
  );
}
 
setInterval(tick, 1000);

```

你的 React 代码也可以放在一个独立文件上，例如我们创建一个 `helloworld_react.js` 文件，代码如下：

```jsx
ReactDOM.render(
	<h1>Hello, world!</h1>,
    document.getElementById('example')
    );
```

然后在 HTML 文件中引入该 JS 文件：

```html
<body>
    <div id="example"></div>
    <script type="text/babel" src="helloworld_react.js"></script>
</body>
```

## 

# React JSX

- JavaScript XML.
- JSX allows us to **write HTML elements** in JavaScript and place them in the DOM without any `createElement()` and/or `appendChild()` methods.
- JSX is an extension of the JavaScript language based on ES6, and is **translated** into regular JavaScript React element at runtime.
- Multiple line HTML should be include in ().
- Only one top level element! Multiple elements should be included by one parent element or fragment <></>.
- Inside JSX, use className instead of class attribute.

```jsx
const myElement = <h1 className='as'>I Love JSX!</h1>; //with jsx
const myElement = React.createElement('h1', {}, 'I do not use JSX!'); //without jsx, same result
```

## jsx and express

在 JSX 中使用 JavaScript 表达式。表达式写在花括号 **{}** 中。

```jsx
ReactDOM.render(
    <div>
      <h1>{1+1}</h1>
    </div>
    ,
    document.getElementById('example')
);

// JSX 中不能使用 if else 语句，但可以使用 conditional (三元运算) 表达式来替代
ReactDOM.render(
    <div>
      <h1>{i == 1 ? 'True!' : 'False'}</h1>
    </div>
    ,
    document.getElementById('example')
);

```

# 样式

React 推荐使用内联样式。我们可以使用 **camelCase** 语法来设置内联样式.

也可以用CSS 外部表。 使用import引入css文件，会作用于该文件

```jsx
//1
import styles from './my-style.module.css'; 
const Car = () => {
  return <h1 className={styles.bigblue}>Hello Car!</h1>;
}

```

```javascript
var myStyle = {
    fontSize: 100,
    color: '#FF0000'
};
ReactDOM.render(
    <h1 style={{color: "red"}}>Hello Style!</h1>//2
    <h1 style = {myStyle}>菜鸟教程</h1>,
    document.getElementById('example')//3
);
```

# 注释

注释需要写在花括号中，实例如下：

```javascript
ReactDOM.render(
    <div>
    <h1>菜鸟教程</h1>
    {/*注释...*/}
     </div>,
    document.getElementById('example')
);
```

# React Function Components

 Component's name *MUST* start with an upper case letter.

Component's purpose is to return HTML, so define a function component and then render it using syntax: <functionName />.

but actually functionName() also works, (maybe cuz calling the function returns a HTML element, which is same purpose as  <functionName />)

```jsx
// <Name name="菜鸟教程" />为用户自定义的组件。
function App() {
    return (
    <div>
        <Name name="菜鸟教程" />
        <Url url="http://www.runoob.com" />
        <Nickname nickname="Runoob" />
    </div>
    );
}
 
ReactDOM.render(
     <App />,
    document.getElementById('example')
);

//如果我们需要向组件传递参数，可以使用 this.props 对象
function Car(props) {
  return <h2>I am a {props.color} Car!</h2>;
}
const carColor = "red";
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car color="red"/>);
root.render(Car({color:red}));
root.render(<Car color={carColor}/>); //varibale, literals other than string (number, boolean object,,,,) used as property value should be coverd by {}
```

Components can be saved in separate files.

```
//Car.js

function Car() {
  return <h2>Hi, I am a Car!</h2>;
}

export default Car;
```

```
import React from 'react';
import ReactDOM from 'react-dom/client';
import Car from './Car.js';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car />);
```



# React 事件处理

React 事件绑定属性的命名采用驼峰式写法，而不是小写。onClick instead of onclick.

Event handler is written between {}. `onClick={shoot}` instead of `onClick="shoot()"`.

```javascript
function Football() {
  const shoot = () => {
    alert("Great Shot!");
  }

  return (
    <button onClick={shoot}>Take the shot!</button>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Football />);
```

# Hook

Hooks allow function components to **have access to state and other React features.**

You must `import` Hooks from `react`.

There are 3 rules for hooks:

- Hooks can only be called **inside React function components**.
- Hooks can only be called **at the top level of a component.**
- Hooks cannot be conditional

## useState

The React `useState` Hook allows us to track state in a function component.

```jsx
import { useState } from "react";
```

We initialize our state by calling `useState` **in** our function component.

`useState` accepts an initial state and returns two values:

- The current state.
- A function that updates the state.
- The `useState` Hook can be used to keep track of strings, numbers, booleans, arrays, objects, and any combination of these!

```jsx
import { useState } from "react";

function FavoriteColor() {
  const [color, setColor] = useState(""); //destructuring the returned values from useState.
  
  return (
    <>
      <h1>My favorite color is {color}!</h1> //use color
      <button
        type="button"
        onClick={() => setColor("blue")} //setColor() change value for color and change value for variable color used earlier!
      >Blue</button>
    </>
  )
}
```



## useEffect

The `useEffect` Hook allows you to perform side effects in your components, when the component is rendered.

`useEffect` accepts two arguments. The second argument is optional. the function argument will be triggered depending on the dependency.

```jsx
useEffect(<function>, <dependency>)

useEffect(() => {
  //Runs on every render
});

useEffect(() => {
  //Runs only on the first render
}, []);

useEffect(() => {
  //Runs on the first render
  //And any time any dependency value changes
}, [prop, state]);
```

```jsx
import { useState, useEffect } from "react";
import ReactDOM from "react-dom/client";

function Counter() {
  const [count, setCount] = useState(0);
  const [calculation, setCalculation] = useState(0);

  useEffect(() => {
    setCalculation(() => count * 2);
  }, [count]); // when count change, useEffect will be triggered

  return (
    <>
      <p>Count: {count}</p>
      <button onClick={() => setCount((c) => c + 1)}>+</button> //when button clicked, count change and the component will be rendered again
      <p>Calculation: {calculation}</p>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Counter />);
```







## useContext

React Context is a way to manage **state globally**.

It can be used together with the `useState` Hook to share state between deeply nested components more easily than with `useState` alone.

```jsx
import { useState, createContext, useContext } from "react"; //import
import ReactDOM from "react-dom/client";

const UserContext = createContext(); //1 initialize a usecontext

function Component1() {
  const [user, setUser] = useState("Jesse Hall"); // 2 initialize a state 

  return (
    <UserContext.Provider value={user}> 
      <h1>{`Hello ${user}!`}</h1>
      <Component2 />
    </UserContext.Provider>
  );//3 wrap the tree of components that need the state Context, then all components inside the tree can access the state.
}

function Component2() {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 />
    </>
  );
}


function Component3() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 3</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Component1 />);
```



## useRef

The `useRef` Hook allows you to **persist values between renders**.

It can be used to store a mutable value that **does not cause a re-render** when updated.

```jsx
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom/client";

function App() {
  const [inputValue, setInputValue] = useState(""); //change of inputValue causes re-render
  const count = useRef(0); //change of count doesn't cause re-render
    //useRef() only returns one item. It returns an Object called current.
    //It's like doing this: const count = {current: 0}. We can access the count by using count.current.

  useEffect(() => {
    count.current = count.current + 1;
  });

  return (
    <>
      <input
        type="text"
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h1>Render Count: {count.current}</h1>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```



## useReducer



## useCallback

The `useCallback` Hook only runs when one of its dependencies update.

It prevent function from changing when the component is re-render, unless its dependency changes.



Every time a component re-renders, its functions get recreated.

```jsx
const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = () => {
    setTodos((t) => [...t, "New Todo"]);
  };

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

```jsx
//Todos.js

import { memo } from "react";

const Todos = ({ todos, addTodo }) => {
  console.log("child render");
  return (
    <>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
    </>
  );
};

export default memo(Todos);
```

Todos component will be re-rendered when count change, that is cuz when count change, App re-render, then addTodo() get re-created.

To prevent it,

```
const addTodo = useCallback(() => {
    setTodos((t) => [...t, "New Todo"]);
  }, [todos]);
```



## useMemo

