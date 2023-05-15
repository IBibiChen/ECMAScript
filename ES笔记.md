## **理解 ES**
1. 全称: ECMAScript
2. js 语言的规范
3. 我们用的 js 是它的实现
4. js 的组成
  * ECMAScript(js 基础)
  * 扩展-->浏览器端
    * BOM
    * DOM
  * 扩展-->服务器端
    * Node.js
      
## ES5
1. **严格模式**
  * 运行模式: 正常(混杂)模式与严格模式
  * 应用上严格式: 'strict mode';
  * 作用: 
    * 使得 Javascript 在更严格的条件下运行
    * 消除 Javascript 语法的一些不合理、不严谨之处，减少一些怪异行为
    * 消除代码运行的一些不安全之处，保证代码运行的安全
    * 需要记住的几个变化
      * 声明定义变量必须用 var
      * 禁止自定义的函数中的 this 关键字指向全局对象
      * 创建 eval 作用域, 更安全
      
2. **JSON 对象**
  * 作用: 用于在 json 对象/数组与 js 对象/数组相互转换
  * JSON.stringify(obj/arr)
      js 对象(数组)转换为 json 对象(数组)
  * JSON.parse(json)
      json 对象(数组)转换为 js 对象(数组)
      
3. Object 扩展
  * Object.create(prototype[, descriptors]) : 创建一个新的对象
    * 以指定对象为原型创建新的对象
    * 指定新的属性, 并对属性进行描述
      * value : 指定值
      * writable : 标识当前属性值是否是可修改的, 默认为 true
      * **get 方法** : 用来得到当前属性值的回调函数
      * **set 方法** : 用来监视当前属性值变化的回调函数
  * Object.defineProperties(object, descriptors) : 为指定对象定义扩展多个属性
  
4. Array 扩展
  * Array.prototype.indexOf(value) : 得到值在数组中的第一个下标
  * Array.prototype.lastIndexOf(value) : 得到值在数组中的最后一个下标
  * **Array.prototype.forEach(function(item, index){}) : 遍历数组**
  * **Array.prototype.map(function(item, index){}) : 遍历数组返回一个新的数组**
  * **Array.prototype.filter(function(item, index){}) : 遍历过滤出一个子数组**
  
5. **Function 扩展**
  * Function.prototype.bind(obj)
      * 将函数内的 this 绑定为 obj, 并将函数返回
  * 面试题: 区别 bind()与 call() 和 apply()?
      * fn.bind(obj) : 指定函数中的 this, 并返回函数
      * fn.call(obj) : 指定函数中的 this, 并调用函数
      
6. Date 扩展
  * Date.now() : 得到当前时间值
  
## ES6
1. **2 个新的关键字**
  * let/const
  * 块作用域
  * 没有变量提升
  * 不能重复定义
  * 值不可变
  
2. **变量的解构赋值**
  * 将包含多个数据的对象(数组)一次赋值给多个变量
  * 数据源: 对象/数组
  * 目标: {a, b}/[a, b]
  
3. 各种数据类型的扩展
  * 字符串
    * **模板字符串** 
      * 作用: 简化字符串的拼接
      * 模板字符串必须用``
      * 变化的部分使用 ${xxx} 定义
    * contains(str) : 判断是否包含指定的字符串
    * startsWith(str) : 判断是否以指定字符串开头
    * endsWith(str) : 判断是否以指定字符串结尾
    * repeat(count) : 重复指定次数
         
  * 对象
    * **简化的对象写法**
      ```
      let name = 'Tom';
      let age = 12;
      let person = {
          name,
          age,
          setName (name) {
              this.name = name;
          }
      };
      ```
    * Object.assign(target, source1, source2...) : 将源对象的属性复制到目标对象上
    * Object.is(v1, v2) : 判断 2 个数据是否完全相等
    * __proto__属性 : 隐式原型属性
     
  * 数组
    * Array.from(v) : 将伪数组对象或可遍历对象转换为真数组
    * Array.of(v1, v2, v3) : 将一系列值转换成数组
    * find(function(value, index, arr){return true}) : 找出第一个满足条件返回 true 的元素
    * findIndex(function(value, index, arr){return true}) : 找出第一个满足条件返回 true 的元素下标
  * 函数
    * **箭头函数**
      * 用来定义匿名函数
      * 基本语法:
        * 没有参数: () => console.log('xxxx')
        * 一个参数: i => i + 2
        * 大于一个参数: (i, j) => i + j
        * 函数体不用大括号: 默认返回结果
        * 函数体如果有多个语句, 需要用{}包围
      * 使用场景: 多用来定义回调函数
    * **形参的默认值**
      * 定义形参时指定其默认的值
    * **rest(可变)参数**
      * 通过形参左侧的...来表达, 取代 arguments 的使用
    * **扩展运算符(...)**
      * 可以分解出数组或对象中的数据
    
4. set/Map 容器结构
  * 容器: 能保存多个数据的对象, 同时必须具备操作内部数据的方法
  * 任意对象都可以作为容器使用, 但有的对象不太适合作为容器使用(如函数)
  * **Set 的特点**: 保存多个 value, value 是不重复 ===> 数组元素去重
  * **Map 的特点**: 保存多个 key--value, key 是不重复, value 是可以重复的
  * API
    * Set()/Set(arr) // arr 是一维数组
    * add(value)
    * delete(value)
    * clear();
    * has(value)
    * size
    * 
    * Map()/Map(arr) // arr是二维数组
    * set(key, value)
    * delete(key)
    * clear()
    * has(key)
    * size
    
5. **for--of 循环**
  * 可以遍历任何容器
  * 数组
  * 对象
  * 伪/类对象
  * 字符串
  * 可迭代的对象
  
6. **Promise**
  * 解决`回调地狱`(回调函数的层层嵌套, 编码是不断向右扩展, 阅读性很差)
  * 能以同步编码的方式实现异步调用
  * 在 es6 之前原生的 js 中是没这种实现的, 一些第三方框架(jQuery)实现了 promise
  * ES6 中定义实现 API: 
    ```
    // 1. 创建 promise 对象
    var promise = new Promise(function(resolve, reject){ 
      // 做异步的操作 
      if(成功) { // 调用成功的回调
        resolve(result); 
      } else { // 调用失败的回调
        reject(errorMsg); 
      } 
    }) 
    // 2. 调用 promise 对象的 then()
    promise.then(function(
      result => console.log(result), 
      errorMsg => alert(errorMsg)
    ))
    ```
7. **class 类**
  * 用 class 定义一类
  * 用 constructor() 定义构造方法(相当于构造函数)
  * 一般方法: xxx () {}
  * 用 extends 来定义子类
  * 用 super() 来父类的构造方法
  * 子类方法自定义: 将从父类中继承来的方法重新实现一遍
  * js 中没有方法重载(方法名相同, 但参数不同)的语法
  
8. **模块化(后面讲)**

## ES7
* 指数运算符: **
* Array.prototype.includes(value) : 判断数组中是否包含指定 value
  
  
* **区别方法的 2 种称谓**
  * 静态(工具)方法
    * Fun.xxx = function(){}
  * 实例方法
    * 所有实例对象 : Fun.prototype.xxx = function(){} // xxx 针对 Fun 的所有实例对象
    * 某个实例对象 : fun.xxx = function(){} // xxx 只是针对 fun 对象