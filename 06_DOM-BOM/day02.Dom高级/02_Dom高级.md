+ 获取dom对象方式
+ 事件类型
+ 节点操作
+ dom的版本

## 一、Dom0/Dom1/Dom2/Dom3

前言：DOM(Document Object Model，文档对象模型)是针对HTML文档和XML(可扩展的标记语言)文档的一个API。DOM描绘了一个层次化的节点树，允许开发人员添加、移出和修改页面的某一部分，DOM脱胎于Netscape及微软公司创始的DHTML（动态HTML）。但现在它已经成为表现和操作页面标记的真正跨平台、语言中立的方式。

Netscape Navigator 4和IE4分别发布于1997年的6月和10月发布的DHTML，由于IE4和Netscape Navigator4分别支持不同的DHTML，为了统一标准，W3C开始制定DOM。1998年10月W3C总结了IE和 Navigator4的规范，制定了DOMLevel 1即DOM1，之前IE与Netscape的规范则被称为DOMLevel 0即DOM0。

+ Dom0
  + div.onclick = function(){}
  + Dom0级事件具有极好的跨浏览器优势，会以最快的速度绑定。
  + 为某一个元素的同一个行为绑定不同的方法在行内会分别执行
  + 为某一个元素的同一个行为绑定不同的方法在script标签中后面的方法会覆盖前面的方法
  + 删除Dom0事件处理程序，只要将对应事件的属性设置为null即可
+ Dom1
  + Dom1一般只有设计规范没有具体实现，企业级应用无
+ Dom2
  + Dom2级事件是通过addEventListener绑定的事件，IE下的Dom2事件通过attachEvent绑定
  + 可以给某个元素的同一个行为绑定不同的方法在行内会分别执行
  + 删除Dom2事件处理程序通过removeEventListener
+ Dom3
  + Dom3级事件在Dom2级事件的基础上添加了更多的事件类型
  + 允许开发人员自定义一些事件

## 二、Dom0事件

+ 绑定

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>04_DOM0-高级浏览器-绑定</title>
        <style>
            div {
                width: 200px;
                height: 200px;
                background-color: skyblue;
            }
        </style>
    </head>
    <body>
        <div id="d1"></div>

        <script>
            var div = document.getElementById('d1');

            div.onclick =function(){
                console.log(111);
            }
        </script>
    </body>
</html>
```

+ dom0高级浏览器中同一个对象 绑定同一个事件

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>05_DOM0-高级浏览器-绑定-同一个对象绑定同一个事件的执行顺序</title>
        <style>
            div {
                width: 100px;
                height: 100px;
                background-color: tomato;
            }
        </style>
    </head>
    <body>
        <div id="d1"></div>

        <script>

            // dom0高级浏览器中同一个对象 绑定同一个事件  那么会覆盖
            var div = document.getElementById('d1');

            div.onclick = function(){
                console.log(111);
            }

            div.onclick = function(){
                console.log(222);
            }
        </script>
    </body>
</html>
```

+ 解绑

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>06_DOM0-高级浏览器-解绑</title>
        <style>
            div {
                width: 100px;
                height: 100px;
                background-color: #666;
            }
        </style>
    </head>
    <body>
        <div></div>
        <button>解绑</button>

        <script>
            var div = document.querySelector('div');

            div.onclick = function(){
                console.log(1111);
            }


            var btn = document.querySelector('button');

            btn.onclick = function(){
                div.onclick = null;
            }
        </script>
    </body>
</html>
```

## 三、Dom2事件

> 前言：dom2事件添加和解绑高低浏览器使用的方法是不同的

+ 绑定方法1

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>10_DOM2-高级浏览器-绑定</title>
        <style>
            div {
                width: 100px;
                height: 100px;
                background-color: black;
            }
        </style>
    </head>
    <body>
        <div></div>

        <script>
            var div = document.querySelector('div');

            // （1）事件类型
            // （2）回调函数
            div.addEventListener('click',function(){
                console.log(1111);
            });
        </script>
    </body>
</html>
```

+ DOM2-高级浏览器-同一个对象绑定同一个事件的执行顺序

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>11_DOM2-高级浏览器-同一个对象绑定同一个事件的执行顺序</title>
        <style>
            div {
                width: 100px;
                height: 100px;
                background-color: aqua;
            }
        </style>
    </head>
    <body>
        <div></div>

        <script>

            // dom2高级浏览器 同一个对象绑定同一个事件的执行顺序是从上到下依次执行的
            var div = document.querySelector('div');

            div.addEventListener('click',function(){
                console.log(111);
            })

            div.addEventListener('click',function(){
                console.log(222);
            })
        </script>
    </body>
</html>
```

+ 绑定方法2

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>12_DOM2-高级浏览器-绑定2</title>

        <style>
            div {
                width: 100px;
                height: 100px;
                background-color: darksalmon;
            }
        </style>
    </head>
    <body>
        <div></div>

        <script>
            var div = document.querySelector('div');

            function f1(){
                console.log(1111);
            }

            div.addEventListener('click',f1);
        </script>
    </body>
</html>
```

+ DOM2-高级浏览器-同一个对象绑定同一个事件的执行顺序

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>12_DOM2-高级浏览器-绑定2</title>

        <style>
            div {
                width: 100px;
                height: 100px;
                background-color: darksalmon;
            }
        </style>
    </head>
    <body>
        <div></div>

        <script>
            var div = document.querySelector('div');

            function f1(){
                console.log(1111);
            }

            div.addEventListener('click',f1);

            function f2(){
                console.log(2222);
            }
            div.addEventListener('click',f2);
        </script>
    </body>
</html>
```

+ 解绑

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>14_DOM2-高级浏览器-解绑</title>
        <style>
            div {
                width: 100px;
                height: 100px;
                background-color: goldenrod;
            }
        </style>
    </head>
    <body>
        <div></div>
        <button>解绑</button>

        <script>
            var div = document.querySelector('div');


            function f1(){
                console.log(11111);
            }
            div.addEventListener('click',f1)

            var btn = document.querySelector('button');
            btn.addEventListener('click',function(){
                // 解绑的代码
                // 参数：（1）事件类型
                //      （2）事件的回调函数
                div.removeEventListener('click',f1)
            })
        </script>
    </body>
</html>
```

## 四、事件流

事件流：发生了事件之后的各个盒子的顺序

+ 捕获事件流（网景）   最终很少用几乎不用
+ 冒泡事件流（ie）        最终我们所用的事件传播都是冒泡
+ 标准DOM事件流      这个是我们现用的标准事件流，里面包含三个阶段： 有捕获  再去获取目标元素   最后冒泡，这个三个阶段当中的捕获和冒泡可以由程序员自己选择。但是通常情况我们都是使用默认 （冒泡）

![事件流](.\img\事件流.png)

### 4.1、Dom0事件的事件流

**注意：Dom0 只有冒泡，没有捕获**

+ 默认事件流

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>21_DOM0事件流-高级浏览器-</title>

        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                border: 10px solid red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                border: 10px solid blue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                border: 10px solid green;
            }
        </style>


    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');

            var laoer = document.querySelector('.laoer');

            var laosan = document.querySelector('.laosan');

            laoda.onclick = function(){
                console.log('laoda');
            }

            laoer.onclick = function(){
                console.log('laoer');
            }

            laosan.onclick = function(){
                console.log('laosan');
            }
        </script>
    </body>
</html>
```

+ 整体事件流

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>22_DOM0事件流-高级浏览器-整体事件流</title>
        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                background-color: red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                background-color: skyblue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                background-color: yellowgreen;
            }
        </style>
    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');
            var laoer = document.querySelector('.laoer');
            var laosan = document.querySelector('.laosan');

            laoda.onclick = function(){
                console.log('laoda');
            }

            laoer.onclick =function(){
                console.log('laoer');
            }

            laosan.onclick = function(){
                console.log('laosan');
            }

            document.body.onclick = function(){
                console.log('body');
            }

            document.documentElement.onclick = function(){
                console.log('html');
            }

            document.onclick = function(){
                console.log('document');
            }

            window.onclick = function(){
                console.log('window');
            }
        </script>
    </body>
</html>
```

+ 取消冒泡事件流

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>21_DOM0事件流-高级浏览器-</title>

        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                border: 10px solid red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                border: 10px solid blue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                border: 10px solid green;
            }
        </style>


    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');

            var laoer = document.querySelector('.laoer');

            var laosan = document.querySelector('.laosan');

            laoda.onclick = function(){
                console.log('laoda');
            }

            laoer.onclick = function(event){
                console.log('laoer');
                event.cancelBubble = true;
            }

            laosan.onclick = function(event){
                console.log('laosan');
                // 方法1
                // event.cancelBubble = true;

                // 方法2
                // event.stopPropagation();

                // 方法3
                event.stopImmediatePropagation();

            }
        </script>
    </body>
</html>
```

### 4.2、Dom2事件的事件流

#### 4.2.1、冒泡事件流

+ 默认事件流

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>28_DOM2事件流-高级浏览器-</title>
        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                background-color: red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                background-color: skyblue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                background-color: yellowgreen;
            }
        </style>
    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');
            var laoer = document.querySelector('.laoer');
            var laosan = document.querySelector('.laosan');

            laoda.addEventListener('click',function(){
                console.log('laoda');
            })

            laoer.addEventListener('click',function(){
                console.log('laoer');
            })

            laosan.addEventListener('click',function(){
                console.log('laosan');
            })
        </script>
    </body>
</html>
```

+ 整体事件流

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>28_DOM2事件流-高级浏览器-</title>
        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                background-color: red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                background-color: skyblue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                background-color: yellowgreen;
            }
        </style>
    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');
            var laoer = document.querySelector('.laoer');
            var laosan = document.querySelector('.laosan');

            laoda.addEventListener('click',function(){
                console.log('laoda');
            })

            laoer.addEventListener('click',function(){
                console.log('laoer');
            })

            laosan.addEventListener('click',function(){
                console.log('laosan');
            })

            document.body.addEventListener('click',function(){
                console.log('body');
            })

            document.documentElement.addEventListener('click',function(){
                console.log('html');
            })

            document.addEventListener('click',function(){
                console.log('document');
            })
        </script>
    </body>
</html>
```

+ 取消冒泡

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>28_DOM2事件流-高级浏览器-</title>
        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                background-color: red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                background-color: skyblue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                background-color: yellowgreen;
            }
        </style>
    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');
            var laoer = document.querySelector('.laoer');
            var laosan = document.querySelector('.laosan');

            laoda.addEventListener('click',function(){
                console.log('laoda');
            })

            laoer.addEventListener('click',function(){
                console.log('laoer');
            })

            laosan.addEventListener('click',function(event){
                console.log('laosan');
                // event.cancelBubble = true;
                // event.stopPropagation();
                event.stopImmediatePropagation();
            })
        </script>
    </body>
</html>
```

#### 4.2.2、捕获事件流

+ 捕获事件流

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>31_DOM2事件流-高级浏览器-捕获事件流</title>
        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                background-color: red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                background-color: skyblue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                background-color: yellowgreen;
            }
        </style>
    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');
            var laoer = document.querySelector('.laoer');
            var laosan = document.querySelector('.laosan');

            laoda.addEventListener('click',function(){
                console.log('laoda');
            },true);

            laoer.addEventListener('click',function(){
                console.log('laoer');
            },true);

            laosan.addEventListener('click',function(){
                console.log('laosan');
            },true);
        </script>
    </body>
</html>
```

+ 整体事件流

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>31_DOM2事件流-高级浏览器-捕获事件流</title>
        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                background-color: red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                background-color: skyblue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                background-color: yellowgreen;
            }
        </style>
    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');
            var laoer = document.querySelector('.laoer');
            var laosan = document.querySelector('.laosan');

            laoda.addEventListener('click',function(){
                console.log('laoda');
            },true);

            laoer.addEventListener('click',function(){
                console.log('laoer');
            },true);

            laosan.addEventListener('click',function(){
                console.log('laosan');
            },true);

            document.body.addEventListener('click',function(){
                console.log('body');
            },true);

            document.documentElement.addEventListener('click',function(){
                console.log('html');
            },true);

            document.addEventListener('click',function(){
                console.log('document');
            },true);
        </script>
    </body>
</html>
```

+ 取消捕获

```html
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="UTF-8" />
        <title>31_DOM2事件流-高级浏览器-捕获事件流</title>
        <style>
            .laoda {
                position: relative;
                width: 500px;
                height: 500px;
                background-color: red;
            }

            .laoer {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                background-color: skyblue;
            }

            .laosan {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%,-50%);
                width: 100px;
                height: 100px;
                background-color: yellowgreen;
            }
        </style>
    </head>
    <body>
        <div class="laoda">
            <div class="laoer">
                <div class="laosan">

                </div>
            </div>
        </div>

        <script>
            var laoda = document.querySelector('.laoda');
            var laoer = document.querySelector('.laoer');
            var laosan = document.querySelector('.laosan');

            laoda.addEventListener('click',function(event){
                console.log('laoda');
                // event.cancelBubble = true;
                // event.stopPropagation();
                event.stopImmediatePropagation();
            },true);

            laoer.addEventListener('click',function(){
                console.log('laoer');
            },true);

            laosan.addEventListener('click',function(){
                console.log('laosan');
            },true);
        </script>
    </body>
</html>
```

<font color='bronze'>总结：dom0事件及低级浏览器的dom2事件（没有第三个参数）都是只有冒泡, 没有捕获，以后我们用的最多的也是冒泡，捕获几乎不用，高级浏览器的dom2事件可以根据第三个参数选择是捕获还是冒泡，一般我们都不写，默认是冒泡</font>

## 五、事件委派

#### 5.1 什么是事件委派

+ 事件委派也叫做事件委托也叫做事件代理

+ 事件委派过程当中依赖了事件冒泡

+ 事件冒泡的好处就是可以进行事件委派

+ **把子元素的事件监听添加给父（祖先）元素，把子元素发生的事件委托给父元素进行处理**

#### 5.2 事件委派用法

+ 什么时候用?
  
  + 当一个元素内部子元素（儿子）很多，并且每个子元素（儿子）都要添加相同的事件的时候，我们可以使用事件委派来提高效率，节省内存
  + 出现新添加的东西，并且新添加的东西要和老的拥有同样的行为；此时我们就想事件委派；不用事件委派，老的身上会有想要的行为，而新添加的没有

+ 用法？
  
  + <font color='blue'>事件委派的做法： 给父元素添加事件监听，不给元素本身添加，事件发生后通过event的target属性去找真正发生事件的目标元素进行处理</font>

+ 好处？
  
  + <font color='blue'>事件委派的好处：可以大大降低内存的占用，并且可以提高效率。</font>

+ 总结
  
  ​    <font color='bronze'>事件委派其实是借用事件冒泡去做的，因为事件冒泡导致内部所有的元素发生事件都会冒泡到祖先身上，我们不在子元素身上去添加事件监听和处理，而是在共同的祖先身上去添加，让祖先去处理子元素发生的事件；祖先去处理其实就是通过事件对象当中的target 去获取到真正发生事件的子元素；对子元素进行处理</font>

+ 事件委派1
  
  + 普通移入变色
  
  ```html
  <!DOCTYPE html>
  <html>
      <head>
          <meta charset="UTF-8">
          <title></title>
      </head>
      <body>
          <ul>
              <li>我是列表项1</li>
              <li>我是列表项2</li>
              <li>我是列表项3</li>
              <li>我是列表项4</li>
              <li>我是列表项5</li>
              <li>我是列表项6</li>
              <li>我是列表项7</li>
              <li>我是列表项8</li>
          </ul>
          <script type="text/javascript">
              window.onload = function() {
                  var liNodes = document.querySelectorAll('li');
                  for (var i = 0; i < liNodes.length; i++) {
                      liNodes[i].onmouseover = function() {
                          this.style.backgroundColor = 'hotpink';
                      };
                      liNodes[i].onmouseout = function() {
                          this.style.backgroundColor = 'white';
                      };
                  }
              }
          </script>
      </body>
  </html>
  ```
  
  + 事件委派变色
  
  ```js
  window.onload = function(){
                  //2、事件委派写法（子元素（儿子）很多）
                  //事件监听添加给共有的父（祖先）元素
                  //事件发生在子元素（儿子）身上的时候，会自动冒泡到父元素（爹）身上
                  //父元素（爹）感受到事件发生后，再回过头去找到发生事件的子元素（儿子）
                  // 进行处理
                  var ulNode = document.querySelector('ul');
                  ulNode.onmouseover = function(e){
                      //找到真正发生事件的儿子     目标元素
                      //目标元素是藏在事件对象当中的
                      //事件对象当中target属性就是发生事件的目标元素
                      // （代表的是最内部的一个）
                      console.log(e);
                      if(e.target.nodeName === 'LI'){//不加if有可能拿到的就是爹
                          //这个判断事件委派一般都会有，为了确保目标元素是我们找到的那个元素
                          e.target.style.backgroundColor = 'hotpink';
                      }
                  };        
                  ulNode.onmouseout = function(e){
                      if(e.target.nodeName === 'LI'){
                          e.target.style.backgroundColor = 'white';
                      }
                  };
              }
  ```
  
  + 移入标签不是最内层标签
  
  ```html
  <!DOCTYPE html>
  <html>
      <head>
          <meta charset="UTF-8">
          <title></title>
      </head>
      <body>
          <ul>
              <li>我是列表项1</li>
              <li>我是列表项2</li>
              <li>我是列表项3</li>
              <li>我是列表项4</li>
              <li>我是列表项5</li>
              <li>我是列表项6</li>
              <li>我是列表项7</li>
              <li><span>我是列表项8</span></li>
          </ul>
  
       <script type="text/javascript">
            window.onload = function(){
                var ulNode = document.querySelector('ul');
                ulNode.onmouseover = function(e){
                    //找到真正发生事件的儿子     目标元素
                    //目标元素是藏在事件对象当中的
                    //事件对象当中target属性就是发生事件的目标元素（代表的是最内部的一个）
                    console.log(e);
                    if(e.target.nodeName === 'LI'){//不加if有可能拿到的就是爹
                        //这个判断事件委派一般都会有，为了确保目标元素是我们找到的那个元素
                        e.target.style.backgroundColor = 'hotpink';
                    }else if(e.target.parentElement.nodeName === 'LI'){
                        e.target.parentElement.style.backgroundColor = 'hotpink';
                    }
  
                };
  
                ulNode.onmouseout = function(e){
                    if(e.target.nodeName === 'LI'){
                        e.target.style.backgroundColor = 'white';
                    }else if(e.target.parentElement.nodeName === 'LI'){
                        e.target.parentElement.style.backgroundColor = 'white';
                    }
                };
            }
        </script>
    </body>
  </html>
  ```

+ 事件委派2
  
  + 普通使用
  
  ```html
  <!DOCTYPE html>
  <html>
      <head>
          <meta charset="UTF-8">
          <title></title>
      </head>
      <body>
          <ul>
              <li>我是列表项1</li>
              <li>我是列表项2</li>
              <li>我是列表项3</li>
              <li>我是列表项4</li>
              <li>我是列表项5</li>
              <li>我是列表项6</li>
              <li>我是列表项7</li>
              <li>我是列表项8</li>
          </ul>
  
          <button>点击添加</button>
  
          <script type="text/javascript">
              window.onload = function(){
                  //本来有一些，然后还可能去动态添加一些新的
                  //老的和新的都要有相同的行为效果
                  //此时就想事件委派
  //                //1、先让原来的li可以移入变色
                  var liNodes = document.querySelectorAll('li');
                  var btn = document.querySelector('button');
                  var ulNode = document.querySelector('ul');
  
                  for(var i = 0; i < liNodes.length; i++){
                      liNodes[i].onmouseover = function(){
                          this.style.backgroundColor = 'hotpink';
                      };
  
                      liNodes[i].onmouseout = function(){
                          this.style.backgroundColor = 'white';
                      };
                  }
  
                  //2、点击按钮添加新的
                  btn.onclick = function(){
                      var liNode = document.createElement('li');
                      liNode.innerHTML = '我是新的';
                      ulNode.appendChild(liNode);
                      liNode.onmouseover = function(){
                          this.style.backgroundColor = 'hotpink';
                      };
                      liNode.onmouseout = function(){
                          this.style.backgroundColor = 'white';
                      };
                  }
              }
          </script>
      </body>
  </html>
  ```
  
  + 事件委派
  
  ```js
          <script type="text/javascript">
              window.onload = function(){
                  //本来有一些，然后还可能去动态添加一些新的
                  //老的和新的都要有相同的行为效果
                  //此时就想事件委派
  //                //1、先让老的可以移入变色
                  var liNodes = document.querySelectorAll('li');
                  var btn = document.querySelector('button');
                  var ulNode = document.querySelector('ul');
                  //事件委派的写法
                  btn.onclick = function(){
                      var liNode = document.createElement('li');
                      liNode.innerHTML = '我是新的';
                      ulNode.appendChild(liNode);
                  }
  
                  ulNode.onmouseover= function(e){
                      if(e.target.nodeName === 'LI'){
                          e.target.style.backgroundColor = 'hotpink';
                      }
                  };
  
                  ulNode.onmouseout = function(e){
                      if(e.target.nodeName === 'LI'){
                          e.target.style.backgroundColor = 'white';
                      }
                  };
              }
          </script>
  ```

## 六、两对移入移出区别

+ onmouseover/onmouseout    如果涉及到事件切换或者冒泡必须使用双o
  
   如果是一个父子元素模型，对父元素添加移入和移出，当鼠标移入父元素里面的子元素的时候，事件会移出然后再移入。也就是说事件元素会有切换；事件委派的时候，必须使用这一对，大部分的时候我们使用的事件流都是冒泡，冒泡一定会涉及到事件的切换；
  
   如果涉及到事件委派 那么就要使用双o 

+ onmouseenter/onmouseleave
  
  如果是一个父子元素模型，对父元素添加移入和移出，当鼠标移入父元素里面的子元素的时候，
  事件并没有移出然后再移入。也就是说事件元素没有切换；

+ **企业级开发中大部分使用的是onmouseenter/onmouseleave 因为不会发生事件切换  不会影响动态效果**
  
   **使用双o在部分浏览器下会发生卡顿现象。如果使用冒泡必须使用双o**

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title></title>
        <style>
            *{
                margin: 0;
                padding: 0;
            }

            #box{
                width: 300px;
                height: 300px;
                background-color: red;
            }
            #box1{
                width: 150px;
                height: 150px;
                background-color: green;
            }
        </style>
    </head>
    <body>
        <div id="box">
            <div id="box1"></div>
        </div>

        <script type="text/javascript">
            window.onload = function(){
                var box = document.getElementById('box');
                //如果从外部元素移入到内部元素有事件切换，可以区分出不同元素的
//                box.onmouseover = function(){
//                    console.log('移入')
//                };
//                
//                box.onmouseout= function(){
//                    console.log('移出')
//                };

                //如果从外部元素移入到内部元素没有事件切换，认为内部元素和外部元素就是同一个
                box.onmouseenter = function(){
                    console.log('移入')
                };

                box.onmouseleave= function(){
                    console.log('移出')
                };
            }
        </script>
    </body>
</html>
```

## 七、案例练习

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title></title>
    </head>
    <body>
        <table>
            <tr>
                <th>姓名</th>
                <th>年龄</th>
                <th>操作</th>
            </tr>
            <tr>
                <td>马一</td>
                <td>18</td>
                <td>
                    <a href="javascript:;">删除</a>
                </td>
            </tr>
            <tr>
                <td>马二</td>
                <td>18</td>
                <td>
                    <a href="javascript:;">删除</a>
                </td>
            </tr>
            <tr>
                <td>马三</td>
                <td>18</td>
                <td>
                    <a href="javascript:;">删除</a>
                </td>
            </tr>
        </table>

        <input type="text" placeholder="请输入学生姓名"/> <br />
        <input type="text" placeholder="请输入学生年龄"/> <br />
        <input type="button" value="确认添加"/>


        <script type="text/javascript">
            window.onload = function(){
                //先搞添加
                //获取按钮，添加点击事件
                var inputNodes = document.querySelectorAll('input');
                var tbodyNode = document.querySelector('tbody');
                inputNodes[2].onclick = function(){
                    var username = inputNodes[0].value;
                    var age = inputNodes[1].value;

                    if(username.trim()&&age.trim()){
                        //username和age拿到的都不是空串或者空白串
                        var trNode = document.createElement('tr');
                        //往tr当中加入td是学生名字
                        var tdUsername = document.createElement('td');
                        tdUsername.innerHTML = username;
                        trNode.appendChild(tdUsername);
                        //往tr当中加入td是学生年龄
                        var tdAge = document.createElement('td');
                        tdAge.innerHTML = age;
                        trNode.appendChild(tdAge);
                        //往tr当中加入td是删除操作
                        var tdOperate = document.createElement('td');
                        tdOperate.innerHTML = '<a href="javascript:;">删除</a>';
                        trNode.appendChild(tdOperate);
                        //把tr放到table当中，但是切记tr的爹是tbody
                        tbodyNode.appendChild(trNode);
                    }else{
                        alert('学生姓名或年龄不能为空')

                    }
                    inputNodes[0].value = '';
                    inputNodes[1].value = '';

                }

                //再搞删除
                tbodyNode.onclick = function(event){
                    event = event || window.event;
                    var target = event.target || event.srcElement;
                    if(target.nodeName === 'A'){
                        //点的是哪个a，就把和这个a相关的tr给删除
                        tbodyNode.removeChild(target.parentNode.parentNode); 
                    } 
                }
            }
        </script>
    </body>
</html>
```
