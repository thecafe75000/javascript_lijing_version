## 一、querySelect和getXXXByXXX区别

> getXXXByXXX 获取的是动态集合，querySelector获取的是静态集合。
> 
> 简单的说就是，动态就是选出的元素会随文档改变，静态的不会，取出来之后就和文档的改变无关了。

```js
<ul>
    <li>1111</li>
    <li>2222</li>
    <li>3333</li>
</ul>

//demo1
var ul = document.getElementsByTagName('ul')[0];
var li_list = ul.getElementsByTagName("li");
for(var i = 0; i < 3 ; i++){
     ul.appendChild(document.createElement("li"));
}
console.log(li_list.length);  //6

//demo2
var ul = document.querySelector('ul');
var li_list = ul.querySelectorAll("li");
for(var i = 0; i < 3 ; i++){
     ul.appendChild(document.createElement("li"));
}
console.log( li_list.length);  //3
```

## 二、bind方法

bind() 函数会创建一个新函数（称为绑定函数）

- bind是ES5新增的一个方法
- 传参和call类似
- 不会执行对应的函数，call或apply会自动执行对应的函数
- 返回对函数的引用
- 语法 `fun.bind(thisArg[, arg1[, arg2[, ...]]])`

```js
var obj = {
            name: "阿马"
}
function add(a, b) {
     console.log(this);
     console.log(a + b)
}
var new = add.bind(obj, 1, 2)
console.log(new);
new();
//返回的不是同一个函数
console.log(new === add); 
```

## 三、JS终极原型链

![终极原型链原理图](.\img\终极原型链原理图.png)

## 四、面向对象

面向对象三大特性：封装继承多态

+ 原型继承
  + 让父类的实例作为子类的原型，将子类的原型构造器补充完整 （为了让子类继承方法）

```js
<script type="text/javascript">
            //父类
            function Dog(name,age){
                this.name = name;
                this.age = age;
            }

            //子类
            function Teddy(name,age){
                this.name = name;
                this.age = age;
            }

            Dog.prototype.run = function(){
                console.log('跑的很快~');
            }
            //为了让子类去继承父类原型当中的方法
            //我们需要用到原型继承，原型继承主要就是为了让子类继承方法使用的
            //让子类的原型变成父类的一个实例
            Teddy.prototype = new Dog();
            // 手动给原型对象添加一个构造器，因为原型对象里面都是有构造器的，指向和自己匹配的构造函数
            Teddy.prototype.constructor = Teddy;

            var d1 = new Dog('旺财',3);
            d1.run();

            var t1 = new Teddy('小黑',2);
            t1.run(10);
</script>
```

+ 借用构造函数继承
  + 在子类当中去调用父类的构造函数（为了让子类继承属性）

```js
<script type="text/javascript">
            //父类
            function Dog(name,age){
                this.name = name;
                this.age = age;
            }

            //子类
            function Teddy(name,age){
//                this.name = name;
//                this.age = age;
                //借助父类的构造函数实现属性的继承
                Dog.call(this,name,age);
            }


            var d1 = new Dog('旺财',3);
            d1.run();

            var t1 = new Teddy('小黑',2);
            t1.run(10);

            console.log(t1);    
        </script>
```

+ 组合继承
  + 原型继承方法，借用构造函数继承属性一起使用

```js
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title></title>
    </head>
    <body>
        <script type="text/javascript">
            //父类
            function Dog(name,age){
                this.name = name;
                this.age = age;
            }

            //子类
            function Teddy(name,age){
//                this.name = name;
//                this.age = age;
                //借助父类的构造函数实现属性的继承
                Dog.call(this,name,age);
            }

            Dog.prototype.run = function(){
                console.log('跑的很快~');
            }

            //为了让子类去继承父类原型当中的方法
            //我们需要用到原型继承，原型继承主要就是为了让子类继承方法使用的
            //让子类的原型变成父类的一个实例
            //手动给原型对象添加一个构造器，因为原型对象里面都是有构造器的，指向和自己匹配的构造函数
            Teddy.prototype = new Dog();
            Teddy.prototype.constructor = Teddy;


            //方法重写和方法重载   是多态的两个表现形式
            //方法重写；和父类同名方法功能不同，被称作方法重写
            Teddy.prototype.run = function(flag){
                //方法重载
                if(typeof flag === 'number'){
                    console.log('跑的很慢~');
                }else{
                    console.log('跑的很快~');
                }
            }


            var d1 = new Dog('旺财',3);
            d1.run();

            var t1 = new Teddy('小黑',2);
            t1.run(10);

            console.log(t1);

        </script>
    </body>
</html>
```

## 五、Web Workers

- H5规范提供了js分线程的实现, 取名为: Web Workers

- 相关API
  
  - Worker: 构造函数, 加载分线程执行的js文件
  
  - Worker.prototype.onmessage: 用于接收另一个线程的回调函数
  
  - Worker.prototype.postMessage: 向另一个线程发送消息
  
  - 每个线程可以向不同线程发送消息  也可以接收不同线程传来的消息
  
  - 主线程操作
    
    - 发送消息：   worker.postMessage(消息可以是任何数据)
    
    - 接受消息：   worker.onmessage = function(e){
      
      ​                console.log(e.data)//接收到的消息或者数据在事件对象的data属性当中
      
      ​            }
  
  - 子线程操作
    
    - 发送消息：   worker.postMessage(消息可以是任何数据)
    
    - 接受消息：   worker.onmessage = function(e){
      
      ​                console.log(e.data)//接收到的消息或者数据在事件对象的data属性当中
      
      ​            }

- 不足
  
  - worker内代码不能操作DOM
  - 不能跨域加载JS
  - 不是每个浏览器都支持这个新特性

- 计算得到fibonacci数列中第n个数的值
  
  - 在主线程计算: 当位数较大时, 会阻塞主线程, 导致界面卡死
  
  ```js
  function fib(n){
      if(n <= 2){
          return 1;
      }
      return fib(n- 1) + fib(n - 2);
  }
  ```
  
  - 在分线程计算: 不会阻塞主线程
    
    - js代码-myThread.js
    
    ```js
    function fib(n){
        if(n <= 2){
            return 1;
        }
        return fib(n- 1) + fib(n - 2);
    }
    ```

    self.onmessage = function(e){
        e = e || window.event;
    //    console.log(e.data);//就 可以拿到主线程给我 发过来的消息内容
    
        var result = fib(e.data);
        self.postMessage(result);//分线程接受到主线程的消息，然后开始计算，把计算后的记过发消息再给主线程
    }
    
    ```
    
    - html代码

```js
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title></title>
    </head>
    <body>
        <script type="text/javascript">
            //第一步：实例化一个对象，初始化主线程和分线程关联对象


            var worker = new Worker('./myThread.js');

            worker.postMessage(100);//主线程发送消息给分线程,消息内容可以是任意类型

            worker.onmessage = function(e){
                e = e || window.event;
                //等待接受分线程计算完的结果
                console.log(e.data);
            }

            console.log('大哥 js Ending~');

        </script>
    </body>
</html>
```

## 六、浅拷贝

> 浅拷贝是指，一个新的对象对原始对象的属性值进行精确地拷贝，
> 
> 如果拷贝的是基本数据类型，拷贝的就是基本数据类型的值；
> 
> 如果拷贝的是引用数据类型，拷贝的就是内存地址。

+ 基本使用

```js
        var person = {
            name: '马志强',
            age: 18,
            eat: function () {
                console.log('麻婆豆腐');
            },
            hobby: ['吃', '喝']
        }

        console.log(person);

        function lightCopy() {
            var newPerson = {};
            for (var key in person) {
                newPerson[key] = person[key];
            }
            return newPerson;
        }

        var person2 = lightCopy();
        console.log(person2);

        console.log(person === person2);
        console.log(person.name === person2.name);
        console.log(person.age === person2.age);
        console.log(person.eat === person2.eat);
        console.log(person.hobby === person2.hobby);
```

+ 当person对象的属性值为基本类型时，修改person的属性值，不会影响person2的属性值

```js
        person.name = '阿马';
        person.age = 45;

        console.log(person.name);
        console.log(person.age);

        console.log(person2.name);
        console.log(person2.age);
```

+ 当person对象的属性值为引用类型时， 修改person的属性值，会影响person2的属性值

```js
        person.eat.abc = 123;
        person.hobby.push('嫖');

        console.log(person.eat.abc);
        console.log(person.hobby);

        console.log(person2.eat.abc);
        console.log(person2.hobby);
```

> 所有的浅拷贝都只能拷贝一层对象。如果存在对象的嵌套，那么浅拷贝就无能为力了

## 七、深拷贝

> 深拷贝是指：
> 
> 对于简单数据类型直接拷贝他的值
> 
> 对于引用数据类型，在堆内存中开辟一块内存用于存放复制的对象，并把原有的对象类型数据拷贝过来，这两个对象相互独立，属于两个不同的内存地址，修改其中一个，另一个不会发生改变。

+ JSON.parse(JSON.stringify(xxx))；

```js
        var obj1 = {
            name: '马志强',
            age: 35,
            sex: true,
            und: undefined,
            abc: null,
            reg: /^[a-z]\w{5,7}$/,
            friends: ['李四', '王五', function () { console.log(111) }, { a: 123 }],
            say: function () {
                console.log('hello child')
            },
            father: {
                name: '老张',
                age: 44,
                sex: true,
                und: undefined,
                abc: null,
                reg: /^[a-z]\w{5,7}$/,
                friends: ['老李', '老王', function () { console.log(222) }, { a: 456 }],
                say: function () {
                    console.log('hello father')
                }
            }
        }

        // JSON.parse的问题：
        // 不可以拷贝 undefined、function、正则 等类型
        // 这种方法能正确处理的对象只有 Number, String, Boolean, Array, 扁平对象
        var obj2 = JSON.parse(JSON.stringify(obj1))
        console.log( obj1 );
        console.log( obj2 );
```

> JSON.parse的问题：
> 不可以拷贝 undefined、function、正则 等类型

+ 简单深拷贝

```js
function deepCopy2(target){
    var result = {}
    for (var key in target){
        result[key] = typeof target[key] === 'object' ? deepCopy2(target[key]) : target[key]
    }
    return result
}
var obj3 = deepCopy2(obj1)
console.log( obj1 )
console.log( obj3 )
```

> 简单深拷贝的问题：
> 不可以拷贝 数组、正则、null 会被拷贝为{}对象

+ 复杂深拷贝

```js
function deepCopy(target){
    var result;
    if (typeof target === 'object') {
        // console.log( '对象、数组、正则、null' )
        if (target instanceof Array) {
            // console.log( '数组' )
            result = [] // 将result赋值为一个数组，并且执行遍历
            for (var i in target) {
                // 递归克隆数组中的每一项
                result.push(deepCopy(target[i]))
            }
        }
        else if (target === null){
            // console.log( 'null' )
            result = null
        }
        else if (target.constructor === RegExp){
            // console.log( '正则' )
            result = target
        }
        else {
            // console.log( '普通对象' )
            result = {}
            for (var key in target){
                // 递归克隆对象中的每一项
                result[key] = deepCopy(target[key])
            }
        }
    } else {
        // console.log( '函数' )
        result = target
    }
    // 返回最终结果
    return result
}

var obj4 = deepCopy(obj1)
console.log( obj1 )
console.log( obj4 )
```

> 复杂深拷贝的问题：通常数组和对象需要深拷贝，函数和正则浅拷贝即可

+ lodash.js

```js
// lodash很热门的函数库，提供了 _.cloneDeep()实现深拷贝
var obj5 = _.cloneDeep(obj1)
console.log( obj1 )
console.log( obj5 )
```

## 八、防抖节流前瞻

> 高频触发事件
> 
> 特征：短时间内执行多次事件处理函数
> 
> document.onmousemove = function (){
> 
> console.log( 'onmousemove' );
> 
> }
> 
> document.onmousewheel = function (){
> 
> console.log( 'onmousewheel' );
> 
> }
> 
> txt.onkeyup = function (){
> 
> console.log( 'onkeyup' );
> 
> }
> 
> txt.onkeydown = function (){
> 
> console.log( 'onkeydown' );
> 
> }
> 
> window.onscroll = function (){
> 
> console.log( 'onscroll' );
> 
> }
> 
> window.onresize = function (){
> 
> console.log( 'onresize' );
> 
> }

## 九、防抖

> 生活中案例：
> 
> - 比如你现在使用的电脑，在不使用后一段时间睡眠
> - 当你再次使用的时候重新激活，并开始你设置的时间倒计时`5`分钟
> - 在这`5`分钟内你继续使用电脑又会重新开始倒计时`5`分钟
> - 当你最后一次使用电脑并离开时重新倒计时`5`分钟过去了，电脑就休眠了
> 
> 总结：
> 
> ​         在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时。

+ 基本使用

```js
        var div = document.querySelector('div');

        div.addEventListener('mousemove',function(){
            div.innerHTML++;
        })
```

+ 需要对执行的事件进行处理所以接下来我们需要封装一下函数

```js
        var div = document.querySelector('div');

        function move(){
            div.innerHTML++
        }

        function debounce(fun){
            return function(){
                fun();
            }
        }

        div.addEventListener('mousemove',debounce(move));
```

+ 我们用闭包处理了一下函数，接下来我们需要添加一个延时器来倒计时

```js
        var div = document.querySelector('div');

        function move(){
            div.innerHTML++
        }

        function debounce(fun){
            return function(){
                setTimeout(function(){
                    fun();
                },2000)
            }
        }

        div.addEventListener('mousemove',debounce(move));
```

+ 每次移动都会新增一个1 而且并不能达到我们多次移动只执行一次的效果
  
  需要在我们移动后也就是执行时要先把之前的先清除再重新计时

```js
        var div = document.querySelector('div');

        function move(){
            div.innerHTML++
        }

        function debounce(fun){
            var timer = null;
            return function(){
                clearTimeout(timer)
                timer = setTimeout(function(){
                    fun();
                },2000)
            }
        }
        div.addEventListener('mousemove',debounce(move));
```

+ lodash.js

```js
        var div = document.querySelector('div');

        function move(){
            div.innerHTML++
        }

        div.addEventListener('mousemove',_.debounce(move,2000));
```

## 十、节流

> 规定在一个单位时间内，只能触发一次函数。如果这个单位时间内触发多次函数，只有一次生效。
> 
> 节流的应用场景也比较广泛，例如在用户滚动页面时，可以使用节流来避免频繁地触发函数。

+ 基本使用

```js
        function testScroll() {
            console.log('翻滚吧,马志强')
        }
        document.addEventListener('scroll', testScroll)
```

+ 封装一个节流函数，跟防抖一样我们也需要利用闭包

```js
         function testScroll() {
                    console.log('翻滚吧,马志强')
         }
         function throttle(fun,time){
              return function(){
                fun()
              }
            }
         document.addEventListener('scroll',throttle(testScroll,3000))
```

+ 两次鼠标滚动的时间间隔未到所设置的时间则不执行

```js
        function testScroll() {
            console.log('翻滚吧,马志强')
        }

        function throttle(fun, time) {
            var t1 = 0 //初始时间
            return function () {
                var t2 = new Date() //当前时间
                if (t2 - t1 > time) {
                    fun();
                    t1 = t2;
                }
            }
        }
        document.addEventListener('scroll', throttle(testScroll, 3000));
```

+ lodash.js

```js
        function testScroll() {
            console.log('翻滚吧,马志强')
        }

        document.addEventListener('scroll', _.throttle(testScroll,3000));
```

> **马志强疯狂的点击一个某一个按钮**，如果使用了**防抖**则会只执行**一次**，而你使用了
> 
> **节流**则会每隔一段时间执行**一次**

## 十一、面试题

面试题1：属性的赋值优先级比变量高（连等的情况下）

```js
var a = {n:1};
var b = a;
a.x = a = {n:2};
console.log(a.x);
console.log(b.x);
```

面试题2：

```js
var b1 = {
                b2:[2,'atguigu',console.log],
                b3:function () {
                      alert('hello')
                }
          }
console.log(b1,b1.b2,b1.b3)
console.log(b1 instanceof Object,typeof b1)
console.log(b1.b2 instanceof Array,typeof b1.b2)
console.log(b1.b3 instanceof Function,typeof b1.b3)
console.log(typeof b1.b2[2])
console.log(typeof b1.b2[2]('atguigu'))
```

面试题3：

```js
var a = {};
var obj1 = {
    m: 2
}
var obj2 = {
    n: 2
}
var obj3 = function() {};

a[obj1] = 4
a[obj2] = 5
a.name = 'kobe'
a[obj3] = 6;

console.log(a[obj1])
console.log(a)
```
