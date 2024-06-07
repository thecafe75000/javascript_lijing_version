## 一、CSS基础

### 1、什么是CSS？

![01](.\img\01.jpg)

CSS 是层叠样式表 ( Cascading Style Sheets ) 的简称. 有时我们也会称之为 CSS 样式表或级联样式表。

CSS 是也是一种标记语言 CSS 主要用于设置 HTML 页面中的文本内容（字体、大小、对齐方式等）、图片的外形（宽高、边框样式、边距等）以及版面的布局和外观显示样式。 

CSS 让我们的网页更加丰富多彩，布局更加灵活自如。简单理解：CSS 可以美化 HTML , 让HTML更漂亮， 让页面布局更简单。

CSS 最大价值: 由 HTML 专注去做结构呈现，样式交给 CSS，即 结构 ( HTML ) 与样式( CSS ) 相分离。

### 2、CSS的使用方式

#### 2.1 行内样式

+ 写在标签的 `style` 属性中，（又称：内联样式）。


+ 语法：

  ```html
  <h1 style="color:red;font-size:60px;">是谁在敲打我窗</h1>
  ```

+ 注意点：

  > 1. `style` 属性的值不能随便写，写要符合 `CSS` 语法规范，是  `名:值;`  的形式。
  > 2. 行内样式表，只能控制当前标签的样式，对其他标签无效。

- 存在的问题：

  > 书写繁琐、样式不能复用、并且没有体现出：**结构（html）与表现（css）分离** 的思想，不推荐大量使用，只有对当前元素添加简单样式时，才偶尔使用。

#### 2.2 内部样式

+ 写在` html` 页面内部，将所有的 `CSS` 代码提取出来，单独放在 `<style>` 标签中。

+ 语法：

  ```html
  <style>
      h1 {
          color: red;
          font-size: 40px;
      }
  </style>
  ```

+ 注意点：

  > 1. `<style>` 标签理论上可以放在 `HTML` 文档的任何地方，但一般都放在`<head>`标签中。
  > 2. 此种写法：样式可以复用、代码结构清晰。

- 存在的问题：

  > 1. 并没有实现：结构与样式**完全分离**。
  > 2. 多个`HTML`页面无法复用样式。

#### 2.3 外部样式

+ 写在单独的`.css`文件中，随后在 `HTML` 文件中引入使用。

+ 语法：

  1. 新建一个扩展名为 `.css` 的样式文件，把所有` CSS` 代码都放入此文件中。

     ```css
     h1{
         color: red;
         font-size: 40px;
     }
     ```

  2. 在 `HTML` 文件中引入 `.css` 文件。

     ```css
     <link rel="stylesheet" href="./xxx.css">
     ```

+ 注意点：

  > 1. `<link>`标签要写在`<head>`标签中。
  > 2. `<link>`标签属性说明：
  >    - `href`：引入的文档来自于哪里。
  >    - `rel`：(`relation`：关系）说明引入的文档与当前文档之间的关系。
  > 3. 外部样式的优势：样式可以复用、结构清晰、可触发浏览器的缓存机制，提高访问速度 ，实现了**结构与样式的完全分离**。
  > 4. 实际开发中，**几乎都使用外部样式**，这是<font color="red">**最推荐的使用方式！**</font>

#### 2.4、样式表优先级

- 优先级规则：**行内样式** `>` **内部样式** `=` **外部样式**

  > 1. 内部样式、外部样式，这二者的优先级相同，且：后面的 会覆盖 前面的（简记：“后来者居上”）。
  > 2. 同一个样式表中，优先级也和编写顺序有关，且：后面的 会覆盖 前面的（简记：“后来者居上”）。

| 分类     | 优点                                                         | 缺点                                                         | 使用频率                          | 作用范围 |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------- | -------- |
| 行内样式 | <font color="green">**优先级最高**</font>                    | <font color="gray">1. 结构与样式未分离<br>2. 代码结构混乱<br>3. 样式不能复用</font> | 很低                              | 当前标签 |
| 内部样式 | **<font color="green">1. 样式可复用<br>2. 代码结构清晰</font>** | <font color="gray">1. 结构与样式未**彻底**分离<br>2. 样式不能多页面复用</font> | 一般                              | 当前页面 |
| 外部样式 | **<font color="green">1. 样式可多页面复用<br>2. 代码结构清晰<br>3. 可触发浏览器的缓存机制 <br/>4. 结构与样式彻底分离</font>** | <font color="gray">需要引入才能使用</font>                   | <font color="red">**最高**</font> | 多个页面 |

### 3、CSS语法规范

​	使用 HTML 时，需要遵从一定的规范，CSS 也是如此。要想熟练地使用 CSS 对网页进行修饰，首先需要了解CSS 样式规则。

+ CSS 规则由两个主要的部分构成：选择器以及一条或多条声明。
  + 选择器是用于指定 CSS 样式的 HTML标签（现阶段如此）
  + 花括号内是对该对象设置的具体样式
  + 属性和属性值以“键值对”的形式出现
  + 属性是对指定的对象设置的样式属性，例如字体大小、文本颜色等
  + 属性和属性值之间用英文“:”分开 5.多个“键值对”之间用英文“;”进行区分
  + 选择器和{}之间要有一个空格
  + 属性后面的分号也要有一个空格
  + 每一个声明的后面都要添加一个分号，但是最后一个声明可以加也可以不加，但是最好是加

![02](.\img\02.jpg)

​	

```html
选择器{
    属性1:值1;
    属性2:值2;
    属性3:值3;
    ...
    属性n:值n;
}
```

例如： 所有的样式，都包含在 `<style>` 标签内，表示是样式表。`<style>`一般写到`</head>` 上方

```html
<head>
    <style>
        h4 {
            color: blue;
            font-size: 100px;
        }
    </style>
  	<body>
      <h4>
        苍茫的天涯是我的爱
      </h4>
  	</body>
</head>
```

### 4、CSS代码风格

#### 4.1、样式格式书写

+ **紧凑格式**

  ```css
  h3 { color: skyblue;font-size: 20px;}
  ```

+ **展开格式**

  ```css
  h3 {
          color: skyblue;
          font-size: 20px;    
       }
  ```

> 项目上线时，我们会通过工具将【展开风格】的代码，变成【紧凑风格】，这样可以减小文件体积，节约网络流量，同时也能让用户打开网页时速度更快。

#### 4.2、样式大小写书写

+ **小写格式**

  ```css
  h3 {
   	color: skyblue;
  }
  ```

+ **大写格式**

  ```css
  H3 {
   	COLOR: PINK;   
  } 
  ```

> 推荐第一种全部使用小写字母的风格。

### 5、CSS注释

```css
/*注释的内容*/
```

快捷键（与html注释一样）：`ctrl+/`或者`shift+Alt+A`

## 二、CSS选择器

### 1、CSS选择器是什么

CSS选择器是CSS规则的一部分。它是元素和其他部分组合起来告诉浏览器哪个HTML元素应当是被选为应用规则中的CSS属性值的方式。选择器所选择的元素，叫做“选择器的对象”。

```html
<html>
  <head>
  	<style>
      h1{
        color:skyblue;
      }
    </style>
  </head>
  <body>
    <h1>我是CSS选择器</h1>
  </body>
</html>
```

### 2、CSS选择器的作用

选择器(选择符)就是根据不同需求把不同的标签选出来这就是选择器的作用。

简单来说，就是选择标签用的。找到所有的 h1 标签。 选择器（选对人） 设置这些标签的样式，比如颜色为红色（做对事）。

![03](.\img\03.jpg)

### 3、CSS基本选择器(4)

> 基础选择器包括：
>
> 1.标签选择器
>
> 2.ID选择器
>
> 3.类选择器
>
> 4.通配符选择器

#### 3.1、标签选择器

+ 概念：标签选择器（元素选择器）是指用 HTML 标签名称作为选择器，按标签名称分类，为页面中某一类标签指定统一的 CSS 样式。

+ 语法：标签选择器{ 属性：属性值 ... } 

+ 作用：标签选择器（元素选择器）是指用 HTML 标签名称作为选择器，按标签名称分类，为页面中某一类标签指定统一的 CSS 样式。

+ 案例：

  ```css
  div {

   }
  ```

#### 3.2、ID选择器

+ 概念：ID选择器可以为标有特定 id 的 HTML 元素指定特定的样式。 HTML 元素以 id 属性来设置 id 选择器，CSS 中 id 选择器以“#" 来定义。

+ 语法：id名 { 属性1: 属性值1; ... }

+  注意：

  + id 属性只能在每个 HTML 文档中出现一次
  + 起名时要取英文名，不能用关键字：(所有的标记和属性都是关键字)

+ 案例：

  ```css
   #idName {

   }
  ```

#### 3.3、类选择器

+ 概念：如果想要差异化选择不同的标签，单独选一个或者某几个标签，可以使用类选择器。

+ 语法：.类名 { 属性1: 属性值1;... }

+ 注意：

  + 如果想要差异化选择不同的标签，单独选一个或者某几个标签，可以使用类选择器。
  + 类选择器在 HTML 中以 class 属性表示，在 CSS 中，类选择器以一个点“.”号显示。
  + 类选择器使用“.”（英文点号）进行标识，后面紧跟类名（自定义，我们自己命名的）。
  + 不要使用纯数字、中文等命名，尽量使用英文字母来表示。
  + 命名要有意义，尽量使别人一眼就知道这个类名的目的。

+ 分类：

  + 单类名选择器

    ```css
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8" />
            <title>test</title>
            <style>
                .demo{
                    color: aqua;
                }
            </style>
        </head>
        <body>
            <div class="demo">
                传说中你为爱甘心被搁浅
            </div>
        </body>
    </html>
    ```

  + 多类名选择器

    ```css
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8" />
            <title>test</title>
            <style>
                .demo{
                    color: aqua;
                }
    		   .demo1{
                    font-size:90px;
                }
            </style>
        </head>
        <body>
            <div class="demo demo1">
                传说中你为爱甘心被搁浅
            </div>
        </body>
    </html>
    ```

    > 在标签class 属性中写 多个类名 ,多个类名中间必须用空格分开,这个标签就可以分别具有这些类名的样式

#### 3.4、通配符选择器

+ 概念：通配符选择器不需要调用， 自动就给所有的元素使用样式 特殊情况才使用

+ 语法：* {    属性1: 属性值1;      ...}

+ 案例：

  ```css
  /* 选中所有元素 */
  * {
      color: orange;
      font-size: 40px;
  }
  ```

#### 3.5、选择器总结

| 基础选择器  | 作用              | 特点                   | 使用情况      | 用法                   |
| ------ | --------------- | -------------------- | --------- | -------------------- |
| 元素选择器  | 可以选出所有相同的标签，比如p | 不能差异化选择              | 较多        | p{color:skyblue}     |
| 类选择器   | 可以选出1个或者多个标签    | 可以根据需求选择             | 非常多       | .nav{color:skyblue}  |
| ID选择器  | 一次只能选择一个标签      | id属性只能在每个HTML文档中出现一次 | 一般和js一起使用 | \#nav{color:skyblue} |
| 通配符选择器 | 选择所有的标签         | 选择的太多                | 样式初始化使用   | *{color:skyblue}     |

### 4、CSS复合选择器

> 在 CSS 中，可以根据选择器的类型把选择器分为**基础选择器**和**复合选择器**，复合选择器是建立在基础选择器之上，对基本选择器进行组合形成的。 复合选择器是由两个或多个基础选择器，通过不同的方式组合而成的，可以更准确、更高效的选择目标元素（标签） 常用的复合选择器包括：**后代选择器、子元素选择器、交集选择器、并集选择器、属性选择器、伪类选择器、链接伪类选择器**等等

#### 4.1、后代选择器

+ 概念：后代选择器又称为包含选择器，可以选择父元素里面子元素。其写法就是把外层标签写在前面，内层标签写在后面，中间用空格分隔。当标签发生嵌套时，内层标签就成为外层标签的后代

+ 语法：

  ```css
  元素1 元素2{样式声明}
  ```

  > 上述语法表示选择元素 1 里面的所有元素 2 (后代元素)。

+ 语法说明：

  + 元素1 和 元素2 中间用空格隔开
  + 元素1 是父级，元素2 是子级，最终选择的是元素2
  + 元素2 可以是儿子，也可以是孙子等，只要是元素1 的后代即可
  + 元素1 和 元素2 可以是任意基础选择器

+ 案例：

  ![05](.\img\05.jpg)

  ```css
  .cla h3{
    color:red;
  }
  ```


#### 4.2、子代选择器

+ 概念：子元素选择器（子选择器）只能选择作为某元素的最近一级子元素，（简单理解就是选亲儿子元素）

+ 语法：

  ```css
  元素1 > 元素2{样式声明}
  ```

  > 上述语法表示选择元素1 里面的所有直接后代(子元素) 元素2。

+ 语法说明：

  + 元素1 和 元素2 中间用 大于号 隔开
  + 元素1 是父级，元素2 是子级，最终选择的是元素2
  + 元素2 必须是亲儿子，其孙子、重孙之类都不归他管. 你也可以叫他 亲儿子选择器

+ 案例：

  ```css
  div > p{
    color:red;
  }
  选择div里面所有最近一级的p标签
  ```


#### 4.3、交集选择器

+ 概念：交集选择器由两个选择器构成，其中第一个为标签选择器，第二个为class选择器或id选择器，两个选择器之间不能有空格，交集选择器是并且的意思。 即...又...的意思。

+ 语法：

  ```css
  h3.class{color:red font-size:100px;}
  ```

  ![04](.\img\04.jpg)

+ 案例：

  ```css
  p.one {} /* 选择的是： 类名为 .one的段落标签。*/
  p#two {} /* 选择的是： id为two的段落标签。*/
  ```

#### 4.4、并集选择器

+ 概念：并集选择器可以选择多组标签, 同时为他们定义相同的样式，通常用于集体声明。并集选择器是各选择器通过英文逗号（,）连接而成，任何形式的选择器都可以作为并集选择器的一部分。

+ 语法：

  ```css
  元素1，元素2{
    样式声明
  }
  ```

  > 上述语法表示选择元素1 和 元素2。

+ 语法说明：

  + 元素1 和 元素2 中间用逗号隔开
  + 逗号可以理解为和的意思
  + 并集选择器通常用于集体声明

+ 案例：

  ```css
  ul,div{
    样式声明
  }
  选择ul和div标签元素
  ```


#### 4.5、兄弟选择器（2）

+ **`+`选择器**
  
  + 概念：“+”选择器则表示某元素后相邻的兄弟元素，也就是紧挨着的，是单个的
  
+ 案例：
  
  ```html
  <!DOCTYPE html>
  <html lang="en">
  	<head>
      	<meta charset="UTF-8">
      	<title>Document</title>
      	<style>
          	.h3 + p{
              	color: red;
          	}
      	</style>
  	</head>
    	<body>
        <p>起来</p>
        <p>不愿做奴隶的人民</p>
        <p>把我们的血肉筑成我们新的长城</p>
        <h3 class="h3">中华民族到了</h3>
        <p>最危险的时候</p>
        <p>2022</p>
        <p>中国加油</p>
       </body>
  </html>
  ```
  
+ **`~`选择器**

  + 概念：作用是查找某一个指定元素的后面的所有兄弟节点

+ 案例：

  ```html
   <!DOCTYPE html>
      <html lang="en">
      	<head>
          	<meta charset="UTF-8">
          	<title>Document</title>
          	<style>
              	.h3 ~ p{
                  	color: red;
              	}
          	</style>
      	</head>
        	<body>
            <p>起来</p>
            <p>不愿做奴隶的人民</p>
            <p>把我们的血肉筑成我们新的长城</p>
            <h3 class="h3">中华民族到了</h3>
            <p>最危险的时候</p>
            <p>2022</p>
            <p>中国加油</p>
           </body>
      </html>
  ```

#### 4.6、属性选择器（7）

- 作用：选中属性值符合一定要求的元素。

- 语法：

  1. `[属性名]` 选中<font color=blue>**具有**</font>某个属性的元素。
  2. `[属性名="值"]` 选中包含某个属性，且属性值<font color=blue>**等于**</font>指定值的元素。
  3. `[属性名^="值"]` 选中包含某个属性，且属性值以指定的值<font color=blue>**开头**</font>的元素。
  4. `[属性名$="值"]`  选中包含某个属性，且属性值以指定的值<font color=blue>**结尾**</font>的元素。
  5. `[属性名*=“值”]`  选择包含某个属性，属性值<font color=blue>**包含**</font>指定值的元素。
  6. `[属性名~=“值”]`选择具有att属性且属性值用空格分隔的字词列表，其中一个等于val的E元素（包含只有一个值且该值等于val的情况）
  7. `[属性名|=“值”]`选择具有att属性且属性值为以val开头并用连接符"-"分隔的字符串的E元素，如果属性值仅为val，也将被选择。

- 举例：

  ```css
  /* 选中具有title属性的元素 */
  div[title]{color:red;}
  
  /* 选中title属性值为atguigu的元素 */
  div[title="atguigu"]{color:red;}
  
  /* 选中title属性值以a开头的元素 */
  div[title^="a"]{color:red;}
  
  /* 选中title属性值以u结尾的元素 */
  div[title$="u"]{color:red;}
  
  /* 选中title属性值包含g的元素 */
  div[title*="g"]{color:red;}
  ```

#### 4.7、伪类选择器

##### 4.7.1、动态伪类选择器(5)

- `E:link`

  ```css
    设置超链接a在未被访问前的样式。
    a:link{
                  color: greenyellow;
    }
  ```

  注意，a:hover 必须位于 a:link 和 a:visited 之后，a:active 必须位于 a:hover 之后

- `E:visited`

  ```css
    设置超链接a在其链接地址已被访问过时的样式。
    a:visited{
                  color: #ccc;
    }
  ```

- `E:hover`

  ```css
    设置元素在其鼠标悬停时的样式。
    a:hover{
                  color: red;
    }
  ```

- `E:active`

  ```css
    设置元素在被用户激活（在鼠标点击与释放之间发生的事件）时的样式。
    a:active{
                  color: blueviolet;
    }
  ```

- `E:focus`

  ```css
    设置对象在成为输入焦点（该对象的onfocus事件发生）时的样式。
    :focus主要处理的是 获取到焦点之后样式的改变
              注意的将outline要提前设置为none */
     :focus{
           outline: none;
           border: 1px solid hotpink;
    }
  ```

- 案例练习

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        input {
            width: 300px;
            padding: 10px;
            border: 1px solid #ccc;
        }

        :focus {
            outline: none;
            border-color: pink;
        }
    </style>
</head>
<body>
    <input type="text">

    <textarea name="" id="" cols="30" rows="10"></textarea>
</body>
</html>
```

##### 4.7.2、目标伪类选择器

- `E:target`

  ```
    匹配相关URL指向的E元素。
  ```

- 案例练习

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .box {
            margin-top: 60px;
            height: 400px;
            border: 2px dashed red;
            font-size: 200px;
            font-weight: 700;
            text-align: center;
        }
        /* 选择当前地址指向的锚点元素 */
        :target {
            background-color: cyan;
            color: #fff;
        }
    </style>
</head>
<body>
    <div class="box" id="box01">一</div>
    <div class="box" id="box02">二</div>
    <div class="box" id="box03">三</div>
    <div class="box" id="box04">四</div>
    <div class="box" id="box05">五</div>
</body>
</html>
```

##### 4.7.3、语言伪类选择器

- `E:lang `

  ```
    匹配使用特殊语言的E元素
  ```

- 案例练习

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        :lang(en) {
            border: 1px solid red;
        }
    </style>
</head>
<body>
    <ul lang="cn">
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
        <li>Lorem ipsum dolor sit amet.</li>
    </ul>

    <div>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptates consequuntur sed quasi eius sint omnis ex ullam maxime nesciunt magni, nam aut, illum, fuga nostrum labore neque quo quas dolore!
    </div>
</body>
</html>
```

##### 4.7.4、UI元素伪类选择器(3)

- `E:checked`

  ```
    匹配用户界面上处于选中状态的元素E。(用于input type为radio与checkbox时)
  ```
  
- `E:enabled`

  ```
    匹配用户界面上处于可用状态的表单元素
  
  ```

- `E:disabled`

  ```
    匹配用户界面上处于禁用状态的表单元素
  ```

- 案例练习

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        input:checked {
            width: 30px;
            height: 30px;
        }

        :enabled {
            border: 1px solid red;
        }

        :disabled {
            background-color: green;
        }
    </style>
</head>
<body>
    
    <input type="text" disabled>
    <br>
    <input type="radio">100
    <input type="radio">200
    <input type="radio">300
    <br>
    <input type="checkbox" name="" id="">1000
    <input type="checkbox" name="" id="">2000
    <input type="checkbox" name="" id="">3000
    <input type="checkbox" name="" id="">4000
    <br>

    <select name="" id="">
        <option value="">10</option>
        <option value="">20</option>
        <option value="">30</option>
        <option value="">40</option>
    </select>
    <br>
    <button disabled>提交</button>

</body>
</html>
```

##### 4.7.5、结构伪类选择器(12)

- `E:root`

  ```
    匹配E元素在文档的根元素。在HTML中，根元素永远是HTML
  ```

- `E:first-child`

  ```
    匹配父元素的第一个子元素E。
  ```

- `E:last-child`

  ```
    匹配父元素的最后一个子元素E。
  ```

- `E:only-child`

  ```
    匹配父元素仅有的一个子元素E。
  ```

- `E:nth-child(n)`

  ```
    匹配父元素的第n个子元素E，假设该子元素不是E，则选择符无效。
  ```

- `E:nth-last-child(n)`

  ```
    匹配父元素的倒数第n个子元素E，假设该子元素不是E，则选择符无效。
  ```

- `E:first-of-type`

  ```
    匹配同类型中的第一个同级兄弟元素E
  ```

- `E:last-of-type`

  ```
    匹配同类型中的最后一个同级兄弟元素E
  ```

- `E:only-of-type`

  ```
    匹配同类型中的唯一的一个同级兄弟元素E
  ```

- `E:nth-of-type(n)`

  ```
    匹配同类型中的第n个同级兄弟元素E
  ```

- `E:nth-last-of-type(n)`

  ```
    匹配同类型中的倒数第n个同级兄弟元素E
  ```

- `E:empty`

  ```
    匹配没有任何子元素（包括text节点）的元素E
  ```

##### 4.7.6、否定伪类选择器

- `E:not(s)`

  ```
  排除满足括号中选择器条件的元素。 
  ```

#### 4.8、伪元素选择器(6)

+ 概念：伪类选择器（简称：伪类）通过冒号来定义，它定义了元素的状态，如点击按下，点击完成等，通过伪类可以为元素的状态修改样式

  > 到底何为伪类?
  >
  > 就是css内置类css内部本身赋予它一些特性和功能，也就是你不用再class=...或id=...你就可以直接拿来使用，当然你也可以改变它的部分属性比如：a:link{color:red;}

- `E::first-letter`

  ```
  用于给元素中的第一个文字（字母或汉字）设置样式。  设置对象内的第一个字符的样式。
  ```

- `E::first-line`

  ```
  用于给元素中的第一行文字设置样式。
  ```

- `E::before`

  ```
  动态地给元素创建一个子元素,位于最开始的位置，必须设置 content 属性才生效。 
  非常重要。
  ```

- `E::after`

  ```
  动态地给元素创建一个子元素位于最后的位置，必须设置 content 属性才生效。  
  ```

- `E::placeholder`

  ```
  用于给文本输入框或文本域设置 placeholder 文字的样式。 
  ```

- `E::selection`

  ```
  用于设置文本被鼠标选中之后的样式。
  ```

#### 4.9、选择器的优先级（权重）

通过<font color=green>**不同的选择器**</font>，选中<font color=green>**相同的元素**</font> ，并且为<font color=green>**相同的样式名**</font>设置<font color=green>**不同的值**</font>时，就发生了样式的冲突。

到底应用哪个样式，此时就需要看<font color=red>**优先级**</font>了。

- 简单描述：

  > **行内样式 `>` ID选择器 `>` 类选择器 `>` 元素选择器 `>` 通配选择器**。

- 详细描述：

  1. 计算方式：每个选择器，都可计算出一组权重，格式为：**`(a,b,c)`**

     > - **`a`**: **ID** 选择器的个数。
     > - **`b`**: **类、伪类、属性** 选择器的个数。
     > - **`c`**: **元素、伪元素** 选择器的个数。
     >
     > 例如：
     >
     > | 选择器                         | 权重          |
     > | ------------------------------ | ------------- |
     > | **`ul>li`**                    | **`(0,0,2)`** |
     > | **`div ul>li p a span `**      | **`(0,0,6)`** |
     > | **`#atguigu .slogan `**        | **`(1,1,0)`** |
     > | **`#atguigu .slogan a`**       | **`(1,1,1)`** |
     > | **`#atguigu .slogan a:hover`** | **`(1,2,1)`** |

  2. 比较规则：按照<font color=red>**从左到右**</font>的顺序，依次比较大小，当前位胜出后，后面的不再对比，例如：

     > - **`(1,0,0)`** > **`(0,2,2)`**  
     > - **`(1,1,0)`** > **`(1,0,3)`** 
     > - **`(1,1,3)`** > **`(1,1,2)`**

  3. 特殊规则：

     1. **行内样式**权重大于**所有选择器**。
     2. **`!important`**的权重，大于**行内样式**，大于**所有选择器**，**权重最高！**

  4. 图示：

     ![09](.\img\09.png)


#### 4.10、扩展

##### 4.10.1、 first-child

> 1.选中的是div的第一个儿子是p标签的（按照所有兄弟计算的）

```html
div>p:first-child {
            color: red;
        }
        
<div>
        <p>红浪漫</p>
        <p>天上人间</p>
        <p>白马会所</p>
        <p>云水谣</p>
</div>
```

> 2.选中的是div的第一个儿子是p标签（按照所有兄弟计算的）

```html
div>p:first-child {
            color: red;
        }
        
<div>
    	<span>来吧，客官</span>
        <p>红浪漫</p>
        <p>天上人间</p>
        <p>白马会所</p>
        <p>云水谣</p>
</div>
```

> 选中的是div的后代p元素，且不管p的父亲是谁，但是p必须是其父亲的第一个儿子（按照所有兄弟计算的）

```html
div p:first-child {
            color: red;
        }
<div>
        <p>马志强1</p>
        <div>
            <p>马志强2</p>
            <p>马志强3</p>
        </div>
        <p>马志强4</p>
        <p>马志强5</p>
        <p>马志强6</p>
</div>
```

> 选中的是p元素，且不管p的父亲是谁，但p必须是其父亲的第一个儿子（按照所有兄弟计算的）

```html
p:first-child {
            color: red;
        }
<p>马志强0</p>
<div>
        <p>马志强1</p>
        <div>
            <p>马志强2</p>
            <p>马志强3</p>
        </div>
        <p>马志强4</p>
        <p>马志强5</p>
        <p>马志强6</p>
</div>
```

> first-child和last-child一样

##### 4.10.2、nth-child

> 1. `0`或`不写`：什么都选不中 —— 几乎不用。
>
> 2. `n`：选中所有子元素  —— 几乎不用。
>
> 3. `1~正无穷的整数` ：选中对应序号的子元素****
>
> 4. `2n` 或 `even`  ：选中序号为偶数的子元素。
>
> 5. `2n+1` 或 `odd` ：选中序号为奇数的子元素。
>
> 6. `-n+5` ：选中的是前`5`个。

https://flukeout.github.io/

