# Html5

## 浏览器内核

浏览器内核又可以分成两部分：渲染引擎（layout engineer 或者 Render Engine）和 JS 引擎。

渲染引擎 它负责取得网页的内容（HTML、XML、图像等）、整理讯息（例如加入 CSS 等），以及计算网页的显示方式。然后会输出至显示器或打印机。浏览器的 JS 引擎则是解析 JavaScript 语言。执行 JavaScript 语言来实现网页的动态效果。

最开始渲染引擎和 JS 引擎并没有区分的很明确。后来 JS 引擎越来越独立，内核就倾向于只渲染引擎。

（1）Trident（IE 内核）

​	Window10 发布后，IE 将其内置浏览器命名为 Edge，Edge 最显著的特点就是新内核 EdgeHTML。

（2）Gecko（firefox）

（3）webkit（Safari）

（4）Chromium/Bink（chrome）

## Web 标准

### 好处

1. 让 Web 的发展前景更广阔
2. 内容能被广泛的设备访问
3. 更容易被搜索引擎搜索
4. 降低网站流量费用
5. 使网站更易于维护
6. 提高页面浏览速度

### 构成

> Web 标准不是某一个标准，而是由 W3C 和 其他标准化组织指定的一系列标准的集合。主要包括结构（Structure）、表现（Presentation）和行为（Behavior）三个方面

<font color='crimson'>结构标准：</font>结构用于对网页元素进行整理和分类，主要包括 XML 和 XHTML 两个部分

<font color='crimson'>样式标准：</font>表现用于设置网页元素的版式、颜色、大小等外观样式，主要指的是 CSS

<font color='crimson'>行为标准：</font>行为是指网页模型的定义及交互的编写，主要包括 DOM 和 ECMAScript 两个部分

## HTML 骨架格式

```html
<html>
    <head>
        <title></title>
    </head>
    <body>
    </body>
</html>
```

1. html 标签：作用所有 html 中标签的一个根标签
2. head 标签：用于存放 title、meta、base、style、script、link，注意在 head 标签中我们必须要设置的标签是 title
3. title 标签：页面的标题
4. body 标签：页面的主体部分，用于存放所有的 html 标签

## 文档类型<!DOCTYPE>

```html
<!DOCTYPE html>
```

这句话就是告诉我们使用的是哪个 html 版本？html 有很多版本，那我们应该告诉用户和浏览器我们使用的版本号。

\<!DOCTYPE> 标签位于文档的最前面，用于向浏览器说明当前文档使用哪种 HTML 和 XHTML 标准规范，必需在开头处使用 <!DOCTYPE> 标签为所有的 XHTML 文档指定 XHTML 版本和类型，只有这样浏览器才能按指定的文档类型进行解析。

## 字符集

```html
<meta charset="UTF-8">
```

utf-8 是目前最常用的字符集编码方式，常用的字符集编码方式还有 gdk 和 gb2313

gb2313 简单中文，包括 6763 个汉字

BIGS 繁体中文，港澳台等使用

GBK 包含全部中文字符，是 GB2313 的扩展，加入对繁体字的支持，兼容 GB2313

UTF-8 则包含全世界所有国家需要用到的字符

## 锚点定位（难点）

通过创建描点连接，用户能够快速定位到目标内容。

创建锚点连接分两步：

```html
1. 使用 <a href="#id名">链接文本</a> 创建链接文本
2. 使用响应的 id 名标注跳转目标的位置
```

例如：

```html
<a href="#live">个人生活</a>
<h3 id="live">个人生活</h3>
<hr/>
.... <!-- 一长串内容 -->
```

## base 标签

base 可以设置整体链接的打开状态

例如，原本的 \<a> 标签如下所示：

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        <a href="http://www.baidu.com" target="_blank">百度</a>
        <a href="http://www.sina.com" target="_blank">新浪</a>
        <a href="http://www.sohu.com" target="_blank">搜狐</a>
        <a href="http://www.163.com" target="_blank">网易</a>
    </body>
</html>
```

修改如下：

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
        <base target="_blank"/>
    </head>
    <body>
        <a href="http://www.baidu.com">百度</a>
        <a href="http://www.sina.com">新浪</a>
        <a href="http://www.sohu.com">搜狐</a>
        <a href="http://www.163.com">网易</a>
    </body>
</html>
```

# ES6

> ES 全称 EcmaScript，是脚本语言的规范，而平时经常编写的 JavaScript 是 EcmaScript 的一种实现，所以 ES 新特性其实就是指的是 JavaScript 的新特性

## 变量的解构赋值

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6 允许按照一定模式从数组和对象中提取值，对变量进行赋值
            // 这被称为解构赋值
            // 1. 数组的解构
            const F4 = ['小沈阳', '刘能', '赵四', '宋小宝'];
            let [xiao, liu, zhao, song] = F4;
            console.log(xiao); // 小沈阳
            console.log(liu); // 刘能
            console.log(zhao); // 赵四
            console.log(song); // 宋小宝

            // 2. 对象的解构
            const zhao = {
                name: '赵本山',
                age: '不详',
                xiaopin: function() {
                    console.log("我可以演小品");
                }
            };

            let {name, age, xiaopin} = zhao;
        </script>
    </body>
</html>
```

## 模板字符串 ``

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        <script>
            // ES6 引入新的字符串方式 `` '' ""
            // 1. 声明
            let str1 = `我也是一个字符串`;
            console.log(str, typeof str);

            // 2. 内容可以直接出现换行符
            let str2 = `<ul>
                        <li>沈腾</li>
                        <li>玛丽</li>
                        <li>魏翔</li>
                        <li>艾伦</li>
                        </ul>`;

            // 3. 变量拼接
            let lovest = '魏翔';
            // let str3 = 'xxx 是我心目中最搞笑的演员！！';
            let str3 = `${lovest} 是我心目中最搞笑的演员！！`;
        </script>
    </body>
</html>
```

## 对象简化写法

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6 引入新的字符串方式 `` '' ""
            let name = '尚硅谷';
            let change = () => {
                console.log('我们可以改变你们！');
            };

            const school = {
                name,
                change,
            }
            // 等价于以下写法
            // const school = {
            //     name: name,
            //     change: change,
            //  }
        </script>
    </body>
</html>
```

## 函数参数的默认值

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6 引入新的字符串方式 `` '' ""
            function add(a, b, c = 10) {
                return a + b + c;
            }
            let result = add(1, 2);
            console.log(result);
        </script>
    </body>
</html>
```

## rest 参数 代替 arguments

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6 引入新的字符串方式 `` '' ""
            // ES5 获取实参
            // function date() {
            // 	console.log(arguments);
            // }
            // date('白芷', '阿胶', '思慧');

            // rest 参数
            function date(...args) {
                console.log(args);
            }
            date('白芷', '阿胶', '思慧');
        </script>
    </body>
</html>
```

## ... 扩展运算符

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6 引入新的字符串方式 `` '' ""
            const tfboys = ['易烊千玺', '王源', '王俊凯'];

            // 声明一个函数
            function chunwan() {
                console.log(arguments);
            }

            chunwan(...tfboys);
        </script>
    </body>
</html>
```

## Symbol

> ES6 引入了一种新的原始类型 Symbol，表示独一无二的值，它是 JavaScript 语言中的第七种数据类型，类似于字符串的数据类型

### 特点

1. Symbol 的值是唯一的，用来解决**命名冲突**问题（名字相同，用 Symbol 包装后，即可以在一个 Script 中）
2. Symbol 的值不能与其他数据进行运算
3. Symbol 定义的对象属性不能使用 for...in 循环遍历，但是可以使用 Reflect.ownKeys 来获取对象的所有键名

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6 引入新的字符串方式 `` '' ""
            let s = Symbol();
            console.log(s, typeof s);

            let s2 = Symbol('尚硅谷');
            let s3 = Symbol('尚硅谷');

            console.log(s2 === s3); // false

            // Symbol.for 创建
            let s4 = Symbol.for('尚硅谷');
            let s5 = Symbol.for('尚硅谷');
            console.log(s4 === s5); // true
        </script>
    </body>
</html>
```

### 对象添加 Symbol 属性

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        <script>
            // ES6 引入新的字符串方式 `` '' ""
            let game = {
                name: "俄罗斯方块",
                up: () => {
                    console.log("上");
                },
                down: () => {
                    console.log("下");
                }
            };

            // 声明一个对象
            let methods = {
                up: Symbol(),
                down: Symbol()
            };

            game[methods.up] = function() {
                console.log("我可以改变形状");
            };

            game[methods.down] = function() {
                console.log("我可以快速下降")；
            }

            console.log(game);

            // 另一种声明方式
            let youxi = {
                name: "狼人杀",
                [Symbol('say')]: () => {
                    console.log(“我可以发言");
                },
                [Symbol('zibao')]: () => {
                    console.log("我可以自爆");
                }
            }
        </script>
    </body>
</html>
```

### Symbol 11 个内置值

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        <script>
            // ES6
            class Person {
                static [Symbol.hasInstance](param) {
                    console.log(param);
                    console.log(“我被用来检测类型了");
                }
            };

            let o = {};

            console.log(o instanceof Person); // 自己控制类型检测

            // isConcatSpreadable 控制数组是否可以展开
            const arr = [1, 2, 3];
            const arr2 = [4, 5, 6];
            arr2[Symbol.isConcatSpreadable] = false;
            console.log(arr.concat(arr2));
        </script>
    </body>
</html>
```

## 迭代器

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6
            cosnt xiyou = ['唐僧', '孙悟空', '猪八戒', '沙僧'];

            // for...in
            for (let v in xiyou) {
                console.log(v); // 0 1 2 3
            }

            for (let v of xiyou) {
                console.log(v); // 唐僧 孙悟空 猪八戒 沙僧
            }

            // 获取迭代器
            let iterator = xiyou[Symbol.iterator]();
            console.log(iterator);
        </script>
    </body>
</html>
```

### 自定义遍历数据

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6
            const banji = {
                name: "终极一班",
                stus: [
                    'xiaoming',
                    'xiaoning',
                    'xiaotian',
                    'knight'
                ],
                // !!
                [Symbol.iterator]() {
                    // 索引
                    let index = 0;
                    //
                    let _this = this;
                    return {
                        next: () => {
                            if (index < _this.stus.length) {
                                const result = {value: _this.stus[index], done: false};
                                // 下标自增
                                index++;
                                // 返回
                                return result;
                            } else {
                                return {value: undefined, done: true};
                            }
                        }
                    };
                }
            };

            // 遍历这个对象
            for (let v of banji) {
                console.log(v);
            };
        </script>
    </body>
</html>
```

## 生成器

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6
            // 生成器其实就是一个特殊的函数
            // 异步编程 纯回调函数 node fs ajax mongodb
            function * gen() {
                console.log(111);
                yield '一只没有耳朵'; // yield 可以看做程序代码块的分隔符
                console.log(222);
                yield '一直没有尾巴';
                console.log(333);
                yield '真奇怪';
                console.log(444);
            }
            
            let iterator = gen();
            iterator.next();
            iterator.next();
            iterator.next();
            iterator.next();
            
            // 遍历
            for (let v of gen()) { // 输出 yield 后面的值
                console.log(v); // 一只没有耳朵 一直没有尾巴 真奇怪
            }
        </script>
    </body>
</html>
```

### 生成器函数传参

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6
            // 生成器其实就是一个特殊的函数
            // 异步编程 纯回调函数 node fs ajax mongodb
            function * gen(arg) {
                console.log(arg);
                let one = yield 111; // yield 可以看做程序代码块的分隔符
                console.log(one);
                let two = yield 222;
                console.log(two);
                let three = yield 333;
                console.log(three);
            }
            
            let iterator = gen('AAA');
            console.log(iterator.next());
            iterator.next('BBB');
            iterator.next('CCC');
            iterator.next('DDD');
        </script>
    </body>
</html>
```

### 生成器函数解决回调地狱问题

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6
            // 1s后输出 111 2s后输出 222 3s后输出333
            // 回调地狱
            setTimeout(() => {
                console.log(111);
                setTimeout(() => {
                    console.log(222);
                    setTimeout(() => {
                        console.log(333);
                    }, 3000);
                }, 2000);
            }, 1000);
            
            // 生成器方式
            function one() {
                setTimeout(() => {
                    console.log(111);
                    iterator.next();
                }, 1000);
            }
            
            function two() {
                setTimeout(() => {
                    console.log(222);
                    iterator.next();
                }, 2000);
            }
            
            function three() {
                setTime(() => {
                    console.log(333);
                    iterator.next();
                }, 3000);
            }
            
            function * gen() {
                yield one();
                yield two();
                yield three();
            }
            
            // 调用生成器函数
            let iterator = gen();
            iterator.next();
        </script>
    </body>
</html>
```

## Promise ！！

> Promise 是 ES6 引入的异步编程的新解决方案。语法上 Promise 是一个构造函数，用来封装异步操作并可以获取成功或失败的结果

**<font color='crimson'>Promise 有三个状态：初始化、成功、失败</font>**

1. Promise 构造函数: Promise(excutor) {}
2. Promise.prototype.then 方法
3. Promise.prototype.catch 方法

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6
            // 实例化 Promise 对象（三个状态：初始化、成功、失败）
            const p = new Primse(function(resolve, reject) {
                setTimeout(function() {
                    // 数据读取，文件读取等 io 操作
                    let data = '数据库中的用户数据';
                    // 调用 resolve 或者 reject 函数，可以改变我们这个 Promise 对象的一个状态
                    // resolve => 对象状态就会变成成功
                    // resolve(data);
                    
                    // 发生错误
                    let err = '数据读取失败';
                    reject(err);
                }, 1000);
            });
            
            // 调用 promise 的 then 方法
            // 如果 promise 对象里面调用了 resolve 方法，就会执行第一个回调函数里面的方法
            // 否则则失败，就会调用第二个回调函数里面的方法
            p.then(function(value) { // 成功的形参
                console.log(value);
            }, function(reason) { // 失败的形参
                console.error(reason);
            })
        </script>
    </body>
</html>
```

### catch

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6
            // 实例化 Promise 对象（三个状态：初始化、成功、失败）
            const p = new Primse((resolve, reject) => {
                setTime(() => {
                    // 设置 p 对象状态为失败，并设置失败的值
                    reject("出错啦！！");
                }, 1000);
            });
            
            // p.then(value => {}, reason => {
            //     console.error(reason);
            // })
            
            p.catch(reason => { // 只是一个语法糖
                console.warn(reason);
            })
        </script>
    </body>
</html>
```

## get set

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script>
            // ES6
          	// get 和 set
            class Phone {
                get price() {
                    console.log("价格属性被读取了");
                    return "iloveyou";
                }
                
                set price(newVal) {
                    console.log("价格属性杯修改了");
                }
            }
            
            // 实例化对象
            let s = new Phone();
            
            // console.log(s.price);
            s.price = 'free';
        </script>
    </body>
</html>
```

## 模块化

模块功能主要由两个命令构成：export 和 import

- export 命令用于规定模块的对外接口
- import 命令用来输入其他模块提供的功能

### 基本使用

```js
// 分别暴露
export let school = '尚硅谷';

export function teach() {
    console.log("我们可以教给你开发技能");
}
```

```js
// 统一暴露
let school = '尚硅谷';

function findJob() {
    console.log("我们可以教给你开发技能");
}

export {school, teach}
```

```js
// 默认暴露
export default {
    school: 'ATGUIGU',
    change: function() {
        console.log("我们可以改变你！");
    }
}
```

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script type="module">
            // 引入 m1.js 模块内容
            // import * as m1 from ./src/js/m1.js; // 全部导入
            // console.log(m1);
            
            // 解构赋值
            // import {school, teach} from ./src/js/m1.js;
            // import {school as guigu, findJob} from ./src/js/m2.js;
            // import {default as m3} from ./src/js/m3.js
            
            // 简便形式 针对于默认暴露
            import m3 from "./src/js/m3.js";
            console.log(m3);
        </script>
    </body>
</html>
```

### 入口文件形式

```html
<script src="./src/js/app.js" type="module"></script>
```

```js
import * as m1 from './src/js/m1.js';
import * as m2 from './src/js/m2.js';
import * as m3 from './src/js/m3.js';
```

## babel

### 安装

```
npm i babel-cli babel-preset-env browserify -D
```

### 执行 babel

```
npx babel src/js -d dist/js --persets=babel-perset-env
```

### 打包

```
npx browserify dist/js/app.js -o dist/bundle.js
```

## ES8 async 和 await！！

async 和 await 两种语法结合可以让异步代码像同步代码一样

### async 函数

1. async 函数的返回值为 promise 对象
2. promise 对象的结果由 async 函数执行的返回值决定

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script type="module">
            // async 函数
            async function fn() {
                // 返回一个字符串
               	// return '尚硅谷';
                
                // 返回结果不是一个 Promise 类型的对象，返回的结果就是成功的 Promise 对象
                // return;
                
                // 抛出错误，返回的结果是一个失败的 Promise
                // throw new Error('出错啦！');
                
                // 返回的结果如果是一个 Promise 对象
                return new Promise((resolve, reason) => {
                    // resolve("成功的数据");
                    reject("失败的错误");
                });
            }
            
            const result = fn();
            
            console.log(result); // promise 对象
        </script>
    </body>
</html>
```

### await 表达式

1. await 必须写在 async 函数中
2. await 右侧的表达式一般为 promise 对象
3. await 返回的是 promise 成功的值
4. await 的 promise 失败了，就会抛出异常，需要通过 try...catch 捕获异常

```html
<!DOCTYPE html>
<html lang="en"> <!-- lang 用来定义当前文档显示的语言 -->
    <head>
        <meta charset="utf-8">
    </head>
    <body>
		<script type="module">
            // 创建 promise 对象
            const p = new Promise((resolve, reject) => {
                // resolve("成功的值！");
                reject("失败啦！");
            });
            
            // await 要放在 async 里面
            async funciton main() {
                try {
                    let result = await p;
                
                    console.log(result);
                } catch (e) {
                    console.log(e);
                }
            }
            
            // 调用函数
            main();
        </script>
    </body>
</html>
```

