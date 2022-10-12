# HTML document structure![img](https://www.runoob.com/wp-content/uploads/2013/06/02A7DD95-22B4-4FB9-B994-DDB5393F7F03.jpg)

- The `<!DOCTYPE html>` declaration defines that this document is an HTML5 document
- 网络上有很多不同的文件，如果能够正确声明HTML的版本，浏览器就能正确显示网页内容。doctype 声明是不区分大小写的 not case sensitive
- The `<html>` element is the root element of an HTML page
- The `<head>` element contains meta information about the HTML page。如 **<meta charset="utf-8">** 定义网页编码格式为 **utf-8**。
- The `<title>` element specifies a title for the HTML page (which is shown in the browser's title bar or in the page's tab)
- The `<body>` element defines the document's body, and is a container for all the visible contents, such as headings, paragraphs, images, hyperlinks, tables, lists, etc.



# 什么是HTML?

HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言: **H**yper**T**ext **M**arkup **L**anguage
- HTML 不是一种编程语言，而是一种**标记**语言  **M**arkup **L**anguage
- 标记语言是一套**标记标签** (markup tag)
- HTML 使用标记标签来**描述**网页
- HTML 文档包含了HTML **标签**及**文本**内容
- HTML文档也叫做 **web 页面**

# How to View HTML Source

Have you ever seen a Web page and wondered "Hey! How did they do that?"

## View HTML Source Code:

Right-click in an HTML page and select "View Page Source" (in Chrome) or "View Source" (in Edge), or similar in other browsers. This will open a window containing the HTML source code of the page.

## Inspect an HTML Element:

Right-click on an element (or a blank area), and choose "Inspect" or "Inspect Element" to see what elements are made up of (you will see both the HTML and the CSS). You can also edit the HTML or CSS on-the-fly in the Elements or Styles panel that opens.

# HTML Element and Tag

- HTML 标签是由*尖括号*包围的关键词，比如 <html>
- An HTML **element** is defined by a start tag, some content, and an end tag
- **空元素 empty elements** have no content， e.g. < br> <hr> <img><base><link><meta>
- 空元素**在开始标签中进行关闭**（以开始标签的结束而结束）即使< br > 在所有浏览器中都是有效的，但使用 < br / >是更长远的保障。
- 大多数 HTML 元素可拥有**属性**
- 大多数 HTML 元素可以嵌套 nested
- 标签大小写不敏感 not case sensitive，最好小写 

## HTML Common element

### HTML 标题

HTML 标题（Heading）是通过<h1> - <h6> 标签来定义的。

< hr > 标签在 HTML 页面中创建水平线。

### HTML 注释

```
<!-- 这是一个注释 -->

<!--
<p>Look at this cool image:</p>
<img border="0" src="pic_trulli.jpg" alt="Trulli">
-->

<p>This <!-- great text --> is a paragraph.</p>
```

### HTML 段落

HTML 段落是通过标签 <p> 来定义的。每个段落自动换行 The browser will automatically **remove** any extra spaces and lines when the page is displayed.

use  < br/>  inside a <p> and < /p> to break text to a new line.

use  < hr/>  between <p> and < /p> pairs to show a horizontal line.

### HTML Formatting 格式化标签 

用于文本的标签 can be nested inside <p> or used separately

HTML 文本格式化标签

| 标签   | 描述                         |
| :----- | :--------------------------- |
| b      | 定义粗体文本 Bold text       |
| em     | 定义着重文字 Emphasized text |
| i      | 定义斜体字 Italic text       |
| small  | 定义小号字 Smaller text      |
| strong | 定义加重语气 Important text  |
| sub    | 定义下标字 Subscript text    |
| sup    | 定义上标字  Superscript text |
| ins    | 定义插入字 Inserted text     |
| del    | 定义删除字 Deleted text      |

HTML "计算机输出" 标签

| 标签 | 描述                                        |
| :--- | :------------------------------------------ |
| code | 定义计算机代码                              |
| kbd  | 定义键盘码                                  |
| samp | 定义计算机代码样本                          |
| var  | 定义变量                                    |
| pre  | 定义预格式文本 (keep space and blank lines) |

HTML 引文, 引用, 及标签定义

| 标签       | 描述                                                         |
| :--------- | :----------------------------------------------------------- |
| abbr       | 定义缩写                                                     |
| address    | 定义地址                                                     |
| bdo        | 定义文字方向                                                 |
| blockquote | 定义长的引用 Browsers usually indent 缩进 elements           |
| q          | 定义短的引用语 short inline quotation，browser normally insert quotation marks around the quotation. |
| cite       | 定义引用、引证 Defines the title of a work                   |
| dfn        | 定义一个定义项目。                                           |

```html
<p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>

<bdo dir="rtl">This text will be written from right to left</bdo>
```



### HTML 超链接

HTML 链接是通过标签 <a> 来定义的。在 **href 属性**中指定链接的地址。link's destination is specified in the `href` attribute. 

```html
<a href="https://www.runoob.com/">链接文本</a> 
最后一个斜杠要加，否则服务器会自己加，产生两次http请求
```

 *"链接文本"* 不必一定是文本。图片或其他 HTML 元素都可以成为链接。

使用 **target 属性**，你可以定义被链接的文档在何处显示。

```html
<a target="_blank|_self|_parent|_top|framename">
```

| Value       | Description                                                  |
| :---------- | :----------------------------------------------------------- |
| _blank      | Opens the linked document in a new window or tab             |
| _self       | default, Opens the linked document in the same frame as it was clicked (this is default) |
| _parent     | Opens the linked document in the parent frame                |
| _top        | Opens the linked document in the full body of the window     |
| *framename* | Opens the linked document in the named iframe                |

**id 属性**可用于创建一个 HTML 文档书签。

```html
<a id="tips">1234</a>
<a href="#tips">访问1234</a>
<a href="https://www.runoob.com/html/html-links.html#tips"> 从另一页面链接到1234
```

Use `mailto:` inside the `href` attribute to create a link that opens the user's **email program**

```
<a href="mailto:tengrui@gmail.com">Send email</a>
```

**Link css**

<style>
    a:link {  
        color: green;  
        background-color: transparent;  
        text-decoration: none;
    }
    a:visited {  
        color: pink;  
        background-color: transparent;  
        text-decoration: none;
    }
    a:hover {  
        color: red;  
        background-color: transparent;  
        text-decoration: underline;
    }
    a:active {  
        color: yellow;  
        background-color: transparent;  
        text-decoration: underline;
    }
</style>

### HTML 图像

- 是通过标签 <img> 来定义的. <img> 是空标签，只包含属性，并且没有闭合标签(<img/>也对)
- src属性指定图像的url地址 source file

- alt 属性用来为图像定义一串预备的可替换的文本 alternative text。在浏览器无法载入图像时，替换文本属性告诉读者她们失去的信息

- height（高度） 与 width（宽度）属性用于设置图像的高度与宽度 in pixels
- png，jpg， gif，svg, ..... is allowed
- image can used as the content of a link. < a href=" ">< img src="">< /a>

```html
<p>一个来自文件夹中的图像:</p>
<img src="/images/chrome.gif" alt="Google Chrome" width="33" height="32">
<p>一个来自菜鸟教程的图像:</p>
<img src="//www.runoob.com/images/logo.png" alt="runoob.com" width="500" height="600">
<p>一个来自同目录的图像:</p>
<img src="img_girl.jpg" alt="Girl in a jacket" style="width:500px;height:600px;">
<p>Use the CSS float property to let the image float to the right or to the left of a text:</p>
<p><img src="smiley.gif" alt="Smiley face" style="float:left;width:42px;height:42px;">
The image will float to the left of the text.</p>
```

**Image Map**

```html
<head>

<map name="workmap">
  <area shape="circle" coords="337,300,44" href="coffee.htm" onclick="myFunction()">
</map>

<script>
function myFunction() {
  alert("You clicked the coffee cup!");
}
</script>
</head>

<body>
<h2>Image Maps</h2>
<p>Click on the cup of coffee to execute a JavaScript function:</p>
<img src="workplace.jpg" alt="Workplace" usemap="#workmap" width="400" height="379">
</body>
```

Aroung the page or text

```html
<style>
body {
  background-image: url('img_girl.jpg');
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: 100% 100%;
}
</style>
```



### HTML < head> 元素

可以添加在头部区域的元素标签为: <title>, <style>, <meta>, <link>, <script>, <noscript> 和 <base>。

```html
<head>
<title>A Meaningful Page Title</title>
    
<base href="http://www.runoob.com/images/" target="_blank">
    
<link rel="stylesheet" type="text/css" href="mystyle.css">
    
<style type="text/css">
body {background-color:yellow}
p {color:blue}
</style>

<meta charset="UTF-8">
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
<meta name="description" content="免费 Web & 编程 教程">
<meta name="author" content="Runoob">
    
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<！-- viewport is the user's visible area of a web page. It varies with the device -->
</head>
```



**< title>** 标签定义了文档的标题，在 HTML/XHTML 文档中是**必须**的。

- 定义了浏览器工具栏的标题
- 当网页添加到收藏夹时，显示在收藏夹中的标题
- 显示在搜索引擎结果页面的标题

< base > 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接:

< link> 标签定义了文档与外部资源之间的关系。通常用于链接到样式表

< style> 标签定义了HTML文档的样式文件引用地址.在<style> 元素中也可直接添加样式来渲染 HTML 文档

meta标签描述了一些基本的元数据, 元数据不显示在页面上，但会被浏览器解析。通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。

< script>标签用于加载脚本文件，如： JavaScript。



### HTML Favicon

A favicon image is displayed to the left of the page title in the browser tab

<head>
 <title>My Page Title</title>
 <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
</head>

### HTML 表格

表格由 <table> 标签来定义。每个表格均有若干行（由 <tr> 标签定义），每行被分割为若干单元格（由 <td> 标签定义）。数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等。

```html
<table border="1">
    <caption>Monthly savings</caption>
    <colgroup>
    <col span="2" style="background-color:red">
    <col style="background-color:yellow">
  	</colgroup>
    <tr>
        <th>Header 1</th>
        <th>Header 2</th>
    </tr>
    <tr>
        <td>row 1, cell 1</td>
        <td>row 1, cell 2</td>
        <td>row 1, cell 3</td>
    </tr>
    <tr>
        <td>row 2, cell 1</td>
        <td colspan="2">row2, cell2</td>
    </tr>
</table>

<!-- border定义边框-->
<!--表格的表头使用 <th> 标签进行定义。-->
<!--表格标题 caption-->
<!--colgroup定义列样式-->


<h4>单元格跨两行:</h4>
<table border="1">
<tr>
  <th>First Name:</th>
  <td>Bill Gates</td>
</tr>
<tr>
  <th rowspan="2">Telephone:</th>
  <td>555 77 854</td>
</tr>
<tr>
  <td>555 77 855</td>
</tr>
</table>
```



### HTML 列表

无序列表使用 <ul> 标签 有序列表始于 <ol> 标签

```html
<ul>
<li>Coffee</li>
<li>Milk</li>
</ul>

<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>
<!--li 列表项-->

<dl>
<dt>Coffee</dt>
<dd>- black hot drink</dd>
<dt>Milk</dt>
<dd>- white cold drink</dd>
</dl>
<!--dl定义自定义列表 dt自定义列表项目 dd 定义自定列表项的描述-->
```

## HTML 表单和输入

表单用于收集不同类型的用户输入,表单使用标签 < form> 来设置,多数情况下被用到的表单标签是输入标签（< input>）。输入类型是由类型属性（type）定义的

常用输入类型属性：text,password,radio,checkbox,submit

```html
<form name="input" action="html_form_action.php" method="get">
    
<fieldset>
<legend>Personal information:</legend>
First name: <input type="text" name="firstname"><br>
Last name: <input type="text" name="lastname"><br>
Password: <input type="password" name="pwd"><br>
    
<input type="radio" id="html" name="fav_language" value="HTML">
<label for="html">HTML</label><br>
<input type="radio" id="css" name="fav_language" value="CSS">
<label for="css">CSS</label><br>
    <!--The for attribute of the <label> tag should be equal to the id attribute of the <input> element to bind them together.The <label> element also help users who have difficulty clicking on very small regions (such as radio buttons or checkboxes)-->


    
<input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
<input type="checkbox" name="vehicle" value="Car">I have a car<br>

    
<input type="submit" value="Submit">
<input type="reset">
<input type="button" onclick="alert('Hello World!')" value="Click Me!">
    
</fieldset>
<!--fieldset and legend decode the borader-->
</form>

```

### Form Attributes

action, method, target, 

```
<form action="/action_page.php" target="_blank">
<form action="/action_page.php" method="get">
```

**Notes on GET:**

- Appends the form data to the URL, in name/value pairs
- NEVER use GET to send sensitive data! (the submitted form data is visible in the URL!)
- The length of a URL is limited (2048 characters)
- Useful for form submissions where a user wants to bookmark the result
- GET is good for non-secure data, like query strings in Google

**Notes on POST:**

- Appends the form data inside the body of the HTTP request (the submitted form data is not shown in the URL)
- POST has no size limitations, and can be used to send large amounts of data.
- Form submissions with POST cannot be bookmarked

### Form Elements

```html
<!--a drop-down list-->
<select>
<option>苹果</option>
<option selected="selected">香蕉</option>
<option>樱桃</option>
</select>

<button type='submit/rest/button'>submit</button>
<!--Always specify the type attribute for the button element-->

<!--The <fieldset> element is used to group related data in a form.
The <legend> element defines a caption for the <fieldset> element.-->
<form action="/action_page.php">
  <fieldset>
    <legend>Personalia:</legend>
    <label for="fname">First name:</label><br>
    <input type="text" id="fname" name="fname" value="John"><br>
    <input type="submit" value="Submit">
  </fieldset>
</form>
```

### Input attribute

- value-  initial value for an input field

- readonly - read-only. The value of a read-only input field will be sent when submitting the form!

- disabled - un-clickable. The value of a disabled input field will not be sent when submitting the form!

- maxlength -  the maximum number of characters

- size

- multiple attribute specifies that the user is allowed to enter more than one value

- placeholder

- required

  ```html
  <input type="text" id="fname" name="fname" value="John" readonly ><br>
  <input type="text" id="fname" name="fname" value="John" disabled size="4"><br>
  <input type="text" id="pin" name="pin" maxlength="4" size="4">
  <input type="file" id="files" name="files" multiple>
  <input type="tel" id="phone" name="phone"
    placeholder="123-45-678" required>
  ```

- form

- formaction

- formmethod

- form target

  ```html
  <form action="/action_page.php">
    <label for="email">Enter your email:</label>
    <input type="email" id="email" name="email"><br><br>
    <input type="submit" value="Submit">
    <input type="submit" formaction="/action_page2.php" value="Submit as Admin">
    <input type="submit" formmethod="post" value="Submit using POST">
    <input type="submit" formtarget="_blank" value="Submit to a new window/tab">
  </form>
  
  <label for="lname">Last name:</label>
  <input type="text" id="lname" name="lname" form="form1">
  ```

  



## HTML 区块元素，内联元素

大多数 HTML 元素被定义为**块级元素** block-level element 或**内联元素** Inline element.

块级元素在浏览器显示时，通常会以新行来开始（和结束）。

实例:<div> <h1>, <p>, <ul>,<form>, <table>,<header>,<footer>,<section>

内联元素在显示时通常不会以新行开始。

实例: <b>, <td>, <a>, <img><span>

------

HTML 可以通过 <div> 和 <span>将元素组合起来。

HTML <div> 元素是块级元素，它可用于组合其他 HTML 元素的容器。< div> 元素没有特定的含义。由于它属于块级元素，浏览器会在其前后显示折行。如果与 CSS 一同使用，< div> 元素可用于对大的内容块设置样式属性。< div> 元素的另一个常见的用途是文档布局。

 < span> 元素是内联元素，可用作文本的容器 < span> 元素也没有特定的含义。当与 CSS 一同使用时，< span> 元素可用于为部分文本设置样式属性。

### HTML 布局 - 使用< div> 元素

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head>
<body>
 
<div id="container" style="width:500px">
 
<div id="header" style="background-color:#FFA500;">
<h1 style="margin-bottom:0;">主要的网页标题</h1></div>
 
<div id="menu" style="background-color:#FFD700;height:200px;width:100px;float:left;">
<b>菜单</b><br>
HTML<br>
CSS<br>
JavaScript</div>
 
<div id="content" style="background-color:#EEEEEE;height:200px;width:400px;float:left;">
内容在这里</div>
 
<div id="footer" style="background-color:#FFA500;clear:both;text-align:center;">
版权 © runoob.com</div>
 
</div>
 
</body>
</html>
```



## HTML Iframe

The HTML `<iframe>` tag specifies an inline frame.

An inline frame is used to embed another document within the current HTML document.

```html
<iframe src="demo_iframe.htm" name="iframe_a" width="200" height="200"></iframe>
<p><a href="https://www.runoob.com" target="iframe_a">RUNOOB.COM</a></p>
```

## Semantic element

A semantic Web allows data to be shared and reused across applications, enterprises, and communities.

Helps grouping contents, and add style together. <article> <aside> <details> <figcaption> <figure> <footer><header><main> <mark> <nav> <section> <summary> <time>

```html
<figure>
  <img src="pic_trulli.jpg" alt="Trulli">
  <figcaption>Fig1. - Trulli, Puglia, Italy.</figcaption>
</figure>
```



## HTML Graphics

### Canvas

Always specify an `id` attribute (to be referred to in a script), and a `width` and `height` attribute to define the size of the canvas.

```html
<canvas id="myCanvas" width="250" height="300"
style="border:1px solid #d3d3d3;">
Your browser does not support the HTML canvas tag.</canvas>

<p><button onclick="myCanvas()">Try it</button></p>

<script>
function myCanvas() {
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");
  var img = document.getElementById("scream");
  ctx.drawImage(img,10,10);
}
</script>
```

### SVG

Scalable Vector Graphics

```html
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40"
  stroke="green" stroke-width="4" fill="yellow" />
Sorry, your browser does not support inline SVG.
</svg>
```

Canvas VS SVG

| Canvas                                                       | SVG                                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| Resolution dependent <br>No support for event handlers <br>Poor text rendering capabilities<br>You can save the resulting image as .png or .jpg<br>Well suited for graphic-intensive games | Resolution independent (vecter, does not distort)<br> Support for event handlers (XML based)<br>Best suited for applications with large rendering areas (Google Maps)<br>Slow rendering if complex (anything that uses the DOM a lot will be slow)<br>Not suited for game applications |

## HTML Media

images, music, sound, videos, records, films, animations...

Vedio format: MP4, WebM, and Ogg formats are supported by HTML.

Audio format: MP3, MP4, Ogg, WAV formats are supported by HTML.

### Vedio

The `controls` attribute adds video controls, like play, pause, and volume.

Always include `width` and `height` attributes. If height and width are not set, the page might flicker while the video loads.

The `<source>` element allows you to specify alternative video files which the browser may choose from. The browser will use **the first recognized format.**

The text between the `<video>` and `</video>` tags will only be displayed in browsers that do not support the `<video>` element.

```html
<video width="320" height="240" controls autoplay muted>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
Your browser does not support the video tag.
</video>


```

### Audio

```
<audio controls autoplay muted>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>
```

### Youtube Vedio

Converting videos to different formats can be difficult and time-consuming.

An easier solution is to let YouTube play the videos in your web page.

- Upload the video to YouTube
- Take a note of the video id
- Define an element in your web page`<iframe>`
- Let the attribute point to the video URL`src`
- Use the and attributes to specify the dimension of the player`width`` height`
- Add any other parameters to the URL (0 or 1)

```html
<iframe width="420" height="315"
src="https://www.youtube.com/embed/tgbNymZ7vqY?controls=0&autoplay=1&mute=1">
</iframe>
```



# HTML 属性

- HTML 元素可以设置**属性**
- 属性可以在元素中添加**附加信息**
- 属性一般描述于**开始标签**, always specified in **the start tag**
- Always Use **Lowercase** Attributes
- Always **Quote** Attribute Values
- 属性总是以名称/值对 name/value pairs 的形式出现，**比如：name="value"**。数字value也要引号。

## href Attribute

The `<a>` tag defines a hyperlink. The `href` attribute specifies the URL of the page the link goes to:

```html
<a href="http://www.runoob.com">这是一个链接</a>
```

## src Attribute

The `<img>` tag is used to embed an image in an HTML page. The `src` attribute specifies the path to the image to be displayed:

**1. Absolute URL** - Links to an external image that is hosted on another website. Example: src="https://www.w3schools.com/images/img_girl.jpg".

```html
<img src="img_girl.jpg">
```

**2. Relative URL** - Links to an image that is hosted within the website. Here, the URL does not include the domain name. 

- If the URL begins **without** a slash, it will be relative to the current page. Example: src="img_girl.jpg".当前目录和文件目录在同一个目录里. 
- If the URL begins with a slash, it will be relative to the domain. Example: src="/images/img_girl.jpg". 代表根目录
- src="../picture.jpg"， located in the folder one level up from the current folder

**Tip:** It is almost always best to use relative URLs. They will not break if you change domain.



## width and height Attributes

```
<img src="img_girl.jpg" width="500" height="600">
```

## alt Attribute

```
<img src="img_girl.jpg" alt="Girl with a jacket">
```

## style Attribute

The `style` attribute is used to add styles to an element, such as color, font, size, and more.

```html
Use for background color background-color
Use for text colors color
Use for text fonts font-family
Use for text sizes font-size
Use for text alignment text-align
Use for border border


<tagname style="property:value;">
    
<h1 style="text-align:center; color:red; font-size:100%; font-family:courier; border:2px solid Tomato;">Centered Heading</h1>
```

color can be specified by using a color name: tomato

colors can also be specified using RGB values rgb(255, 99, 71), HEX values\#ff6347, HSL valueshsl(9, 100%, 64%), RGBA values rgba(255, 99, 71, 0.5) , and HSLA values hsla(9, 100%, 64%, 0.5) .

## lang Attribute

You should always include the `lang` attribute inside the `<html>` tag, to declare the language of the Web page. 

```
<html lang="en">
<body>
...
</body>
</html>
```

## title Attribute

The `title` attribute defines some extra information about an element.

The value of the title attribute will be displayed as a tooltip when you mouse over the element:

```
<p title="I'm a tooltip">This is a paragraph.</p>
```



# HTML 样式- CSS

------

The word **cascading** means that a style applied to a parent element will also apply to all children elements within the parent. So, if you set the color of the body text to "blue", all headings, paragraphs, and other text elements within the body will also get the same color (unless you specify something else)!

CSS (Cascading Style Sheets)  可以通过以下方式添加到HTML中:

- **Inline** - by using the **`style` attribute** inside HTML elements
- **Internal** - by using a **`<style>` element in the `<head>`** section
- **External** - by using **a `<link>` element to link to an external CSS file**

```html
内联样式
<p style="color:blue;margin-left:20px;">这是一个段落。</p> 
<p style="font-family:arial;color:red;font-size:20px;">一个段落。</p>

内部样式表
<head>
<style type="text/css">
body {background-color:yellow;}
p {color:blue;}
</style>
</head>

外部样式表
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
<!-- rel 属性规定当前文档与被链接文档之间的关系。stylesheet 指明这是样式表 
The type attribute specifies the media type of the linked document/resource.

The most common value of type is "text/css". If you omit the type attribute, the browser will look at the rel attribute to guess the correct type. So, if rel="stylesheet", the browser will assume the type is "text/css".-->
    
</head>
```

## Class

The `class` attribute is often used to point to a class name in a style sheet. 

The class name is case sensitive!

```html
<head>
<style>
.city {
  background-color: tomato;
}
.main {
  text-align: center;
}
</style>
</head>
<body>

<div class="city main">
  <h2>London</h2>
  <p>London is the capital of England.</p>
</div>

</body>
</html>
```

The class name can also be used by JavaScript to perform certain tasks for specific elements.

```
<script>
function myFunction() {
  var x = document.getElementsByClassName("city");
  for (var i = 0; i < x.length; i++) {
    x[i].style.display = "none";
  }
}
</script>
```

## ID

```
<head>
<style>
#qwe {
  background-color: tomato;
}
</style>
</head>
<body>

<div id="qwe">
  <h2>London</h2>
</div>

</body>
</html>
```



# HTML Entities实体

在 HTML 中，某些字符是预留的。

在 HTML 中不能使用小于号（<）和大于号（>），这是因为浏览器会误认为它们是标签。

如果希望正确地显示预留字符，我们必须在 HTML 源代码中使用字符实体（character entities）。 字符实体类似这样：

&*entity_name*; &#*entity_number*;

如需显示小于号，我们必须这样写：

```
&lt; 或 &#60; 或 &#060;
```

**Non-breaking Space**, HTML 中的常用字符实体是不间断空格(&nbsp；),,连续的space只会保留一个，但连续的&nbsp；都会保留。

**Entity can also present symbols** and **Emoji** with an entity name, a decimal, and a hexadecimal value corresponding to their value in UTF-8.





# HTML Responsive Web Design

A responsive web design will automatically adjust for different screen sizes and viewports.

## setting view port at meta tag.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## responsive image: 

using width property / max-width

```html
<img src="img_girl.jpg" style="width:100%;">
<!-- the image will be responsive and scale up and down according to the window size-->

<img src="img_girl.jpg" style="max-width:100%;height:auto;">
<!-- the image will be responsive and scale down, but never scale up to be larger than its original size-->
```

## show different images for different window size

```html
<picture>
  <source srcset="img_smallflower.jpg" media="(max-width: 600px)">
  <source srcset="img_flowers.jpg" media="(max-width: 1200px)">
  <source srcset="flowers.jpg">
  <img src="img_flowers.jpg" alt="Flowers" style="width:auto;">
</picture>

<!-- show samll flowers for browser smaller than 600 px, img_flower for browser between 600 px - 1200px, otherwize show flowers-->
<!-- 顺序很重要 按先后顺序选择满足条件的, 类似switch in 找到满足的就跳出，default要放在最后-->
```

## responsive text 

```html
<p style="font-size:5vw;">Use the "vw" unit when sizing the text. 10vw will set the size to 10% of the viewport width.</p>

<p>Viewport is the browser window size. 1vw = 1% of viewport width. If the viewport is 50cm wide, 1vw is 0.5cm.</p>
```

## media query: 

define media query after default style. 

```html
<style>
* {
  box-sizing: border-box;
}

.left {
  background-color: #2196F3;
  padding: 20px;
  float: left;
  width: 20%; /* The width is 20%, by default */
}

.main {
  background-color: #f1f1f1;
  padding: 20px;
  float: left;
  width: 60%; /* The width is 60%, by default */
}

.right {
  background-color: #04AA6D;
  padding: 20px;
  float: left;
  width: 20%; /* The width is 20%, by default */
}

/* Use a media query to add a break point at 800px: */
@media screen and (max-width: 800px) {
  .left, .main, .right {
    width: 100%; /* The width is 100%, when the viewport is 800px or smaller */
  }
}
</style>

<!-- 类似独立的if语句，找到满足条件的还会往下查找， 所以default放前面-->
```

## CSS framework

boostrap, ....

# HTML API

## HTML Geolocation API

showPosition and showError is parameter for getCurrentPosition(), the former one is to be run when a geolocation is returned, otherwise the latter one is run.

```html
<p>Click the button to get your coordinates.</p>

<button onclick="getLocation()">Try It</button>

<p id="demo"></p>

<script>
var x = document.getElementById("demo");

function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition, showError);
  } else { 
    x.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function showPosition(position) {
  x.innerHTML = "Latitude: " + position.coords.latitude + 
  "<br>Longitude: " + position.coords.longitude;
}

function showError(error) {
  switch(error.code) {
    case error.PERMISSION_DENIED:
      x.innerHTML = "User denied the request for Geolocation."
      break;
    case error.POSITION_UNAVAILABLE:
      x.innerHTML = "Location information is unavailable."
      break;
    case error.TIMEOUT:
      x.innerHTML = "The request to get user location timed out."
      break;
    case error.UNKNOWN_ERROR:
      x.innerHTML = "An unknown error occurred."
      break;
  }
}
</script>
```

## HTML Drag and Drop API

```html
1. To make an element draggable, set the draggable attribute to true:
<img draggable="true">

2. Then, specify what should happen when the element is dragged.
function drag(ev) {
  ev.dataTransfer.setData("text", ev.target.id);
}
<img id="drag1" src="img_logo.gif" draggable="true" ondragstart="drag(event)" width="336" height="69">

3. The ondragover event specifies where the dragged data can be dropped.
By default, data/elements cannot be dropped in other elements. To allow a drop, we must prevent the default handling of the element. This is done by calling the event.preventDefault() method for the ondragover event:
4. When the dragged data is dropped, a drop event occurs.

function allowDrop(ev) {
  ev.preventDefault();
}
function drop(ev) {
  ev.preventDefault();
  var data = ev.dataTransfer.getData("text");
  ev.target.appendChild(document.getElementById(data));
}
<div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)"></div>

```

## HTML Web Storage API

With web storage, web applications can store data locally within the user's browser.

Unlike cookies, the storage limit is far larger (at least 5MB) and information is never transferred to the server.

HTML web storage provides two objects for storing data on the client:

- `window.localStorage` - stores data with no expiration date

- `window.sessionStorage` - stores data for one session (data is lost when the browser tab is closed)

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
      document.getElementById("result").innerHTML = "Sorry, your browser does not support web storage...";
    }
  }
  </script>
  </head>
  <body>
  
  <p><button onclick="clickCounter()" type="button">Click me!</button></p>
  <div id="result"></div>
  <p>Click the button to see the counter increase.</p>
  <p>Close the browser tab (or window), and try again, and the counter will continue to count (is not reset).</p>
  
  </body>
  ```

## HTML Web Worker API

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



## HTML SSE

A server-sent event is when a web page automatically gets updates from a server.

```html
<h1>Getting server updates</h1>
<div id="result"></div>

<script>
if(typeof(EventSource) !== "undefined") {
  var source = new EventSource("demo_sse.php");
  source.onmessage = function(event) {
    document.getElementById("result").innerHTML += event.data + "<br>";
  };
} else {
  document.getElementById("result").innerHTML = "Sorry, your browser does not support server-sent events...";
}
</script>
```



# Notes

## ID and Name

name：name 属性规定 input 元素的名称。

- 用于获取提交表单的某表单域信息， 作为可与服务器交互数据的HTML元素的服务器端的标示，比如input、select、textarea、框架元素(iframe、frame、 window的名字，用于在其他frame或window指定target)和button等，这些元素都与表单(框架元素作用于form的target)提交有关，浏览器会根据name来设定发送到服务器的request，在表单的接收页面只接收有name的元素, 所以赋ID的元素通过表单是接收不到值的。 我们可以在服务器端根据其Name通过Request.Params取得元素提交的值. 在form里面，如果不指定Name，就不会发送到服务器端 。
- 用途2: HTML元素Input type='radio'分组，我们知道radio button控件在同一个分组类，check操作是mutex的，同一时间只能选中一个radio，这个分组就是根据相同的Name属性来实现的。
- 在IMG元素和MAP元素之间关联的时候，如果要定义IMG的热点区域，需要使用其属性usemap，使usemap="#name"(被关联的MAP元素的Name)。

id就是Client端HTML元素的Identity(唯一标记），主要是在客户端脚本里用。

- label与form控件的关联, for属性指定与label关联的元素的id，不可用name替代
- 元素选择机制

## Style guide

- Always specify alt, width, heightfor images.
- Space-less

```html
<link rel="stylesheet" href="styles.css"> good
<link rel = "stylesheet" href = "styles.css"> bad
```

- Never Skip the <title> Element
- Close Empty HTML Elements

```
<meta charset="utf-8" /> better
<meta charset="utf-8">
```

- setting view port
- lowercase file names
- extension: .html .css .js



## URL Encode

Web browsers request pages from web servers by using a URL.

A Uniform Resource Locator (URL) is used to address a document (or other data) on the web.

scheme://prefix.domain:port/path/filename  https://www.w3schools.com/html/default.asp

- **scheme** - defines the **type** of Internet service (most common is **http or https**)
- **prefix** - defines a domain **prefix** (default for http is **www**)
- **domain** - defines the Internet **domain name** (like w3schools.com)
- **port** - defines the **port number** at the host (default for http is **80**)
- **path** - defines a **path** at the server (If omitted: the root directory of the site)
- **filename** - defines the name of a document or resource

URLs can only be sent over the Internet using the [ASCII character-set]. If a URL contains characters outside the ASCII set, the URL has to be converted.
