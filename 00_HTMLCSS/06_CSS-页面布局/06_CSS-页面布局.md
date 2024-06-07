## 一、精灵图

### 1、精灵图的介绍

#### 1.1、概念

CSS Sprites 也称之为精灵图或雪碧图，是一种**背景图片**的应用处理方式，将很多小图片合并到到一张大图中去。把整个大图作为背景图，然后通过 `background-position` 属性将合适的图片显示到元素上。

#### 1.2、目的

精灵图最大的作用是**减少网络的请求次数**，因为图片只要下载一次就好，不用再分别去下载那些小图。

![03](.\img\03.png)

#### 1.3、总结

+ 精灵图主要**针对于小的背景图片**使用。
+ 主要借助于背景位置来实现---**background-position** 。
+ 一般情况下精灵图都是**负值**。（注意网页中的坐标： x轴右边走是正值，左边走是负值， y轴同理。）

### 2、精灵图的使用

#### 2.1、基本语法

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>03_精灵图的基本使用</title>
        <style>
            .box {
                display: inline-block;
                width: 100px;
                height: 100px;
                background: url(./img/bg02.png) no-repeat;
            }

            .box01 {
                background-position: 0 0;
            }

            .box02 {
                background-position: -100px -100px;
            }

            .box03 {
                background-position: -200px -200px;
            }

            .box04 {
                background-position: -200px -100px;
            }

        </style>
    </head>
    <body>
        <!-- （1）展示三次这个图片
             （2）展示每一张图中的部分颜色 -->
        <div class="box box01"></div>
        <div class="box box02"></div>
        <div class="box box03"></div>
        <div class="box box04"></div>
        <div class="box"></div>
    </body>
</html>
```

#### 2.2、案例练习

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .btn {
            width: 120px;
            height: 56px;
            border: none;
            background: transparent url(images/toolbars.png) no-repeat;
        }
        .btn1 {
            background-position:  -100px 0;
        }
        .btn2 {
            background-position: -220px 0;
        }
    </style>
</head>
<body>
    <h1>精灵图的使用</h1>
    <hr>

    <button class="btn btn1"></button>
    <button class="btn btn2"></button>
</body>
</html>
```

#### 2.3、制作精灵图

在线工具 <https://alloyteam.github.io/gopng/>

![04](.\img\04.png)

![05](.\img\05.png)

![06](.\img\06.png)

![07](.\img\07.png)

## 二、favicon 图标

### 1、favicon 图标介绍

网站图标

![08](.\img\08.jpg)

**favicon 图标** 一般用于作为缩略的网站标志,它显示位于浏览器的地址栏或者在标签上，用于显示网站的logo，如图红圈的位置， 目前主要的浏览器都支持 favicon 图标。

favicon 图标文件一般命名为 `favicon.ico`， 是后缀为 `.ico` 的图片文件。

### 2、favicon 图标的使用

**使用方法一：**把 ico 图标文件命名为 `favicon.ico` ,放在网站根目录下，网页会自动获取 ico 图标，

-必须使用live server

**使用方法二：**在网页中使用 link 标签自行引入 ico 文件。

```
<link rel="shortcut icon" type="images/x-icon" href="favicon.ico">
```

### 3、favicon 图标的制作

- 在线工具 <http://www.ico51.cn/>
- 在线工具 <http://www.bitbug.net/>

## 三、页面布局

### 1、页面组成

![01](.\img\01.png)

### 2、重置样式

​	很多元素是具有默认样式的，比如 p 元素有默认的上外边距和下外边距，h1~h6 标题元素也有默认的上外边距和下外边距且字体加粗，body 元素有默认的外边距，超链接有默认的字体颜色和下划线，ul 元素有默认的左内边距 等等。

在不同的浏览器下，元素的默认样式有时候有些差异，这样元素的默认样式就未我们的开发带来了一些问题。

所以，在开发页面之前，我们会选择重置元素的默认样式，这里介绍三种重置方案。

#### 2.1、全局选择器重置样式

```css
* {
    margin: 0;
    padding: 0;
}
```

此种方法，在讲解案例的时候可以简单用一下，但实际开发中是不会用这种方式的，因为 `*` 是选择所有的元素，而并不是所有的元素都有默认样式，改方式效率较低。

#### 2.2、Reset.css重置样式

选择到具有默认样式的元素，清空其默认的样式。

```
/* 基础设置 */
body,h1,h2,h3,h4,h5,h6,hr,p,blockquote,dl,dt,dd,ul,ol,li,pre,form,fieldset,legend,button,input,textarea,th,td{
    margin: 0;
    padding: 0;
}

ul,ol {
    list-style: none;
}

img {
    /* 底部留白 */
    display: block;
  border:0;
}

b,strong {
    font-weight: 400;
}

h1,h2,h3,h4,h5,h6 {
    /* 父元素字号的百分比 */
    font-size: 100%;
}

i,em {
    /* 不倾斜 */
    font-style: normal;
}

u,ins,s,del {
    /* 去掉中划线和下划线 */
    text-decoration: none;
}

table {
    border: 1px solid #999;
    /* 相当于是cellspacing */
    border-spacing: 0;
    /* 1px边框 */
    border-collapse: collapse;
}

td,th {
    border: 1px solid #999;
}

input,button {
    /* 去掉轮廓线 */
    outline: none;
    border:none;
}

/* 风格设置 */
body {
    font: 12px/1.3 "Microsoft YaHei", Tahoma, Helvetica, Arial, "\5b8b\4f53", sans-serif;
    color: #333;
}

a {
    text-decoration: none;
    color: #666;
}

a:hover {
    color:#c00;
    text-decoration: underline;
}

.clearfix::after {
    content: "";
    display: block;
    clear: both;
}

```

各网站都会定义自己的重置样式表，请参考 <http://www.unclealan.cn/index.php/front/174.html>

#### 2.3、Normalize.css重置样式

Normalize.css是一种CSS reset的替代方案。它在默认的HTML元素样式上提供了跨浏览器的高度一致性。相比于传统的CSS reset，Normalize.css是一种现代的、为HTML5准备的优质替代方案。

官网地址：<http://necolas.github.io/normalize.css/>

GitHub: <https://github.com/necolas/normalize.css/>

相对于 Reset.css， Normalize.css 有如下特点：

- 保护有价值的浏览器默认样式而不是完全去掉它们。
- 新增对 HTML5 元素的设置。
- 修复浏览器 BUG 并保证各浏览器的一致性，修复的 BUG 有预格式化文字的 `font-size` 问题、在 IE9 中 SVG 的溢出、许多出现在各浏览器和操作系统中的与表单相关的 BUF 等。
- Normalize.css 对并集选择器的使用比较谨慎，有效避免调试工具杂乱。

### 3、网页的版心

在PC端网页中,一般都会有一个固定宽度且水平居中的盒子,来显示网页的主要内容,这是网页的**版心**。

版心常见的宽度有 1200px、1000px、960px 等等。

![02](.\img\02.png)

## 四、CSS 书写规范

### 1、CSS 书写的几点建议

- 去掉小数点前面的 0，`0.5em →`.5em` 。
- 颜色用小写，用缩写，如：`#fff` 。
- 不要随意使用Id，Id在JS是唯一的，不能多次使用，而使用 class 类选择器却可以重复使用，另外id的优先级优先与class，所以id应该按需使用，而不能滥用。
- 0 不用加单位。
- 尽量缩写，`margin: 5px 10px 5px 10px;` → `margin: 5px 10px;` 。

### 2、CSS 属性书写顺序

相关的属性声明应当归为一组，并按照下面的顺序排列：

- Positioning 定位相关属性
- Box model 盒子模型相关属性
- Typography 文字字体相关属性
- Visual 视觉效果相关属性（背景等）

由于定位（Positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（Box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。

其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面。

```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;


  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;


  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

### 3、Class 命名规则

- 推荐使用小写字母。
- class 名称应当尽可能短，并且意义明确，使用有意义的名称的名称。
- 避免过度任意的简写。`.btn` 代表 *button*，但是 `.s` 不能表达任何意思。
- 允许多个单词组成类型，推荐 kebab-case 命名方式（短横线分隔符），如 `btn-danger`、`col-md-hidden`。
- 基于最近的父元素或基本 class 作为新 class 的前缀，如`news-title`

```css
/* Bad example */
.t { ... }
.red { ... }
.header { ... }

/* Good example */
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

### 4、常见的命名

#### 4.1、常见命名1

| **名称**          | **用途**     |
| ----------------- | ------------ |
| .wrap 或 .wrapper | 用于外侧包裹 |
| .container 或 .ct | 包裹容器     |
| .header           | 用于头部     |
| .body             | 页面 body    |
| .footer           | 页面尾部     |
| .aside、.sidebar  | 用于侧边栏   |
| .content          | 用于主要内容 |
| .nav              | 导航元素     |
| .pagination       | 分页         |

#### 4.2、常见命名 2

| **名称**       | **用途**     |
| ------------ | ---------- |
| .tabs        | tab 切换、选项卡 |
| .breadcrumbs | 导航列表、面包屑   |
| .dropdown    | 下拉菜单       |
| .article     | 文章         |
| .main        | 用于主体       |
| .thumbnail   | 头像、小图像 缩略图 |
| .media       | 媒体资源       |
| .panel       | 面板         |
| .tooltip     | 鼠标放置上去的提示  |
| .popup       | 鼠标点击弹出的提示  |

#### 4.3、常见命名 3

| **名称**              | **用途** |
| ------------------- | ------ |
| .button、.btn        | 按钮     |
| .ad                 | 广告     |
| .subnav             | 二级导航   |
| .menu               | 菜单     |
| .tag                | 标签     |
| .message 或者 .notice | 提示消息   |
| .summary            | 摘要     |
| .logo               | logo   |
| .search             | 搜索框    |
| .login              | 登录     |

#### 4.4、常见命名 4

| **名称**            | **用途** |
| ----------------- | ------ |
| .register         | 注册     |
| .username         | 用户名    |
| .password         | 密码     |
| .banner           | 广告条    |
| .copyright        | 版权     |
| .modal 或者 .dialog | 弹窗     |

#### 4.5、ID 命名规则

- ID 名称应当尽可能短，并且意义明确，使用有意义的名称的名称。
- ID 名称可以由多个单词组成，推荐 camelCase （小驼峰）命名法，如 `#pageHeader`。
- ID 不随意使用，一般页面中明确唯一的地方可以使用 ID 选择器，比如页头、页脚等。