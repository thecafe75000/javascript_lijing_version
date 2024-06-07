+ CSS书写位置
+ CSS选择器

## 一、CSS三大特性

### 1、层叠性

+ 概念：当样式发生冲突时，需要确定样式声明的最终值，既要考虑样式的来源又要考虑优先级、以及先后顺序 ，这个过程就叫做层叠

+ 层叠性原则:样式冲突，遵循的原则是就近原则，哪个样式离结构近，就执行哪个样式

+ 代码：

  **index.css**

```css
#atguigu {
    color: red;
}
```

​		**html**

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>CSS层叠性</title>
    <link rel="stylesheet" href="./index.css">
    <style>
        h2 {
            color: green;
        }
        h2 {
            color: gray;
        }
    </style>
</head>
<body>
    <h2 id="atguigu">尚硅谷</h2>
</body>
</html>
```

### 2、继承性

- 概念：元素会自动拥有<font color=blue>**其父元素**</font>、或<font color=blue>**其祖先元素**</font>上所设置的<font color=red>**某些样式**</font>。
- 规则：优先继承<font color=blue>**离得近**</font>的，如果自己有 那么就使用自己的。
- 代码：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>CSS继承性</title>
    <link rel="stylesheet" href="./index.css">
    <style>
        div {
            color: red;
            font-size: 40px;
            background-color: skyblue;
        }
        p {
            color: purple;
            background-color: yellowgreen;
        }
    </style>
</head>
<body>
    <div>
        红浪漫div
        <span>红浪漫span1</span>
        <span>红浪漫span2</span>
        <span>红浪漫span3</span>
        <p>
            <span>红浪漫span4</span>
        </p>
    </div>
</body>
</html>
```

> 子元素可以继承父元素的样式：（text-，font-，line-这些元素开头的可以继承，以及color属性）
>
> 备注：参照<a href="https://developer.mozilla.org/zh-CN/">MDN</a>网站，可查询属性是否可被继承。

### 3、优先级

- 简单聊：**`!important` `>` 行内样式 `>` ID选择器 `>` 类选择器 `>` 元素选择器 `>` * `>` 继承的样式。**

- 详细聊：需要计算权重。

  > 计算权重时需要注意：<font color=red>**并集选择器的每一个部分是分开算的！**</font>

+ 代码：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>CSS层叠性</title>
    <link rel="stylesheet" href="./index.css">
    <style>
        h2 {
            color: green;
        }
        div {
            color: red;
            font-size: 40px;
            background-color: skyblue;
        }
        p {
            color: purple;
            background-color: yellowgreen;
        }
        * {
            color: gray;
        }
    </style>
</head>
<body>
    <h2 id="atguigu">尚硅谷</h2>
    <hr>
    <div>
        红浪漫div
        <span>红浪漫span1</span>
        <span>红浪漫span2</span>
        <span>红浪漫span3</span>
        <p>
            <span>红浪漫span4</span>
        </p>
    </div>
</body>
</html>
```

## 二、颜色属性

### 1、像素的概念

- 概念：我们的电脑屏幕是，是由一个一个“小点”组成的，每个“小点”，就是一个像素（px）。

- 规律：像素点越小，呈现的内容就越清晰、越细腻。

  ![01](.\img\01.png)

  > 注意点：如果电脑设置中开启了缩放，那么就会影响一些工具的测量结果，但这无所谓，因为我们设计稿，去给元素设置宽高。

### 2、表示方式一：颜色名

+ 编写方式：直接使用颜色对应的英文单词，编写比较简单，例如：

  + **<font color=red>红色：red</font>**

  + **<font color=green>绿色：green</font>**

  + **<font color=blue>蓝色：blue</font>**

  + **<font color=purple>紫色：purple</font>**

  + **<font color=orange>橙色：orange</font>**

  + **<font color=gray>灰色：gray</font>**

    ....

  > 1. 颜色名这种方式，表达的颜色比较单一，所以用的并不多。
  >
  > 2. 具体颜色名参考`MDN`官方文档：
  >
  >    `https://developer.mozilla.org/en-US/docs/Web/CSS/named-color`

### 3、表示方式二：rgb 或 rgba

- 编写方式：使用 **红、绿、蓝** 这三种光的三原色进行组合。

  - <font color=red>**r** </font>表示 <font color=red>**红色**</font> （0,255）
  - <font color=green>**g**</font> 表示 <font color=green>**绿色**</font>（0,255）
  - <font color=blue>**b**</font> 表示 <font color=blue>**蓝色**</font>（0,255）
  - <font color=gray>**a**</font> 表示 <font color=gray>**透明度**</font>

- 举例：

  ```css
  /* 使用 0~255 之间的数字表示一种颜色 */
  color: rgb(255, 0, 0);/* 红色 */
  color: rgb(0, 255, 0);/* 绿色 */
  color: rgb(0, 0, 255);/* 蓝色 */
  color: rgb(0, 0, 0);/* 黑色 */
  color: rgb(255, 255, 255);/* 白色 */
  
  /* 混合出任意一种颜色 */
  color:rgb(138, 43, 226) /* 紫罗兰色 */
  color:rgba(255, 0, 0, 0.5);/* 半透明的红色 */
  
  /* 也可以使用百分比表示一种颜色（用的少） */
  color: rgb(100%, 0%, 0%);/* 红色 */
  color: rgba(100%, 0%, 0%,50%);/* 半透明的红色 */
  ```

- 小规律：

  > 1. 若三种颜色值相同，呈现的是灰色，值越大，灰色越浅。
  >
  > 2. `rgb(0, 0, 0)`是黑色，`rgb(255, 255,255)`是白色。
  >
  > 3. 对于`rbga`来说，前三位的`rgb`形式要保持一致，要么都是`0~255`的数字，要么都是`百分比`。
  >
  > 4. rgba中的a的范围是0到1，我们一般写的是小数 小数前面的0是可以省略的  直接写.5
  >
  >    也可以写百分比 但是一般很少

###  4、 表示方式三：HEX 或 HEXA

**`HEX` **的原理同与 **`rgb` **一样，依然是通过：<font color="red">**红**</font>、<font color="green">**绿**</font>、<font color="blue">**蓝色**</font> 进行组合，只不过要用 **6位（分成3组）** 来表达，

格式为：**#**<font color=red size=4>**rr**</font><font color=green size=4>**gg**</font>**<font color=blue size=4>bb</font>**

>每一位数字的取值范围是：`0 ~ f` ，即：（`0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a, b, c, d, e, f`）
>
>所以每一种光的最小值是：`00`，最大值是：`ff`

```css
color: #ff0000;/* 红色 */
color: #00ff00;/* 绿色 */
color: #0000ff;/* 蓝色 */
color: #000000;/* 黑色 */
color: #ffffff;/* 白色 */

/* 如果每种颜色的两位都是相同的，就可以简写*/
color: #ff9988;/* 可简为：#f98 */

/* 但要注意前三位简写了，那么透明度就也要简写 */
color: #ff998866;/* 可简为：#f986 */

```

> 注意点：`IE`浏览器不支持`HEXA`，但支持`HEX`。

### 5、 表示方式四：HSL 或 HSLA

- `HSL`是通过：色相、饱和度、亮度，来表示一个颜色的，格式为：`hsl(色相,饱和度,亮度)`

  - 色相：取值范围是`0~360`度，具体度数对应的颜色如下图：

  ![02](.\img\02.jpg) 

  - 饱和度：取值范围是`0%~100%`。（向色相中对应颜色中添加灰色，`0%`全灰，`100%`没有灰）

  - 亮度：取值范围是`0%~100%`。（`0%`亮度没了，所以就是黑色。`100%`亮度太强，所以就是白色了）

- `HSLA`其实就是在`HSL`的基础上，添加了透明度。

## 三、常用属性

### 1、CSS字体属性

#### 1.1、字体大小

+ 概念：CSS 使用 font-size 属性定义字体大小。

+ 语法：

  ```css
  p {  
      font-size: 20px; 
  }
  ```

+ 说明：

  + px（像素）大小是我们网页的最常用的单位
  + 谷歌浏览器支持的最小文字大小为12px，0px会隐藏字体，默认的文字大小为16px
  + 不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小
  + 可以给 body 指定整个页面文字的大小

#### 1.2、字体粗细

+ 概念：CSS 使用 font-weight 属性设置文本字体的粗细

+ 语法：

  ```css
  p {  
      font-weight: bold; 
  }
  ```

  | 属性值   | 描述                                                         |
  | -------- | ------------------------------------------------------------ |
  | normal   | 默认值（不加粗）                                             |
  | lighter  | 定义细的字体                                                 |
  | bold     | 定义粗体（加粗）                                             |
  | 100~1000 | `100~300`等同于`lighter`，`400~500`等同于`normal`，`600`及以上等同于`bold`，一般情况下都是100的倍数 |

+ 说明：

  + 学会让加粗标签（比如 h 和 strong 等) 不加粗，或者其他标签加粗
  + 实际开发时，我们更喜欢用数字表示粗细

#### 1.3、字体样式

+ 概念：CSS 使用 font-style 属性设置文本的风格

+ 语法：

  ```css
  p {  
      font-style: normal;
  }
  ```

  | 属性值  | 作用                                                    |
  | ------- | ------------------------------------------------------- |
  | normal  | 默认值，浏览器会显示标准的字体样式  font-style:normal； |
  | italic  | 浏览器会显示斜体的字体样式                              |
  | oblique | 斜体                                                    |

#### 1.4、字体变形

+ 概念：CSS 使用 font-variant属性设置文本的变形

+ 语法：

  ```css
  p{
  	font-variant: small-caps;
  }
  ```

  | 属性值     | 作用       |
  | ---------- | ---------- |
  | normal     | 默认值     |
  | small-caps | 小写转大写 |

#### 1.5、字体族

+ 概念： 我们认为的"字体"可能不是单纯的一个字体，而是由许多字体变形组成，分别用来描述粗体、斜 体、正常字体等等每种变体都有一个具体的字体风格。所以我们电脑中安装的字体有可能是一个字体系列(字体族)，而不是单纯的字体。

+ 语法：

  ```css
  p{
    font-family:"Arial","Helvetica",sans-serif;
  }
  ```

+ 说明：

  + 我们在写的时候一般使用的是字体的英文名字，为了规避乱码的风险。
  + 设定的字体如果名字包含空格，则应该使用引号包裹起来。
  + 可以定义多个字体，多个字体将按照列表中列出来顺序逐个查找，只要找到了一个就去应用如果到最后都没有找到name将会使用浏览器的默认字体（windows系统中，默认的字体就是微软雅黑）。

> 衬线字体，意思是在字的笔画开始、结束的地方有额外的装饰，而且笔画的粗细会有所不同，
>
> `sans-serif`无衬线字体也叫做非衬线字体 ，没有这些额外的装饰，而且笔画的粗细差不多。

#### 1.6、字体的综合写法

字体属性可以把以上文字样式综合来写, 这样可以更节约代码:

```css
body {font: font-style  font-weight  font-size  font-family;}
```

+ 使用 font 属性时，必须按上面语法格式中的顺序书写，不能更换顺序，并且各个属性间以空格隔开 不需要设置的属性可以省略（取默认值
+ 必须保留 font-size 和 font-family 属性，否则 font 属性将不起作用，
+ font-style  font-weight可以更换位置，但是必须放在font-size和font-family之前。

#### 1.7、字体总结

| 属性         | 表示     | 注视点                                                       |
| ------------ | -------- | ------------------------------------------------------------ |
| font-size    | 字号     | 通常用的单位是px像素，一定要跟上单位                         |
| font-family  | 字体     | 实际企业级研发中按照团队约定来写字体                         |
| font-weight  | 字体粗细 | `100~300`等同于`lighter`，`400~500`等同于`normal`，`600`及以上等同于`bold`，一般情况下都是100的倍数 |
| font-style   | 字体样式 | italic是倾斜，normal是不倾斜，常用normal                     |
| font-variant | 字体变形 | small-caps大写转小写                                         |
| font         | 字体连写 | 字体连写有顺序，位置不能随意更改，字号和字体需同时书写。     |

### 2、CSS文本属性

#### 2.1、文本颜色

+ 概念：color 属性用于定义文本的颜色

+ 语法：

  ```css
  div { 
      color: red;
  }
  ```

  | 标识方式       | 属性值                          |
  | -------------- | ------------------------------- |
  | 预定义的颜色值 | red，green，blue。。            |
  | HEX2           | \#FF000，#FF6600,#29d794        |
  | RGB代码        | rgb(255,0,0)或者rgb(100%,0%,0%) |
  | HSL            | hsl(0,50%,50%)                  |

+ 说明：

  + 开发中最常用的是HEX
  + rgba，格式`rgba(红,绿,蓝,透明度)`，多了一个透明度，透明度是0~1之间的值，0为完全透明，值越大越不透明。可以直接用`.n`的形式来表示，如：`.5`

#### 2.2、文本对齐-水平

+ 概念：text-align 属性用于设置元素内文本内容的水平对齐方式

+ 语法：

  ```css
  div { 
    text-align: center; 
  }
  ```

  | 属性值 | 描述             |
  | ------ | ---------------- |
  | left   | 左对齐（默认值） |
  | right  | 右对齐           |
  | center | 居中对齐         |

#### 2.3、文本对齐-垂直

+ 概念：vertical-align属性用于设置元素内文本内容的垂直对齐方式

+ 语法：

  + 情况1-div中包含了span，span标签在垂直方向的对其方式
  
  ```css
  div {
      font-size：100px;
      height:300px;
      background-color:tomato;
  }
  span{
      font-size:40px
      vertical-align:middle；
      background-color:yellowgreen;
  }
  
  <div>
  	atguigux尚硅谷x<span>x前端学科</span>
  </span>
  ```
  
  + 情况2-div中包含了img，img的高度小于div
  
  ```html
  div {
      font-size：100px;
      height:300px;
      background-color:tomato;
  }
  img {
  	height:30px;
  	vertical-align：middle；
  }
  
  <div>
      <img>
  </div>
  ```
  
  + 情况3-div中包含了img，img的高度大于div
  
  ```html
  div {
      font-size：100px;
      height:300px;
      background-color:tomato;
  }
  img {
  	height:200px;
  	vertical-align：middle；
  }
  
  <div>
      <img>
  </div>
  ```
  
  | 属性值   | 描述                                                         |
  | -------- | ------------------------------------------------------------ |
  | top      | 将支持valign特性的对象的内容与对象顶端对齐                   |
  | middle   | 将支持valign特性的对象的内容与对象中部对齐                   |
  | bottom   | 将支持valign特性的对象的文本与对象底端对齐                   |
  | baseline | 将支持valign特性的对象的内容与基线对齐， **基线**“baseline”并不是汉字文字的下端沿，而是英文字母的下端沿。 |

#### 2.4、文本修饰

+ 概念：text-decoration属性用于设置文本的修饰的属性

+ 语法：

  ```css
  div { 
      text-decoration：underline;
  }
  ```

  | 属性值       | 描述                                        |
  | ------------ | ------------------------------------------- |
  | none         | 默认，没有装饰线（常用），清除a标签的下划线 |
  | underline    | 下划线，链接a自带下划线（常用）             |
  | overline     | 上划线，（几乎不用）                        |
  | line-through | 删除线，（不常用）                          |


> 重点记住如何添加下划线 ? 如何删除下划线 ? 其余了解即可.

#### 2.5、文本缩进

+ 概念：text-indent属性用于设置文本的缩进的属性

+ 语法：

  ```css
  p { 
  	text-indent:200px;
  }
  ```


#### 2.6、文本间距

+ 概念：定义字母/汉字之间的距离

+ 语法：

  ```css
  letter-spacing:value; /*定义字母/汉字之间的距离*/
  
  word-spacing:value; /*定义单词之间的间隔*/
  ```

  - normal，相当于`letter-spacing:0`
  - px，像素

#### 2.7、文本换行

+ 概念：white-space属性用于设置文本的换行的属性

+ 语法：

  ```css
  div { 
  	width: 50px;
  	height: 50px;
  	border: aqua solid 1px;
  	white-space:nowrap;/*用来处理元素内文本是否允许换行。*/
  }
  ```

  - normal，默认值。`CJK文本`遇到容器便捷自动换行，非`CJK文本`由word-break来决定。

    CJK：`China`、`Japan`、`Korea`，中日韩三国的文字。

  - nowrap，超出容器边界不换行。

  - normal，根据浏览器默认的换行规则来决定是否进行换行。
  
  扩展：
  
  - word-break：break-all，允许在单词内换行。


#### 2.8、隐藏内容

+ 概念：overflow属性用于设置文本的隐藏的属性

+ 语法：

  ```css
  div { 
  	width: 50px;
  	height: 50px;
  	border: aqua solid 1px;
  	overflow: auto;
  }
  ```

  - visible，超出元素框的内容是可见的。
  - hidden，超出元素框的内容隐藏。
  - scroll，多出的内容滚动条显示。
  - auto，浏览器自己决定。（通常具有不确定性）

#### 2.9、行高

+ 概念：line-height 属性用于设置行间的距离（行高），可以控制文字行与行之间的距离

+ 语法：

  ```css
  div { 
      font-size：20;
      line-height: 26px;
  }
  ```

  + `normal`：
    + 默认值，跟随用户的浏览器走，且与字体相关联。

  - `px`
    - 像素值。
  - `数值`：
    - 该数值是font-size的倍数，没有单位
    - 一般是1到2之间，我们在实际的企业级开发的时候 一般是1.5以上2一下  具体1.6左右*
    - 如果数值的结果小于0了 那么就是normal 
  - `百分比`
    - 根据字体大小判断

+ 作用：

  + 使单行文字在垂直区域居中---》让文字的行高等于盒子的高度。

    ```html
    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="utf-8">
    		<title></title>
    		<style type="text/css">
    			div { 
    				width: 220px;
    				height: 220px;
    				border: black solid 1px;
    				line-height: 220px;
    			}
    		</style>
    	</head>
    	<body>
    		<div>细节决定成败</div>
    	</body>
    </html>
    ```


  + 调整多行文字的间距

    ```html
    <!DOCTYPE html>
    <html lang="zh-CN">
        <head>
            <meta charset="UTF-8" />
            <title>文本属性-行高-作用2-多行文字</title>
            <style>
                div {
                    height: 500px;
                    background-color: aquamarine;
                    font-size: 30px;
                    /* 针对于多行文字来说  调整的是多行文字之间的距离
                   使用的非常少 */
                    line-height: 50px;
                }
            </style>
        </head>
        <body>
            <div>
                绵绵的青山脚下花正开x
                绵绵的青山脚下花正开x
                绵绵的青山脚下花正开x
                绵绵的青山脚下花正开x
                绵绵的青山脚下花正开x
                绵绵的青山脚下花正开x
                绵绵的青山脚下花正开x
            </div>
        </body>
    </html>
    ```

+ 细节提升

  + 行高的值不要和font-size一致

  + 行高设置为0

    + 如果设置为0，文字会发生重叠
    + 如果设置为0，那么文字顶部丢失
    + 如果设置为0，背景色消失

  + 如果行高越小，基线靠上，文字会偏上

  + 如果行高越大，基线靠下，文字会偏下

  + 行高是可以继承的

    ```css
    <!DOCTYPE html>
    <html lang="zh-CN">
        <head>
            <meta charset="UTF-8" />
            <title>行高-细说行高-行高可以继承</title>
            <style>
                div {
                    font-size: 40px;
                    height: 500px;
                    background-color: aquamarine;
                    line-height: 1.5;
                }
    
                span {
                    font-size: 100px;
                    background-color: purple;
                }
            </style>
        </head>
        <body>
            <!-- （1）行高可以继承
                 （2）为什么要我们写倍数 
                      因为继承了父元素的1.5倍  会自动计算当前标签font-size1.5倍
                      然后当做行高就可以了   
            -->
            <div>
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
                惊雷这通天修为天塌地陷<span>紫金锤g</span>紫电
            </div>
        </body>
    </html>
    ```

  + line-height和height的关系

    + 如果设置了height，那么height的值就是height
    + 如果没有设置height，那么高度就是行高*行数

### 3、CSS列表属性

#### 3.1、列表类型

格式：`list-style-type:value`

- none：不显示前面的标识，当为none时不会阻断有序列表的计算。
- square：实心方块。
- disc：圆形。
- decimal：数
- lower-roman：小写罗马字
- upper-roman：大写罗马字
- lower-alpha：小写字母
- upper-alpha：大写字母

#### 3.2、列表图像

格式：`list-style-image:url(图像地址)`

#### 3.3、列表标识的位置

格式：`list-style-position:value`

- outside：标示在li外面
- inside：   标示在li里面

#### 3.4、列表复合属性

格式：``list-style:type image position`

> 最常见的列表属性设置
> list-style: none;

顺序可以颠倒

### 4、CSS背景属性

通过 CSS 背景属性，可以给页面元素添加背景样式。 背景属性可以设置背景颜色、背景图片、背景平铺、背景图片位置、背景图像固定等。

#### 4.1、背景颜色

+ 概念：background-color 定义元素的背景颜色

+ 语法：

  ```css
  background-color：颜色值；
  ```

+ 扩展：

  + 元素背景颜色默认值是 transparent（透明）

    ```css
    background-color：transparent；
    ```

  + `transparent`，默认值（透明）。元素的默认背景色是透明的包括html和body标签。

    解释为什么整个页面看起来是白色的，不是transparent吗？

    1. body和html并不是整个页面，body由内容撑开，html由body撑开。
    2. 整个的层次：`body -> html -> 页面画布`
    3. 最终整体的背景颜色是由`页面画布`决定的。
    4. 画布颜色的决定规则：有html的颜色就使用html的颜色，html没有就使用body的颜色，如果都没有则使用画布本身的颜色透明（页面画布的最终颜色由浏览器自己决定，但一般的浏览器都将默认颜色设置成白色。）

#### 4.2、背景图片

+ 概念： background-image 定义元素的背景图片

+ 语法：

  ```css
  background-image：none|url（url）
  ```

  | 参数值 | 描述                             |
  | ------ | -------------------------------- |
  | none   | 无背景图（默认）                 |
  | url    | 使用绝对或者相对地址指定背景图像 |

> 注意：背景图片后面的地址，千万不要忘记加 URL， 同时里面的路径**不要加引号**。

#### 4.3、背景平铺

+ 概念：background-repeat 设置元素背景图像的平铺

+ 语法：

  ```css
  background-repeat：repeat | no-repeat | repeat-x | repeat-y
  ```

  | 参数值    | 描述                               |
  | --------- | ---------------------------------- |
  | repeat    | 背景图像在纵向和横向上平铺（默认） |
  | no-repeat | 背景图像不平铺                     |
  | repeat-x  | 背景图像在横向上平铺               |
  | repeat-y  | 背景图像在纵向上平铺               |

#### 4.4、背景图片位置

+ 概念：background-position 属性可以改变图片在背景中的位置

+ 语法：

  ```css
  background-position：x y;
  ```

  参数代表的意思是：x 坐标和 y 坐标。 可以使用 方位名词 或者 精确单位

  | 参数值   | 描述                                               |
  | -------- | -------------------------------------------------- |
  | length   | 百分数\|由浮点数和单位标识符组成的长度值           |
  | position | top \| center \| bottom \| left \| center \| right |

  **其他说明：**

  1、参数是方位名词

   如果指定的两个值都是方位名词，则两个值前后顺序无关，比如 left top 和 top left 效果一致

   如果只指定了一个方位名词，另一个值省略，则第二个值默认居中对齐

  2、参数是精确单位

   如果参数值是精确坐标，那么第一个肯定是 x 坐标，第二个一定是 y 坐标。

   如果只指定一个数值，那该数值一定是 x 坐标，另一个默认垂直居中。

   如果是正数背景图将会往右、下移动，如果是负数背景图将会往左、上移动。

  3、参数是混合单位

   如果指定的两个值是精确单位和方位名词混合使用，则第一个值是 x 坐标，第二个值是 y 坐标

#### 4.5、背景图片固定

+ 概念：background-attachment 属性设置背景图像是否固定或者随着页面的其余部分滚动，这个是css3的样式。

+ 语法：

  ```css
  background-attachment：scroll | fixed
  ```

  | 参数   | 描述                       |
  | ------ | -------------------------- |
  | scroll | 背景图像是随着对象内容滚动 |
  | fixed  | 背景图像固定               |

  **其他说明：**

   background-attachment 后期可以制作视差滚动的效果。

#### 4.6、背景样式合写

+ 概念：background: 背景颜色 背景图片地址 背景平铺 背景图像滚动 背景图片位置;

+ 语法：

  ```css
  background：transparent url（image.jpg） repeat-y fixed top;
  ```

#### 4.7、背景色半透明

+ 概念：CSS3 提供了背景颜色半透明的效果。

+ 语法：

  ```css
  background：rgba（0,0,0,0.3）;
  ```

  - 最后一个参数是 alpha 透明度，取值范围在 0~1之间
  - 我们习惯把 0.3 的 0 省略掉，写为 background: rgba(0, 0, 0, .3);

  **注意**：

  - 背景半透明是指盒子背景半透明，盒子里面的内容不受影响

#### 4.8、背景总结

| 属性                  | 作用           | 值                                               |
| --------------------- | -------------- | ------------------------------------------------ |
| background-color      | 背景颜色       | 预定义的颜色值/十六进制/RGB代码                  |
| background-image      | 背景图片       | url（图片路径）                                  |
| background-repeat     | 是否平铺       | repeat/no-repeat/repeat-x/repeat-y               |
| background-position   | 背景位置       | length/position 分别是x和y坐标                   |
| background-attachment | 背景附着       | scroll（背景滚动）/fixed（背景固定）             |
| 背景简写              | 书写更加简单   | 背景颜色 背景图片地址 背景平铺 背景滚动 背景位置 |
| 背景色半透明          | 背景颜色半透明 | background：rgba（0,0,0,0.3）；后面是四个值      |

### 5、CSS表格属性

| CSS 属性名      | 功能                     | 属性值                                                       |
| --------------- | ------------------------ | ------------------------------------------------------------ |
| table-layout    | 定义列宽度               | auto：自动，列宽根据内容计算。<br>fixed：固定列宽（不指定宽平均分） |
| border-collapse | 合并单元格`边框`         | collapse：合并                                               |
| border-spacing  | 单元格间距               | 长度<br>生效的前提：单元格边框不能合并                       |
| empty-cells     | 用于隐藏没有内容的单元格 | show：显示，默认<br>hide：隐藏<br>生效前提：单元格不能合并   |
| caption-side    | 设置表格标题位置         | top：在表格上面，默认<br>bottom：在表格下面                  |

> **注意：**
>
> 以上 5 个 css 属性设置给 table 元素才有用，给其他元素无效。

### 6、CSS鼠标属性

| CSS 属性名 | 功能               | 属性值                                                       |
| ---------- | ------------------ | ------------------------------------------------------------ |
| cursor     | 设置鼠标光标的样式 | pointer：   小手<br>move：      移动图标<br>text:            文字选择器 <br>crosshair:   十字架 <br>wait:            等待 |

```css
 /* 自定义鼠标光标 */
 cursor: url(images/arrow.ico),pointer;
```

