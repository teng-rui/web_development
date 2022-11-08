# NodeJS



- node和js的关系：node.js是js的一个运行环境，是jsp和服务端的jsp的运行环境的组合。

- npm是node的包管理器。node中包含有npm，安装好node后，也会发现npm已安装。

- npm 安装 Node.js 模块语法格式如下：`$ npm install <Module Name>`

- 使用 npm 命令安装常用的 Node.js web框架模块 **express**: `$ npm install express`

- VS code 是开发环境。

- node文件以.js 后缀，在terminal 调用node fileName.js 即运行node文件。

- **Web Server**

  - Nginx和apache是server。tomcat是implementation。node.js是runtime。

  - Tomcat 最好跟 Java 配合，NodeJS只能用js语言，Apache 通常跟 PHP 配合。但也不排除Apache能跟 Node.js 配合反向代理。跟 Node.js 关系最好的还算是 Nginx。

  - 当然你在你的服务器上直勾勾挂个 Node.js 监听 80 端口对外也不是不可以。但是通常真正线上（个人玩具除外）的做法是，Node.js 监听本地的某个端口，然后前面挂个 Nginx 监听 80 端口反向代理到 Node.js 上。

# Module

module is library.

**include modules:**

```
var http = require('http');
var express = require('express');
```

**create own module**, in one file called myfirstmodule.js :

```
exports.myDateTime = function () {
  return Date();
};
```

import the file in another file:

```
var dt = require('./myfirstmodule');
dt.myDateTime()

```

在java里，每个文件名即public类名，import该文件，即可以调用该public类的public成员

在javascript中，每个文件中的变量和函数可以不包含在类中，引用一个文件，即可以调用该文件中的export成员。

## HTTP Module

- Allows Node.js to transfer data over the Hyper Text Transfer Protocol (HTTP)
- Create an HTTP server that listens to server ports and gives a response back to the client.

```javascript
//1 include http module
var http = require('http');

//2 create an HTTP server using createServer method, The function passed into the http.createServer() method, will be executed when someone tries to access the computer on port 8080.
http.createServer(function (req, res) {
  res.write('Hello World!'); //write a response to the client
  res.end(); //end the response
}).listen(8080); //the server object listens on port 8080

//3 url
//The function passed into the http.createServer() has a **req** argument that represents the request from the client, as an object (http.IncomingMessage object).
//This object has a property called "url" req.url which holds the part of the url that comes after the domain name
//req.url can be split using built-in module:url
var url = require('url');
var q = url.parse(req.url, true).query;
var a=q.propertyName
```

req和res是http.ServerRequest对象和http.ServerResponse对象

## FS Module

The Node.js file system module allows you to work with the file system on your computer.

It can read,create,update, rename, delete files.

```javascript
var fs = require('fs');

//read file
fs.readFile('demofile1.html', function(err, data) {
    //code
  });// async function


//update files
//.appendFile() append content to file
fs.appendFile('mynewfile1.txt', ' This is my text.', function (err) {
  if (err) throw err;
  console.log('Updated!');
});
//.writeFile() replace content of file
fs.writeFile('mynewfile3.txt', 'This is my text', function (err) {
  if (err) throw err;
  console.log('Replaced!');
});


//create file
//.appendFile() and .writeFile(), when file doesn't exist, they will create a file
fs.open('mynewfile2.txt', 'w', function (err, file) {
  if (err) throw err;
  console.log('Saved!');
});
// the second argument 'w' means the file is open for writing, will create a file it the file doesn;t exist


//delete file
fs.unlink('mynewfile2.txt', function (err) {
  if (err) throw err;
  console.log('File deleted!');
});


//rename file
fs.rename('mynewfile1.txt', 'myrenamedfile.txt', function (err) {
  if (err) throw err;
  console.log('File Renamed!');
});
```



## URL Module

The URL module splits up a web address into readable parts.

```js
var url = require('url');

//Parse an address with the url.parse() method, and it will return a URL object with each part of the address as properties
var adr = 'http://localhost:8080/default.htm?year=2017&month=february';
var q = url.parse(adr, true);
console.log(q.host); //returns 'localhost:8080'
console.log(q.pathname); //returns '/default.htm'
console.log(q.search); //returns '?year=2017&month=february'

var qdata = q.query; //returns an object: { year: 2017, month: 'february' }
console.log(qdata.month); //returns 'february'
```

## Other modules

Not built-in module nodemailer and Formidable can be used to send email to others and receive files from cliends.

```
var nodemailer = require('nodemailer');

var transporter = nodemailer.createTransport({
  service: 'gmail',
  auth: {
    user: 'youremail@gmail.com',
    pass: 'yourpassword'
  }
});

var mailOptions = {
  from: 'youremail@gmail.com',
  to: 'myfriend@yahoo.com',
  subject: 'Sending Email using Node.js',
  text: 'That was easy!'
};

transporter.sendMail(mailOptions, function(error, info){
  if (error) {
    console.log(error);
  } else {
    console.log('Email sent: ' + info.response);
  }
});
```

```
var http = require('http');
var formidable = require('formidable');
var fs = require('fs');

http.createServer(function (req, res) {
  if (req.url == '/fileupload') {
    var form = new formidable.IncomingForm(); //initialize an object
    //form.parse 解析发来的文件，解析成功则执行rename
    form.parse(req, function (err, fields, files) {
      var oldpath = files.filetoupload.filepath;
      var newpath = 'C:/Users/Your Name/' + files.filetoupload.originalFilename;
      //保存文件到新地址
      //rename成功则结束res
      fs.rename(oldpath, newpath, function (err) {
        if (err) throw err;
        res.write('File uploaded!');
        res.end();
      });
 });
  } else {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');
    res.write('<input type="file" name="filetoupload"><br>');
    res.write('<input type="submit">');
    res.write('</form>');
    return res.end();
  }
}).listen(8080);
```



# **Event Loop**

Node.js 几乎每一个 API 都是支持回调函数的。大部分API都是异步的。

执行异步操作的函数将回调函数作为最后一个参数， 回调函数接收错误对象作为第一个参数。

```js
var fs = require("fs");

fs.readFile('input.txt', function (err, data) {
   if (err){
      console.log(err.stack);
      return;
   }
   console.log(data.toString());
});
//如果在读取文件过程中发生错误，错误 err 对象就会输出错误信息。如果没发生错误，readFile 跳过 err 对象的输出，文件内容就通过回调函数输出。
```

Node.js 使用**事件驱动**模型，Node.js 基本上所有的事件机制都是用设计模式中**观察者模式**实现。在事件驱动模型中，会生成一个主循环来监听事件，当检测到事件时触发处理函数(observer)。

Event Module可以设计自己的事件和处理函数。

```javascript
var events = require('events');
var eventEmitter = new events.EventEmitter();

//Create an event handler:
var myEventHandler = function () {
  console.log('I hear a scream!');
}

//Assign the event handler to an event:
eventEmitter.on('scream', myEventHandler);

//Fire the 'scream' event: 当scream事件被emit时，myEventHandler会被触发。
//类似异步函数的回调，promise的then
eventEmitter.emit('scream');
```



类似，当web server接收到请求，就把它关闭然后进行处理，然后去服务下一个web请求。 当这个请求完成，它被放回处理队列，当到达队列开头，这个结果被返回给用户。这个模型非常高效可扩展性非常强，因为 webserver 一直接受请求而不等待任何读写操作。（这也称之为非阻塞式IO或者事件驱动IO）



# Routing

根据http请求的http.ServerRequest.url, get/post 参数等，决定触发不同的任务，即routing.

without express: url module 的 url.parse(string) method 可以解析req.url为对象，根据该对象的pathname， query 成员可以触发不同函数。

with express: 用中间件

```js
var http = require("http");
var url = require("url");

function route(pathname) {
  //code using pathname
}

function onRequest(request, response) {
    var pathname = url.parse(request.url).pathname;
    console.log("Request for " + pathname + " received.");
 
    route(pathname);
 
    response.writeHead(200, {"Content-Type": "text/plain"});
    response.write("Hello World");
    response.end();
  }
http.createServer(onRequest).listen(8888);
```



# GET POST

Http请求有get和post方法。

get 方法的内容嵌套在url，可以url.parse(req.url).query 获得对象。

POST 请求的内容全部的都在请求体中，http.ServerRequest对象并没有一个属性内容为请求体。（express的req对象好像有）

```
```



# Express

Express 框架核心特性：

- 可以设置中间件来响应 HTTP 请求。
- 定义了路由表用于执行不同的 HTTP 请求动作。
- 可以通过向模板传递参数来动态渲染 HTML 页面。

安装express

```
$ cnpm install express --save

$ cnpm install body-parser --save
$ cnpm install cookie-parser --save
$ cnpm install multer --save
```

1. express监听

```
var express = require('express');
var app = express();

var server = app.listen(8081, function () {
 
  var host = server.address().address
  var port = server.address().port
 
  console.log("应用实例，访问地址为 http://%s:%s", host, port)
 
})
```

2. express请求和响应

```
app.get('/', function (req, res) {
   // --
})

app.post('/', function (req, res) {
   //code
})
```

**Request 对象** - request 对象表示 HTTP 请求，包含了请求查询字符串，参数，内容，HTTP 头部等属性。常见属性有：

- req.protocol：获取协议类型
- req.body / req.cookies：获得「请求主体」/ Cookies
- req.path：获取请求路径
- req.query：获取URL的查询参数串
- req.route：获取当前匹配的路由

**Response 对象** - response 对象表示 HTTP 响应，即在接收到请求时向客户端发送的 HTTP 响应数据。常见属性有：

1. res.cookie(name，value [，option])：设置Cookie
2. res.clearCookie()：清除Cookie
3. res.json()：传送JSON响应
4. res.send()：传送HTTP响应
5. res.status()：设置HTTP状态码
6. res.set()：设置HTTP头，传入object可以一次设置多个头

express.response request对象和http.ServerRequest, http.ServerResponse 不一样，都用来表示http请求的信息。



3. **静态文件**

```
app.use('/public', express.static('public'));
```

/public下的文件不必设置路由，只要客户输入服务器url/public/../.. 就会返回对应文件（图片，文本，html,,,)

4. **中间件**

app.use() 实现通用的中间件注册

app.get() app.post()实现与http请求相关的中间件注册

应用级中间件

路由及中间件

错误处理中间件



# RESTful API

REST即表述性状态传递（英文：Representational State Transfer，简称REST

表述性状态转移是一组架构约束条件和原则。满足这些约束条件和原则的应用程序或设计就是RESTful。需要注意的是，REST是设计风格而不是标准。REST通常基于使用HTTP，URI，和XML（标准通用标记语言下的一个子集）以及HTML（标准通用标记语言下的一个应用）这些现有的广泛流行的协议和标准。REST 通常使用 JSON 数据格式。

RESTful API: 

监听端口，根据http请求的方法(get,post)以及url，触发不同任务。(瑞瑞个人理解，这不就是路由到任务吗)



# MySQL

```
npm install mysql
```

```js
var mysql = require('mysql');

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "yourpassword",
  database: "mydb", //optional
  port:3306// optional default 3306

});

var sql = "INSERT INTO customers (name, address) VALUES ?";
  var values = [
    ['John', 'Highway 71'],
    ['Peter', 'Lowstreet 4'],
    ['Amy', 'Apple st 652'],
    ['Hannah', 'Mountain 21'],
    ['Michael', 'Valley 345'],
    ['Sandy', 'Ocean blvd 2'],
    ['Betty', 'Green Grass 1'],
    ['Richard', 'Sky st 331'],
    ['Susan', 'One way 98'],
    ['Vicky', 'Yellow Garden 2'],
    ['Ben', 'Park Lane 38'],
    ['William', 'Central st 954'],
    ['Chuck', 'Main Road 989'],
    ['Viola', 'Sideway 1633']
  ];

con.connect(function(err) {
  if (err) throw err;
  console.log("Connected!");
  con.query(sql,[value], function (err, result) {
    if (err) throw err;
    console.log("succed");
  });
});
```



# MongoDB

```
npm install mongodb
```

create database

```js
var MongoClient = require('mongodb').MongoClient; //creating a MongoClient object
var url = "mongodb://localhost:27017/mydb"; //specify a connection URL with the correct ip address and the name of the database, MongoDB will create the database if it does not exist, and make a connection to it


MongoClient.connect(url, function(err, db) {
  if (err) throw err;
  console.log("Database created!");
  db.close();
});
```

create collection and insertone

```
var MongoClient = require('mongodb').MongoClient;
var url = "mongodb://localhost:27017/";

MongoClient.connect(url, function(err, db) {
  if (err) throw err;
  var dbo = db.db("mydb");
  dbo.createCollection("customers", function(err, res) {
    if (err) throw err;
    console.log("Collection created!");
  });
  
  var myobj = { name: "Company Inc", address: "Highway 37" };
  dbo.collection("customers").insertOne(myobj);
});
```

CRUD操作和单独的MongoDB一样，都是collection.crud()。

Aggregate

```
dbo.collection('orders').aggregate([
    { $lookup:
       {
         from: 'products',
         localField: 'product_id',
         foreignField: '_id',
         as: 'orderdetails'
       }
     }
    ]).toArray(function(err, res) {
    if (err) throw err;
  });
```



Tips:

- 返回多条records，可以转换为array
- mongodb, mysql 的操作都是async的，都可以在操作中加入最后一个argument，回调函数，在回调函数中可以关闭连接.

```
dbo.collection("customers").find({}).toArray(function(err, result) {
    if (err) throw err;
    console.log(result);
    db.close();
  });
```

