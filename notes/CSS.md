# CSS

- CSS 指层叠样式表 (**C**ascading **S**tyle **S**heets)
- 样式定义**如何显示** HTML 元素
- 样式通常存储在**样式表**中
- 把样式添加到 HTML 中，是为了**解决内容与表现分离的问题**
- **外部样式表**可以极大提高工作效率
- 外部样式表通常存储在 **CSS 文件**中
- cascading: inline>internal>external;  different styles at the same level, last wins

# CSS Syntax 语法

CSS 规则由两个主要的部分构成：selector选择器，以及一条或多条声明 declaration:

![img](https://www.runoob.com/wp-content/uploads/2013/07/632877C9-2462-41D6-BD0E-F7317E4C42AC.jpg)

The declaration block contains one or more declarations separated by semicolons.

Each declaration includes a CSS **property** name and a **value**, separated by a colon.

```css
p
{
    color:red;
    text-align:center;
}
/*这是个注释*/
/*为了让CSS可读性更强，你可以每行只描述一个属性*/
```

# CSS Selectors

- Simple selectors (select elements based on n**ame, id, class**)
- [Combinator selectors] (select **elements based on a specific relationship** between them)
- [Pseudo-class selectors] (select **elements based on a certain state**)
- [Pseudo-elements selectors] (select and style **a part of an element**)
- [Attribute selectors] select elements **based on an attribute or attribute value**

## Simple selectors

ID: HTML元素以id属性来设置id选择器,CSS 中 id 选择器以 "#" 来定义。

CLASS: class 选择器在HTML中以class属性表示, 在 CSS 中，类选择器以一个点"."号显示：

- ID属性和类名不要以数字开头，数字开头的ID在 Mozilla/Firefox 浏览器中不起作用。
- 一个element 可以使用多个class < p class="center large">
- You can also specify that only specific HTML elements should be affected by a class: p.center{}

```css
<head>
<style>

#para1
{
	text-align:center;
} 

.center
{
	text-align:center;
}

p.center {
  text-align: center;
  color: red;
}
p.large {
  font-size: 300%;
}

</style>
</head>

<body>
<h1 class="center">标题居中</h1>
<p class="center">段落居中,红色。</p> 
<p id="para1">center paragraph</p>
<p class="center large">This paragraph will be red, center-aligned, and in a large font-size.</p> 
</body>
```

Universal selector: The universal selector (*) selects all HTML elements on the page.

Grouping selector: The grouping selector selects all the HTML elements with the same style definitions.

```css
* {
  text-align: center;
  color: blue;
}

h1, h2, p {
  text-align: center;
  color: red;
}
```

## Combinators Selector

- **descendant selector (space)** The descendant selector matches all elements that are descendants of a specified element.

- **child selector (>)**The child selector selects all elements that are the **children** of a specified element.

- **adjacent sibling selector (+) **select an element that is **directly after** another specific element.

- **general sibling selector (~)**all elements that are next siblings of a specified element.

  ```html
  <head>
  <style>
  div p {
    background-color: yellow;
  }
  div > p {
    background-color: green;
  }
  div ~ p {
    background-color: blue;
  }
  div + p {
    background-color: red;
  }
  </style>
  </head>
  <body>
  <div>
    <p>Paragraph 1 in the div. green</p>
     <!-- div p and div>p both are met, the later one wins -->
    <p>Paragraph 2 in the div. green</p>
    <section><p>Paragraph 3 in the div. yellow</p></section>
  </div>
  <p>Paragraph 3. After a div. red div ~ p and div +p both are met.</p>
  <p>Paragraph 4. After a div. blue </p>
  <h2>A Heading</h2>
  <p>Paragraph 5. After a div. blue </p>
  <p>Paragraph 6. After a div. blue </p>
  
  
  </body>
  ```

  

## Pseudo-class selectors

A pseudo-class is used to define a special **state** of an element. use colon `:`

- Anchor Pseudo-classes

**Note:** a:hover MUST come after a:link and a:visited in the CSS definition in order to be effective.

**Note:** a:active MUST come after a:hover in the CSS definition in order to be effective.

```html
<style>
/* unvisited link */
a:link {
  color: red;
}

/* visited link */
a:visited {
  color: green;
}

/* mouse over link */
a:hover {
  color: hotpink;
}

/* selected link */
a:active {
  color: blue;
}
</style>
```

Combine Anchor Pseudo-classes and combinator selector:

```html
<head>
<style>
p {
  display: none;
  background-color: yellow;
  padding: 20px;
}

div:hover p {
  display: block;
}
</style>
</head>
<body>

<div>Hover over this div element to show the p element
  <p>Tada! Here I am!</p>
</div>

</body>
```

- The :first-child Pseudo-class

  - a specified element that is the first child of **any** **other type** element.`element: first-child`

  - `p i:first-child` the first-child  i element in all **specific** elements
  - Match all <i> elements in all first-child <p> elements `p:first-child i`

```html
<head>
<style>
p:first-child {
  color: blue;
} 
p i:first-child {
  color: red;
} 
</style>
</head>
<body>

<p>This is some text. blue</p>
<p>This is some text.</p>

<div>
  <p>This is some text.blue</p>
  <p>This is some text.</p>
</div>

<p>I am a <i>strong red</i> person. I am a <i>strong no style</i> person.</p>
<p>I am a <i>strong red</i> person. I am a <code> <i>strong red</i> </code> person.</p>

</body>
```

Pseudo-class selectors with parameter: `selector:state(value)` e.g. `p:nth-child(2)` `:not(p)` 

## Pseudo-elements selectors

A CSS pseudo-element is used to style specified parts of an element. `element::pseudo-element`

e.g. `p::first-line` `p::first-letter` `p::selection`

`element::before`and`elemtment::after` is used to add content before or after a specific element.

```
h1::before {
  content: url(smiley.gif);
}
```

以上pseudo-element 如果省略::之前的element，就应用到整个页面。 ::marker 本身就是单独使用，如果要指定某个列表的marker，要`ul ::marker`既ul的descendant marker

## Attribute selectors

The `[attribute]` selector is used to select elements with a specified attribute. e.g. `a[target]`

The `[attribute="value"]` selector is used to select elements with a specified attribute and value.  e.g.`a[target="_blank"]`

The `[attribute~="value"]` selector is used to select elements with an attribute value **containing a specified word**. `a[title~="flower"]` The example above will match elements with title="flower", title="summer flower", and title="flower new", but not title="my-flower" or title="flowers", cuz they are not **space-separated**.

The `[attribute|="value"]` selector is used to select elements with the specified attribute, whose value can be **exactly the specified value, or the specified value followed by a hyphen (-)**. e.g. `a[class="top"]` The value has to be a whole word, either alone, like class="top", or followed by a hyphen( - ), like class="top-text".

The `[attribute^="value"]` selector is used to select elements with the specified attribute, whose value **starts with** the specified value. `[class^="top"]`  class="top" class="top-a" class="topa" class="top a"

The `[attribute$="value"]` selector is used to select elements whose attribute value **ends with** a specified value.

The `[attribute*="value"]` selector is used to select elements whose attribute value contains a specified value. any position including start and end.

## Selector Priority

插入样式表的方法有三种:

- 外部样式表(External style sheet)

使用 < link> 标签链接到样式表。样式表应该以 .css 扩展名进行保存。 < link> 标签在（文档的）头部：

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

- 内部样式表(Internal style sheet)

  当单个文档需要特殊的样式时，就应该使用内部样式表。使用 <style> 标签在文档头部定义内部样式表

- 内联样式(Inline style)

  在相关的标签内使用样式（style）属性。Style 属性可以包含任何 CSS 属性。

- 如果某元素的某样式属性被多重定义，按照优先级，一般 inline>internal=external>browser

- internal and external sheet can contain multiple style for one element, the result depends on selector priority.  **id> class, attribute selector, pseudo class>type, pseudo element**, * and combinators doesn't effect priority. **Equal specificity: the latest rule wins**

# CSS Comments

```css
/* This is a single-line comment */

/* This is
a multi-line
comment */
```

use css comment, not html comment inside < style> in the head of html.

# ---------------------

# CSS Colors

- RGB:In CSS, a color can be specified as an RGB value, using this formula: rgb(*red,* *green*, *blue*)
- HEX: A hexadecimal color is specified with: #RRGGBB, where the RR (red), GG (green) and BB (blue) hexadecimal integers specify the components of the color.
- HSL: In CSS, a color can be specified using hue, saturation, and lightness (HSL) in the form: hsl(*hue*, *saturation*, *lightness*) 色相 饱和度 亮度
- 渐变色 Gradient.

  - Linear Gradient: linear-gradient(*direction*, *color-stop1*, *color-stop2, ...*);

  - Radial Gradient: radial-gradient(*shape size* at *position, start-color, ..., last-color*);

  - Conic Gradient: conic-gradient([from *angle*] [at *position*,] *color* [*degree*]*, color* [*degree*]*, ...*);

  - ```
    background-image: linear-gradient(to bottom right, red, yellow);
    background-image: linear-gradient(180deg, red, yellow);
    radial-gradient(closest-side at 60% 55%, red, yellow, black);
    background-image: conic-gradient(from 90deg, red, yellow, green);
    ```

  - 


# Property Summary

line width cannot use x% e.g. border outline. Size of an area can use n% e,g, background margin padding height width.



| Property                                                     | Value                                                        | comments                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| color                                                        | tomato; rgb(255, 99, 71); #ff6347, hsl(9, 100%, 64%); rgba(255, 99, 71, 0.5)(transparent50%);  hsla(9, 100%, 64%, 0.5); | name,rgb,hex,hsl,.                                           |
| **Background**                                               |                                                              |                                                              |
| background-color                                             | 同上                                                         | 同上                                                         |
| background-image                                             | url("paper.gif"), can have multiple value                    |                                                              |
| background-repeat                                            | no-repeat; repeat-x; repeat-y                                | By default, the image is repeated                            |
| background-attachment                                        | fixed; scroll                                                |                                                              |
| background-position                                          | left\|right\|center  top\|bpttom\|center; x% y%; xpos ypos;  | specifies whether the background image should scroll or be fixed |
| background                                                   | `body { background: #ffffff url("img_tree.png") no-repeat right top;}` | write in order: b-color b-image b-repeat b-attachement b-position, can skip some hs |
| background-size                                              | x% y%                                                        |                                                              |
| opacity                                                      |                                                              | background transparency                                      |
| **Border**                                                   |                                                              | if one value is set, same for four side; if two value set, bottom=top, left=right; |
| border-style                                                 | dotted dashed solid double groove ridge inset outset none hidden | have from one to four values (for the top border, right border, bottom border, and the left border) |
| border-width                                                 | can be set as a specific size (in px, pt, cm, em, etc), or by using  pre-defined values: thin; medium; or thick | have one to four values (for the top border, right border, bottom border, and the left border): |
| border-color                                                 | 选择同color can have one to four value                       |                                                              |
| border-top\|right\|bottom\|left-style\|width\|color          |                                                              | set style for only one side, does not affect other sides     |
| border                                                       | border: 5px solid red;border-left: 6px solid red;            | shorthand inorder:   `border-width` `border-style` (required) `border-color`, can have **only one value** for each property |
| border-radius: 5px;                                          | border-radius: 5px;                                          | rounded boder, can have 1-4 values                           |
| **Margin**,out of border                                     | margin-top=auto;(or inherit; npx; **n%**;)                   | the adjacent margins keep only the largest one.              |
| margin-top\|bottom\|left\|right                              |                                                              |                                                              |
| margin                                                       | margin: 25px 50px 75px 100px;                                | have one to four value.                                      |
| **Padding**, indise border                                   |                                                              |                                                              |
| padding-top\|bottom\|right\|left                             | padding-top: inherit;(or npx; **n%**;)                       |                                                              |
| padding                                                      | padding: 25px 50px 75px 10%;                                 | have one to four value.                                      |
| box-sizing                                                   | \* {<br/> box-sizing: border-box;<br/>}By default            | By default,width + padding + border = actual width of an element. `box-sizing` property allows us to include the padding and border in an element's total width and height. |
| **Height, Width and Max-width**                              |                                                              | The height and width properties do not include padding, borders, or margins. It sets the height/width of the area inside the padding, border, and margin of the element. |
| height` and `width                                           | auto; 5px; 10%; initial; inherit                             | when wigth is set, batter set margin:auto. then the remain space will be separated sma efor two side. |
| max-width                                                    | 5px; 10%                                                     | change when broswer get smaller,                             |
| **Box model: content padding border margin. from the inside out.** |                                                              | box-sizing decide the for which the width property is styling |
| box-shadow                                                   | box-shadow: 5px 10px lightblue;                              | 挨着border外 不属于box model 可以被outline挡住               |
| **Outline**                                                  |                                                              | a line drawn outside the element's border. does not affect the position of element, could cover other element. 不属于box model 不影响元素位置 |
| outline-style                                                | dotted dashed solid double groove ridge inset outset none hidden | have from one to four values                                 |
| outline-width                                                | a specific size (in px; pt; cm; em; etc); or  pre-defined values: thin; medium; or thick | have one to four values                                      |
| outline-color                                                | 选择同color can have one to four value                       |                                                              |
| outline                                                      | outline: 5px solid yellow;                                   | shorthand in order:   `outline-width` `outline-style` (required) `outline-color` |
| outline-offset                                               | outline-offset: 15px;                                        | space between an element/border and its outline, it is transparent. |
| **Text**                                                     |                                                              |                                                              |
| color and background-color                                   |                                                              |                                                              |
| text-align                                                   | left ，right ; centered; or justified(两边对齐)              |                                                              |
| text-align-last                                              | 同上                                                         | 队后一行对齐方式                                             |
| direction                                                    | ltr; rtl                                                     |                                                              |
| vertical-align                                               | .b {  vertical-align: text-top;}   < p >An< code class="b">aaa< /code> text-top alignment.< /p> | sets the vertical alignment of an element  option: baseline;text-top;text-bottom;sub;super |
| text-decoration-line                                         | overline;line-through;underline                              | Specifies the kind of text decoration to be used, canhave multiple value. |
| text-decoration-color                                        | 同color, only one value                                      | Specifies the color of the text-decoration, can have more than one value. |
| text-decoration-style                                        | 同border-style, only one value                               | Specifies the style of the text decoration                   |
| text-decoration-thickness                                    | 5px; 10%; auto                                               | Specifies the thickness of the text decoration line          |
| text-decoration                                              | text-decoration: underline red double 5px;                   | `text-decoration-line` (required) `text-decoration-color` (optional) `text-decoration-style` (optional) `text-decoration-thickness` (optional) |
| text-transform                                               | uppercase;lowercase;capitalize                               |                                                              |
| letter-spacing                                               | npx                                                          | space between characters                                     |
| line-height                                                  | n                                                            | Specifies the **line height**                                |
| text-indent                                                  | npx                                                          | Specifies the **indentation of the first line** in a text-block |
| white-space                                                  | nowrap                                                       | Specifies how to **handle white-space** inside an element    |
| word-spacing                                                 | npx                                                          | Specifies the **space between words** in a text              |
| text-shadow                                                  | text-shadow: 2px 2px 5px red;                                | horizontal shadow ,vertical shadow,effect, color 可叠加 效果由内到外 |
| **Fonts**                                                    |                                                              |                                                              |
| font-family                                                  | font-family: "Times New Roman", Times, serif;                | should hold several font names as a **"fallback" system**, to ensure maximum compatibility between browsers/operating systems, Start with the font you want, and end with a generic family. More commonly used font fallback in W3school. |
| font-style                                                   | normal;italic;                                               |                                                              |
| font-weight                                                  | normal;bold;                                                 |                                                              |
| font-variant                                                 | normal;small-caps;                                           |                                                              |
| font-size                                                    | 10px;10em;10vw;100%;                                         |                                                              |
| font                                                         | font: italic small-caps bold 12px/30px Georgia, serif;       | style variant weight weight size (required) family (required). |
|                                                              |                                                              |                                                              |
| **Style for list**                                           |                                                              |                                                              |
| list-style-type                                              | circle;square;upper-roman;lower-alpha;none(no marker);       |                                                              |
| list-style-position                                          | outside;inside;                                              |                                                              |
| list-style-image                                             | list-style-image: url('sqpurple.gif');                       |                                                              |
| list-style                                                   | list-style: square inside url("sqpurple.gif");               | shorthand, style position image                              |
| **Style for table**                                          |                                                              |                                                              |
| border-collapse;                                             | table, td, th {  border: 1px solid;}table {    border-collapse: collapse;} |                                                              |
| background-color                                             | tr:nth-child(even) {background-color: #f2f2f2;}tr:hover {background-color: coral;} |                                                              |
| overflow-x                                                   | < div style="overflow-x:auto;">< table>< table>< div>        | Add a container element (like <div>) with `overflow-x:auto` around the <table> element to make it responsive |
| **Object-**                                                  |                                                              |                                                              |
| object-fit                                                   | cover;fill;none;contain;scale-down;                          | specify how an <img> or <video> should be resized to fit its container， these value also used for property: background-size when the background is a picture. |
| objext-position                                              | n% n%;                                                       | ow an <img> or <video> should be positioned within its container. |
|                                                              |                                                              |                                                              |

- Above are style propertys, they could be used with element!! they are not element!!
- Shorthand style can have one value for each style property.

# CSS Layout Property

| display                  | none;block;inline;inline-block                               | 'none' does not take up space;inline -block is comba of inline and block, it does not break line but have height, width, padding ,margin on top and bottom |
| ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| visibility               | visible;hidden                                               | 'hidden' take up sapce                                       |
| position                 | static;relative;fixed;absolute;sticky;                       | must before top right .....<br>`static;` is not positioned in any special way;<br>`relative;` is positioned relative to its normal position.<br> **take up its normal space, but could cover other elements.**`fixed;` is positioned relative to the viewport, always stays in the same place, **does not takeup space** <br>`absolute;` is positioned relative to the nearest positioned ancestor **does not takeup space**<br> |
| top\|right\|bottom\|left | npx;                                                         | used after 'position'                                        |
| z-index                  | -1,1;2;3;.....1 is the bottom                                | When elements are positioned, they can overlap other elements. The `z-index` property specifies the stack order of an element. only works on positioned elements and display:flex elements. |
| overflow                 | visible (default, show the content even if it exceed the area);hidden;scroll;auto; | whether to clip the content or to add scrollbars when the content of an element is too big to fit in the **specified area**. |
| float                    | left; right;none;inherit;                                    |                                                              |
| clear                    | left; right;both;none;inherit;                               | float使元素 taken out of the flow of the page，后续块级元素会假装其不存在，在同一行开始排版，但其中内容不会覆盖float元素。clear使后续元素跳过之前的float的空间，按正常layout |

**The Great Collapse**

One of the more bewildering things about working with **floats is how they can affect the element that contains them (their “parent” element).** If this parent element contained nothing but floated elements, the **height of it would literally collapse to nothing.** Collapsing almost always needs to be dealt with to prevent strange layout and cross-browser problems. We fix it by **clearing the float** **after** the floated elements in the container but **before** the close of the container.

# Multiple Columns

to divide a <div> to multiple columns.

```
.newspaper {
  column-count: 3;
  column-gap: 40px;
  column-rule: 1px solid lightblue;
}
<div class="newspaper">
Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad mi</div>

```

# **CSS Resizing**

specifies if (and how) an element should be resizable by the user.

resize: horizontal;vertical;none;both;

# Media Query

```
@media not|only mediatype and (expressions) {
  CSS-Code;
}

<link rel="stylesheet" media="mediatype and|not|only (expressions)" href="print.css">

e.g.
 @media screen and (max-width:400px) and (orientation:landscape){
 }
 
 mediatype: all;print;screen;speech;
```

# Flexbox

| first define a flex container and add element inside the container |                                                        |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------------ |
| display                                                      | flex;                                                  |                                                              |
| flex-direction                                               | column;column-reverse;row;row-reverse;                 |                                                              |
| flex-wrap                                                    | wrap;nowrap;wrap-reverse;                              |                                                              |
| flex-flow                                                    | flex-flow: row wrap;                                   | `flex-flow` property is a shorthand property for setting both the `flex-direction` and `flex-wrap` properties. |
| justify-content                                              | center;flex-start;flex-end;space-around;space-between; |                                                              |
| align-items                                                  | center;flex-start;flex-end;stretch;                    | vertical align                                               |
| **property for flex items inside the container**             |                                                        |                                                              |
| order                                                        |                                                        |                                                              |
| flex-grow                                                    | n;                                                     | how much a flex item will grow relative to the rest of the flex items. |
| flex                                                         |                                                        | shorthand property for the flex-grow, flex-shrink, and the flex-basis properties |
| align-self:                                                  | center;flex-start;flex-end;stretch;                    | override align-items for specific items                      |
|                                                              |                                                        |                                                              |
|                                                              |                                                        |                                                              |
|                                                              |                                                        |                                                              |

# ---------------------

# Transforms

**2D**

- transform: translate(50px, 100px);
- transform: rotate(20deg);
- transform: scale(2, 3);
- transform: scaleY(3);
- transform: skewX(20deg);skews an element along the X-axis by the given angle.
- transform: skewY(20deg);
- transform: skew(20deg);
- transform: matrix(1, -0.3, 0, 1, 0, 0);matrix(scaleX(), skewY(), skewX(), scaleY(), translateX(), translateY())

```html
div {
  width: 300px;
  height: 100px;
  background-color: yellow;
  border: 1px solid black;
}

div:hover {
  transform: matrix(1, -0.3, 0, 1, 0, 0);
}
```

**3D**

transform: rotateX(150deg);

transform: rotateY(150deg);

transform: rotateZ(90deg);

# Transitions

- `transition` shorthand for transition property, transition duration, timeimgfunction, delay.

  ```html
  div {
    width: 100px;
    height: 100px;
    background: red;
    transition: width 2s, height 4s; transform 2s;
  }
  
  div:hover {
    width: 300px;
    height: 300px;
    transform: rotate(180deg);
  }
  ```

- `transition-delay`

- `transition-duration` required!

- `transition-property`required!

- `transition-timing-function`

```html
The transition-delay property specifies a delay (in seconds) for the transition effect.The following example has a 1 second delay before starting:
div{ transition-delay: 1s;}

The transition-timing-function property specifies the speed curve of the transition effect.
#div1 {transition-timing-function: linear;}
#div2 {transition-timing-function: ease;}
#div3 {transition-timing-function: ease-in;}
#div4 {transition-timing-function: ease-out;}
#div5 {transition-timing-function: ease-in-out;}
```

# **Animation**

- `@keyframes`required
- `animation-name`required
- `animation-duration`required

```
<style> 
@keyframes example1 {
  from {background-color: red;}
  to {background-color: yellow;}
}

@keyframes example2 {
  0%   {background-color:red; left:0px; top:0px;}
  25%  {background-color:yellow; left:200px; top:0px;}
  50%  {background-color:blue; left:200px; top:200px;}
  75%  {background-color:green; left:0px; top:200px;}
  100% {background-color:red; left:0px; top:0px;}
}

/* The element to apply the animation to */
div {
  width: 100px;
  height: 100px;
  background-color: red;
  position: relative; must be defiened before top, left etc. cannot be static.
  animation-name: example1;
  animation-duration: 4s;
  animation-delay:2s;
  animation-direction:normal;
  animation-iterate-count:3;
  animation-timing-sunction:linear
  animation-fill-mode:both;
}
</style> 
```

- `animation-timing-function` 同transitions;
- `animation-delay`:ns
- `animation-iteration-count`:n;ifinite;
- `animation-direction`:normal;reverse;alternate;alternate-reverse;
- `animation-fill-mode` specifies a style for the target element when the animation is not playing (before it starts, after it ends, or both).: forwards;backwards;none;
- `animation`animation: example 5s linear 2s infinite alternate;

# --------------------

# **Navigation Bar**

1. create a list with, each li element contain a < a> element.
2. style a display:block;text-decoration: none;
3. style ul list-style-type: none; position: fixed; overflow: auto;
4. set background color for hover link
5. for hironzontal bar, make li display:inline or float:left



# **Dropdowns**

1. define a dropdown div with defined position, define its childern: fropdown content, whose position is relative to dropdown, so it never take up space.
2. display dropdown content as block with z-index:1 when mouse over dropdown button.

```html
<style>

.dropdown {
  position: relative;
}

.dropdown-content {
  display: none;
  position: absolute;
  z-index: 1;
}

.dropdown-content a {
  display: block;
}

.dropdown-content a:hover {background-color: #f1f1f1}

.dropdown:hover .dropdown-content {
  display: block;
}

.dropdown:hover .dropbtn {
  background-color: #3e8e41;
}
</style>

<div class="dropdown">
  <button class="dropbtn">Dropdown</button>
  <div class="dropdown-content">
  <a href="#">Link 1</a>
  <a href="#">Link 2</a>
  <a href="#">Link 3</a>
  </div>
</div>

```

# Counter

count a type of element and help shows the order.

counter-reset: counter;

counter-increment:counter;

content: counter(counter);

```html
<style>
body {
  counter-reset: section;
}

h1 {
  counter-reset: subsection;
}

h1::before {
  counter-increment: section;
  content: "Section " counter(section) ". ";
}

h2::before {
  counter-increment: subsection;
  content: counter(section) "." counter(subsection) " ";
}
</style>
```

# Math Function

calc(100% - 100px)

max()

min()

```html
#div1 {
  background-color: yellow;
  height: 100px;
  width: min(50%, 300px);
}
```

# Masking

Most browsers only have partial support for CSS masking. You will need to use the -webkit- prefix in addition to the standard property in most browsers.

The mask layer image can be a PNG image, an SVG image, a CSS gradient, or an SVG  element.

```
<style>
.mask1 {
  -webkit-mask-image: url(w3logo.png);
  mask-image: url(w3logo.png);
  -webkit-mask-repeat: no-repeat;
  mask-repeat: no-repeat;    
}

.mask1 {
  -webkit-mask-image: linear-gradient(black, transparent);
  mask-image: linear-gradient(black, transparent);
}

</style>

<div class="mask1">
<img src="img_5terre.jpg" alt="Cinque Terre" width="600" height="400">
</div>
```

# -----------------------

# CSS Responsive

## Grid view

A responsive grid-view often has 12 columns, and has a total width of 100%.

1. First ensure that all HTML elements have the property box-sizing set to border-box.

```
* {
  box-sizing: border-box;
}
```

2. Then we make one class for each of the 12 columns, and a number defining how many columns the section should span:`class="col-"`

```
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
.col-3 {width: 25%;}
.col-4 {width: 33.33%;}
.col-5 {width: 41.66%;}
.col-6 {width: 50%;}
.col-7 {width: 58.33%;}
.col-8 {width: 66.66%;}
.col-9 {width: 75%;}
.col-10 {width: 83.33%;}
.col-11 {width: 91.66%;}
.col-12 {width: 100%;}
```

3. All these columns should be floating to the left

```
[class*="col-"] {
  float: left;
  padding: 15px;
  border: 1px solid red;
}
```

4.  Each row should be wrapped in a `<div>`. The number of columns inside a row should always add up to 12:

```
<div class="row">
  <div class="col-3">...</div> <!-- 25% -->
  <div class="col-9">...</div> <!-- 75% -->
</div>
```

5. Add a style that clears the flow:

```
.row::after {
  content: "";
  clear: both;
  display: table;
}
```

## Media Query

1. Mobile First means designing for mobile before designing for desktop or any other device.

```
[class*="col-"] {
  width: 100%;
}

```

2. Then add breaks for other device. two set of col- properties for teo breaks.

```
@media only screen and (min-width: 600px) {
  /* For tablets: */
  .col-s-1 {width: 8.33%;}
  .col-s-2 {width: 16.66%;}
  .col-s-3 {width: 25%;}
  .col-s-4 {width: 33.33%;}
  .col-s-5 {width: 41.66%;}
  .col-s-6 {width: 50%;}
  .col-s-7 {width: 58.33%;}
  .col-s-8 {width: 66.66%;}
  .col-s-9 {width: 75%;}
  .col-s-10 {width: 83.33%;}
  .col-s-11 {width: 91.66%;}
  .col-s-12 {width: 100%;}
}

@media only screen and (min-width: 768px) {
  /* For desktop: */
  .col-1 {width: 8.33%;}
  .col-2 {width: 16.66%;}
  .col-3 {width: 25%;}
  .col-4 {width: 33.33%;}
  .col-5 {width: 41.66%;}
  .col-6 {width: 50%;}
  .col-7 {width: 58.33%;}
  .col-8 {width: 66.66%;}
  .col-9 {width: 75%;}
  .col-10 {width: 83.33%;}
  .col-11 {width: 91.66%;}
  .col-12 {width: 100%;}
}

<div class="row">
  <div class="col-3 col-s-3 menu">
    <ul>
      <li>The Flight</li>
      <li>The City</li>
      <li>The Island</li>
      <li>The Food</li>
    </ul>
  </div>

  <div class="col-6 col-s-9">
    <h1>The City</h1>
    <p>Chania is the capital of the Chania region on the island of Crete. The city can be divided in two parts, the old town and the modern city.</p>
  </div>

  <div class="col-3 col-s-12">
    <div class="aside">
      <h2>What?</h2>
      <p>Chania is a city on the island of Crete.</p>
      <h2>Where?</h2>
      <p>Crete is a Greek island in the Mediterranean Sea.</p>
      <h2>How?</h2>
      <p>You can reach Chania airport from all over Europe.</p>
    </div>
  </div>
</div>
```

**3.Typical Device Breakpoints**

```
/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 600px) {...}

/* Small devices (portrait tablets and large phones, 600px and up) */
@media only screen and (min-width: 600px) {...}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {...}

/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {...}

/* Extra large devices (large laptops and desktops, 1200px and up) */
@media only screen and (min-width: 1200px) {...}
```

# -----------------------

# SASS

**S**yntactically **A**wesome **S**tyle**s**heet

supports inline comments :`/* comment */` `// comment`

 ".scss" file extension.  A browser does not understand Sass code. Therefore, you will need a Sass pre-processor to convert Sass code into standard CSS. This process is called transpiling. So, you need to give a transpiler (some kind of program) some Sass code and then get some CSS code back.

SASS variables:

```
$myColor: red;
p {
  color: $myColor;
}
```

SASS can nest selectors and properties.

```scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
}


font: {
  family: Helvetica, sans-serif;
  size: 18px;
  weight: bold;
}
```

The `@import` directive allows you to include the content of one file in another.The CSS `@import` directive has a major drawback due to performance issues; it creates an extra HTTP request each time you call it. However, the Sass `@import` directive includes the file in the CSS; so no extra HTTP call is required at runtime!

```scss
@import filename; //do not need to specify a file extension

@import "variables";
@import "colors";
@import "reset";
```

The `@mixin` directive lets you create CSS code that is to be reused throughout the website.

The `@include` directive is created to let you use (include) the mixin.

```scss
@mixin important-text {
  color: red;
  font-size: 25px;
  font-weight: bold;
  border: 1px solid blue;
}

.danger {
  @include important-text;
  background-color: green;
}

// passing parameters
@mixin bordered($color, $width) {
  border: $width solid $color;
}
.myArticle {
  @include bordered(blue, 1px);  // Call mixin with two values
}

//define default values for mixin variables:
@mixin bordered($color: blue, $width: 1px) {
  border: $width solid $color;
}
.myTips {
  @include bordered($color: orange);
}
```

The `@extend` directive lets you share a set of CSS properties from one selector to another.

```scss
.button-basic  {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}

.button-report  {
  @extend .button-basic;
  background-color: red;
}

```



# -----------------------

# Notes

## Variables

1.define a variable: --blue: #1e90ff;

2.use a variable:background-color: var(--blue);

- Global variables can be accessed/used through the entire document, while local variables can be used only inside the selector where it is declared. To create a variable with global scope, declare it inside the `:root` selector. The `:root` selector matches the document's root element.

:root {
 --blue: #1e90ff;
 --white: #ffffff;
}

- local variable override global variable.
- variablevalue can be change in media query.



**Icon**  link to icon resource that google, boostarp, font awesome provides, then include icon inside inline element. <span> <i>
