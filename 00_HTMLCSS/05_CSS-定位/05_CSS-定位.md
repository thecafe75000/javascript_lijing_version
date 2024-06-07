+ 书写位置
+ 选择器
+ 属性
+ 布局
  + 浮动   横向排列

## 一、CSS定位前提

### 1、为什么要学习定位

思考：如何实现红色框中的功能？

![01](.\img\01.jpg)

![02](.\img\02.jpg)

> 以我们现在掌握的知识，无论是标准流还是浮动都无法很好的实现。
>
> **标准流**是从上到下，从左到右执行，正常展示
>
> **浮动**是多个块级盒子一行横向排列

### 2、什么是CSS定位

![03](.\img\03.jpg)

+ CSS定位也叫做**定位布局**，是继文档流，浮动布局之后的第三大布局方式，定位的意思是指定一个元素/盒子在网页上的位置
+ 使用 position、left、right、top、bottom，可以改变元素现有位置，譬如让元素从正常布局流中跳出来，固定在页面某个位置上。
+ 可以让盒子自由的在某个盒子内移动位置或者固定屏幕中某个位置

## 二、CSS定位基础

### 1、定位的组成

#### 1.1、定位格式

+ 代码演示

  ```css
  div{
    	  position: absolute;/*定位模式*/
  	  top: 100px;        /*边偏移属性*/
  }
  ```

+ 组成部分

  定位模式 + 边偏移量属性

  > 定位模式就是参照谁
  >
  > 边偏移量属性就是移动的数值

#### 1.2、定位模式

使用`position`属性作为定位模式的属性名字

+ 语法：

  ```css
  选择器 { 
      position: 属性值; 
  }
  ```

+ 定位属性值

  | 取值       | 说明                                       |
  | -------- | ---------------------------------------- |
  | static   | 【静态定位】，默认值，表示没有定位，元素会按照正常的位置显示，此时 top、bottom、left 和 right 4 个定位属性也不会被应用。 |
  | relative | 【相对定位】，即相对于元素的正常位置进行定位，您可以通过 top、right、bottom、left 这 4 个属性来设置元素相对于正常位置的偏移量，在此过程中不会对其它元素造成影响。 |
  | absolute | 【绝对定位】，相对于第一个非 static 定位的父级元素进行定位，可以通过 top、right、bottom、left 这 4 个属性来设置元素相对于父级元素位置的偏移量。如果没有满足条件的父级元素，则会相对于浏览器窗口来进行定位。使用绝对定位的元素不会对其它元素造成影响。 |
  | fixed    | 【固定定位】，相对于浏览器的创建进行定位，可以使用 top、right、bottom、left 这 4 个属性来定义元素相对于浏览器窗口的位置。使用固定定位的元素无论如何滚动浏览器窗口元素的位置都是固定不变的。 |
  | sticky   | 【粘性定位】，它是 relative 和 fixed 的结合体，能够实线类似吸附的效果，当滚动页面时它的效果与 relative 相同，当要滚动到屏幕之外时则会自动变成 fixed 的效果。 |

#### 1.3、边偏移量属性

+ 上边偏移属性

  用来定义元素顶部偏移位置的大小。top: auto | length | percent

  ```html
  <!DOCTYPE html>
  <html>
   <head>
    <title>上边偏移属性</title>
    <style>
      div{
  	  position: absolute;
  	  top: 100px;
  	  border: 2px solid black;
  	  background: red;
  	  width: 300px;
  	  height: 50px;
  	}
    </style>
   </head>
   
   <body>
     <div>这是上边偏移属性</div>
   </body>
  </html>

  ```

+ 右边偏移属性

  用来定义元素右侧偏移位置的大小。right: auto | length | percent;

  ```html
  <!DOCTYPE html>
  <html>
   <head>
    <title>右边偏移属性</title>
    <style>
      div{
  	  position: absolute;
  	  right: 100px;
  	  border: 2px solid black;
  	  background: red;
  	  width: 300px;
  	  height: 50px;
  	}
    </style>
   </head>
   <body>
     <div>这是右边偏移属性</div>
   </body>
  </html>
  ```

+ 下边偏移属性

  用来定义底部偏移位置的大小。bottom:auto | length | percent;

  ```html
  <!DOCTYPE html>
  <html>
   <head>
    <title>下边偏移属性</title>
    <style>
      div{
  	  position: absolute;
  	  bottom: 100px;
  	  border: 2px solid black;
  	  background: red;
  	  width: 300px;
  	  height: 50px;
  	}
    </style>
   </head>
   
   <body>
     <div>这是下边偏移属性</div>
   </body>
  </html>

  ```

+ 左边偏移属性

  用来定义元素左边偏移位置的大小，left: auto | length | percent;

  ```html
  <!DOCTYPE html>
  <html>
   <head>
    <title>左边偏移属性</title>
    <style>
      div{
  	  position: absolute;
  	  left: 100px;
  	  border: 2px solid black;
  	  background: red;
  	  width: 300px;
  	  height: 50px;
  	}
    </style>
   </head>
   
   <body>
     <div>这是左边偏移属性</div>
   </body>
  </html>

  ```

+ 总结

  | 选项     | 说明   |
  | ------ | ---- |
  | top    | 距离顶边 |
  | bottom | 距离下边 |
  | left   | 距离左部 |
  | right  | 距离右边 |

### 2、定位模式

#### 2.1、静态定位

+ 概念

  ​	static 是 position 属性的默认值，表示没有定位，使用静态定位的元素会按照元素正常的位置显示，并且不会受到 top、bottom、left、right 和 z-index 属性的影响

+ 语法

  ```css
  选择器 { 
      position: static; 
  }
  ```

+ 案例

  ```html
  <!DOCTYPE html>
  <html>
  <head>
      <style>
          div{
              height: 100px;
              border: 1px solid black;
          }
          div.static {
              width: 130px;
              height: 50px;
              background-color: #CCC;
              position: static;
              top: 50px;
              left: 20px;
          }
      </style>
  </head>
  <body>
      <div>
          <div class="static">谁在让我东张西望</div>
      </div>
  </body>
  </html>
  ```

+ 特点

  + 静态定位 按照标准流特性摆放位置，它没有边偏移。

#### 2.2、相对定位

+ 概念

  ​	相对定位就是元素相对于自己默认的位置来进行位置上的调整，可以通过 top、bottom、left 和 right 四个属性的组合来设置元素相对于默认位置在不同方向上的偏移量。

![04](.\img\04.jpg)

+ 语法

  ```css
  选择器 { 
      position: relative; 
  }
  ```

+ 案例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Document</title>
      <style>
          .wrapper {
              width: 800px;
              border: 2px dashed red;
              padding: 20px;
          }
          .box {
              width: 200px;
              height: 150px;
              border: 2px solid green;
              background-color: #ccc;
          }

          .box02 {
              /* 相对定位 */
              position: relative;
              left: 300px;

               /* margin-left: 25px; */
               /* margin-top: 100px; */

               /* 设置浮动 */
               /* float: left; */
          }
      </style>
  </head>
  <body>
      <h1>相对定位</h1>
      <hr>

      <div class="wrapper">
          <div class="box box01">1</div>
          <div class="box box02">2</div>
          <div class="box box03">3</div>
      </div>
      <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
      </p>
  </body>
  </html>
  ```

+ 特点

  + 相对于自己原来的位置来移动的（移动位置的时候参照点是自己原来的位置）
  + 同时使用left、right时，left生效；同时使用top、bottom时，top生效。
  + 不会脱离文档流，不会对其他元素产生任何影响
    + 相对定位元素效果上位置调整，但是文档流中仍然保留原来的位置，其他元素会按照它原来的位置在文档流中排列
  + 可以和外边距一起使用
  + 相对定位的元素可以设置为浮动

> 注意：一般，相对定位会用于与绝对定位配合！
  >

#### 2.3、绝对定位

+ 概念

   绝对定位就是元素相对于第一个非静态定位（static）的父级元素进行定位，如果找不到符合条件的父级元素则会相对与"浏览器窗口"来进行定位。同样可以使用 top、bottom、left 和 right 四个属性来设置元素相对于父元素或浏览器窗口不同方向上的偏移量。

![05](.\img\05.jpg)

+ 语法

  ```html
   选择器 { 
       position: absolute; 
   }
  ```

+ 案例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Document</title>
      <style>
          /* body {
              position: relative;
          } */

          .wrapper {
              /* 定义 */
              /* position: relative; */
              border: 2px dashed red;
              padding: 20px;
              width: 800px;

          }

          .box {
              width: 200px;
              height: 150px;
              border: 2px solid green;
              background-color: #ccc;
          }

          .box02 {
             /* 设置为绝对定位 */
             position: absolute;

             /* 定位 */
             /* left: 20px; */
             /* top: 20px; */

             right: 100px;
             bottom: 0;

             /* margin-right: 50px; */

              /* 绝对定位与浮动不能共存 */
             /* float: left; */
          }
      </style>
  </head>
  <body>
      <h1>绝对定位</h1>
      <hr>

      <div class="wrapper">
          <div class="box box01">1</div>
          <div class="box box02">2</div>
          <div class="box box03">3</div>
      </div>

      <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
      </p>
      <!-- <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
      </p>
      <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
      </p>
      <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
      </p> -->
  </body>
  </html>
  ```

+ 特点

  + 绝对定位就是元素相对于第一个非静态定位（static）的父级元素进行定位，如果找不到符合条件的父级元素则会相对与"浏览器窗口"来进行定位。
  + 同时使用left、right时，left生效；同时使用top、bottom时，top生效。
  + 脱离文档流
  + 绝对定位不可以和外边距一起使用
  + 绝对定位不可以和浮动一起使用
  + **父元素没有定位**，则以**初始包含块（浏览器的第一屏）**为准定位
  + 子绝父相

#### 2.4、固定定位

+ 概念

  ​	固定定位就是将元素相对于浏览器窗口进行定位，使用固定定位的元素不会因为浏览器窗口的滚动而移动，就像是固定在了页面上一样，我们经常在网页上看到的返回顶部按钮就是使用固定定位实现的。

+ 语法

  ```css
   选择器 { 
       position: fixed; 
   }
  ```

+ 案例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Document</title>
      <style>
          .wrapper {
              /* 定义 */
              /* position: relative; */
              border: 2px dashed red;
              padding: 20px;
              width: 800px;
  
          }
  
          .box {
              width: 200px;
              height: 150px;
              border: 2px solid green;
              background-color: #ccc;
          }
  
          .box02 {
              /* 固定定位 */
              position: fixed;
  
              /* left: 10px;
              top: 10px; */
  
              right: 20px;
              bottom: 20px;
          }
          p {
            width: 600px;
        }
    </style>
       </head>
    <body>
        <h1>固定定位</h1>
        <hr>
          <div class="wrapper">
        <div class="box box01">1</div>
        <div class="box box02">2</div>
        <div class="box box03">3</div>
    </div>
  
    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
    </p>
    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
    </p>
    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
    </p>
    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil nobis consequatur incidunt sit blanditiis neque commodi facilis ipsum, ullam veritatis perspiciatis voluptates rem hic repellat. Error temporibus tempore rem ducimus?
    </p>
          </body>
    </html>      
  ```

+ 特点

  + 以浏览器的可视窗口为参照点移动元素
  + 同时使用left、right时，left生效；同时使用top、bottom时，top生效。
  + 脱离文档流，固定定位**不在占有原先的位置**，**也可以看做是一种特殊的绝对定位**
  + 跟父元素没有任何关系，不随滚动条滚动。

#### 2.5、粘性定位

+ 概念

  ​		粘性定位与前面介绍的四种定位方式不太一样，它像是相对定位和固定定位的结合体，当滚动页面时它的效果与相对定位相同，当元素滚动到一定程度时它又会呈现出固定定位的效果。比如一些网页上的导航菜单，当页面加载完成时它在自己默认的位置，当我们向下滚动页面时它又会固定在页面的最顶端。

+ 语法

  ```css
   选择器 { 
       position: sticky; 
       top: 10px; 
   }
  ```

+ 案例

  ```html
  <!DOCTYPE html>
  <html>
  <head>
      <style>
          div{
              height: 500px;
          }
          p {
              width: 100%;
              height: 50px;
              margin: 0;
              text-align: center;
              line-height: 50px;
              background-color: #CCC;
          }
          p.sticky {
              background-color: blue;
              position: sticky;
              top:0px;
          }
      </style>
  </head>
  <body style="height: 1100px;">
      <div>
          <p>1</p>
          <p>2</p>
          <p class="sticky">欢迎光临红浪漫</p>
          <p>4</p>
          <p>5</p>
          <p>6</p>
          <p>7</p>
          <p>8</p>
          <p>9</p>
      </div>
  </body>
  </html>
  ```

+ 特点

  + 以浏览器的可视窗口为参照点移动元素（固定定位特点）
  + 必须添加 top 、left、right、bottom **其中一个**才有效
  + 粘性定位占有原先的位置（相对定位特点）
  + 大部分的时候会结合top来使用，一般用于移动端，pc端使用的比较少。
  + 跟页面滚动搭配使用。 兼容性较差，IE 不支持。

#### 2.6、总结

| **定位模式**          | **是否脱离文档流**   | **移动位置**           | **是否常用**                 |
| --------------------- | -------------------- | ---------------------- | ---------------------------- |
| static 静态定位       | 否                   | 不能使用边偏移         | 很少                         |
| **relative 相对定位** | **否 (占有位置)**    | **相对于自身位置移动** | **基本单独使用**             |
| **absolute绝对定位**  | **是（不占有位置）** | **带有定位的父级**     | **要和定位父级元素搭配使用** |
| **fixed 固定定位**    | **是（不占有位置）** | **浏览器可视区**       | **单独使用，不需要父级**     |
| sticky 粘性定位       | 否 (占有位置)        | 浏览器可视区           | 当前阶段少                   |

#### 2.7、z-index属性

+ 概念

  在使用**定位**布局时，可能会**出现盒子重叠的情况**，我们有可能会调整盒子的位置。此时，可以使用 **z-index** 来控制盒子的前后次序 (z轴)。

+ 语法

  ```css
  选择器 { 
      z-index: 1; 
  }
  ```

+ 案例

  ```html
  <!DOCTYPE html>
  <html lang="zh-CN">
      <head>
          <meta charset="UTF-8" />
          <title>定位-z-index-定位层级</title>
  
          <style>
              /* （1）如果定位层级一样  会覆盖 
                 （2）可以通过z-index来修改定位的层级 
                      值越大 层级越高 默认是0  可以为负数  但是我们不写负数
              */
  
              #d1 {
                  position: absolute;
                  /* z-index: -1; */
                  width: 200px;
                  height: 200px;
                  background-color: tomato;
              }
  
              #d2 {
                  position: absolute;
                  /* z-index只有定位元素才可以使用 */
                  /* z-index: -2; */
                  width: 300px;
                  height: 300px;
                  background-color: yellowgreen;
              }
          </style>
      </head>
      <body>
          <div id="d1"></div>
          <div id="d2"></div>
      </body>
  </html>
  ```

+ 特点

  + **属性值**：**正整数**、**负整数**或 **0**，默认值是 0，数值越大，盒子越靠上；
  + **属性值相同**，则按照书写顺序，**后来居上**；
  + 数字后面**不能加单位**。
  + 指定一个定位的元素及其后代的层叠顺序，只有定位元素（非static值）设置 z-index 才可以生效。
  + z-index 的默认值是 auto。

### 3、特殊情况

#### 3.1、情况1

父子盒子没有层级影响

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>test</title>
        <style>
            .d1 {
                position: relative;
                width: 500px;
                height: 300px;
                background-color: aquamarine;
                z-index: 5;
            }

            .d2 {
                position: relative;
                z-index: 1;
                width: 300px;
                height: 300px;
                background-color: tomato;
            }
        </style>
    </head>
    <body>
        <div class="d1">
            <div class="d2"></div>
        </div>
        
    </body>
</html>
```

元素的显示层级受到父元素的显示层级的影响

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .wrapper {
            position: relative;
            width: 800px;
            height: 300px;
            padding: 20px;
            border: 2px dashed red;
            background-color: #f5f5f5;

            z-index: 3;
        }

        .box {
            position: absolute;
            left: 0;
            top: 0;
            z-index: 29;
            width: 200px;
            height: 200px;
            background-color: green;
        }

        .content {
            position: absolute;
            top: 50px;
            left: 60px;
            z-index: 2;
            width: 300px;
            height: 150px;
            background-color: yellow;
        }

    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box"></div>
    </div>

    <div class="content"></div>
</body>
</html>
```

#### 3.2、情况2

定位元素的默认宽度

+ static定位元素的宽：内部元素的宽会根据外部元素的宽自动计算，从而固定一个宽度，如果给小盒子添加了边框或者内边距会压缩这个宽度

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .wrapper {
            padding: 20px;
            width: 800px;
            height: 300px;
            border: 2px dashed red;
        }

        .box {
            border: 5px solid cyan;
            padding: 20px;
            background: green;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box">炸雷</div>
    </div>
</body>
</html>
```

+ 定位元素的默认宽度-相对定位

  相对定位元素 的宽和写了static定位元素的宽是一致的

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .wrapper {
            padding: 20px;
            width: 800px;
            height: 300px;
            border: 2px dashed red;
        }

        .box {
			position: relative;
            border: 5px solid cyan;
            padding: 20px;
            background: green;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box">炸雷</div>
    </div>
</body>
</html>
```

+ 定位元素的默认宽度-绝对定位

  不会根据父元素的内容计算，根据本身内容计算，类似行内块

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .wrapper {
            padding: 20px;
            width: 800px;
            height: 300px;
            border: 2px dashed red;
        }

        .box {
			position: absolute;
            border: 5px solid cyan;
            padding: 20px;
            background: green;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box">炸雷</div>
    </div>
</body>
</html>
```

+ 定位元素的默认宽度-绝对定位-和父元素一样宽

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .wrapper {
			position: relative;
            padding: 20px;
            width: 800px;
            height: 300px;
            border: 2px dashed red;
        }

        .box {
			position: absolute;
			/* width: 100%; */
			/* 不能和宽度高度一起使用 使用就失效了 */
			left: 0;
			right: 0;
          
          	top: 0;
			bottom: 0;
			/* width: 200px;
			height: 150px; */
            border: 5px solid cyan;
            padding: 20px;
            background: green;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box">炸雷</div>
    </div>
</body>
</html>
```

+ 定位元素的默认宽度-固定定位

  默认是被内容撑开，可以使用left right top bottom设置

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .wrapper {
			position: relative;
            padding: 20px;
            width: 800px;
            height: 300px;
            border: 2px dashed red;
        }

        .box {
			position: absolute;
			/* width: 100%; */
			/* 不能和宽度高度一起使用 使用就失效了 */
			left: 0;
			right: 0;
			
			top: 0;
			bottom: 0;
			/* width: 200px;
			height: 150px; */
            border: 5px solid cyan;
            padding: 20px;
            background: green;
        }
		
		.fixedbox{
			position: fixed;
			left: 200px;
			right: 200px;
			top: 200px;
			bottom: 200px;
			background-color: salmon;
		}
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box">炸雷</div>
    </div>
	
	<div class="fixedbox">fff</div>
</body>
</html>
```

+ 总结
  + 固定定位和绝对定位的元素默认宽高都是被内容撑开；相对定位看元素本来是哪一种显示模式。
  + 如果想设置定位元素宽度与包含块宽度一致，可以给定位元素同时设置 left 和 right 为 0；高度想与包含块一致，top 和 bottom 设置为 0。

#### 3.3、情况3

> 前提：让行内元素或行内块元素**水平居中对齐**，在其父元素上设置 `text-align:center`
>
> ​            让行内元素或行内块元素**垂直居中对齐**，在其父元素上设置 `line-height` 属性，行高的值与高度相等即可。
>
> ​            块级元素 在水平位置的居中 使用的是 magin 0 auto
>
> ​            块元素  左右外边距 auto  垂直居中可以吗？

+ 定位元素在包含块中水平垂直都居中1

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .wrapper {
            position: relative;
            border: 2px dashed red;
            height: 600px;
        }
        .box {
            position: absolute;
            left: 50%;
            top: 50%;
            margin-top: -100px;
            margin-left: -150px;
            width: 300px;
            height: 200px;
            background-color: green;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box"></div>
    </div>
</body>
</html>
```

+ 定位元素在包含块中水平垂直都居中2

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .wrapper {
            position: relative;
            border: 2px dashed red;
            height: 600px;
        }
        .box {
            position: absolute;
            left:0;
            right:0;
            top:0;
            bottom:0;
            margin: auto;
            width: 300px;
            height: 200px;
            background-color: green;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box"></div>
    </div>
</body>
</html>
```

