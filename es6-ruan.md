#es6

##let和const
    * 类似var,let声明变量，const声明常量
      * 块级作用域
      * 不存在变量提升
      * 不能重复声明
       * 必须先声明才可以使用，否则报错（暂时性死区）
       * 生命变量的6种方式
           -var/function命令
        -let/const命令
        -import/class命令
        -let命令、const命令、class命令声明的全局变量，不属于顶层对象的属性（不能通过window.访问到）

##解构赋值
    * 只要等号两边的模式相同，左边的变量就会被赋予对应的值
    * 如果解构不成功，变量的值就等于undefined
    * 解构赋值允许指定默认值。（匹配值严格等于undefined）
    * 用途
        -交换变量的值
        -从函数返回多个值
        -函数参数的定义
        -提取JSON数据
        -函数参数的默认值
        -遍历Map结构
        -输入模块的指定方法
##字符串的扩展
    * unicode方面
    * 检测包含字符api
        -includes()：返回布尔值，表示是否找到了参数字符串。
        -startsWith()：返回布尔值，表示参数字符串是否在源字符串的头部。
        -endsWith()：返回布尔值，表示参数字符串是否在源字符串的尾部。
    * 'x'.repeat(3) 方法返回一个新字符串，表示将原字符串重复n次。
    * padStart/padEnd字符串补全长度 'x'.padStart(5, 'ab') // 'ababx'
    * -模板字符串`${msg}`
##正则的扩展
    * 字符串正则方法match()、replace()、search()和split()
    * 新增修饰符x y u flags
##数值的扩展
    * is...
        -Number.isFinite()检查一个数值是否为有限的
        -Number.isNaN()用来检查一个值是否为NaN
        -Number.isInteger()用来判断一个值是否为整数
        -Number.isSafeInteger()用来判断一个整数是否落在Number.MAX_SAFE_INTEGER和Number.MIN_SAFE_INTEGER这两个常量这个范围之内
    * Number.parseInt()/Number.parseFloat()
    * Number.EPSILON为浮点数运算，部署了一个误差检查值
    * Math对象扩展
        -Math.trunc方法用于去除一个数的小数部分，返回整数部分
        -Math.sign方法用来判断一个数到底是正数、负数、还是零
        -Math.cbrt方法用于计算一个数的立方根
        -Math.hypot方法返回所有参数的平方和的平方根
        -...
    * 指数运算符（**） 2**=4;
##函数的扩展
    * 参数默认值（与解构赋值运用）
    * 函数的 length 属性 （没有默认值的参数的个数）
    * 作用域
    * rest参数
    * name 属性
    * arrow 函数
        -简化回调 map/filter/sort
    * 绑定this  thisObj::fn(提案)
    * 尾递归、尾调用 优化  、尾逗号
##数组的扩展
    * 扩展运算符...
        -合并数组
        -与解构赋值
        -函数返回值？
        -将字符串转成数组
        -将某些伪数组实现了 Iterator 接口
    * Array.from()将伪数组、类数组对象转成数组（有length属性）
    * Array.of（）方法用于将一组值，转换为数组
    * [].copoyWithin(target[,start][,end=arr.lenght])将指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组
    * find(fn)
        - find方法，用于找出第一个符合条件的数组成员
        - findIndex方法，用于找出第一个符合条件的数组成员索引
    * fill（n,start,end）方法使用给定值，填充一个数组
    * entries()，keys(),values()遍历数组
	* includes()表示某个数组是否包含给定的值，与字符串的includes方法类似
##对象的扩展
	* 方法的name属性
	* Object.is()用来比较两个值是否严格相等
	* Object.assign(target[,obj1,obj2])方法用于对象的合并(浅拷贝、可枚举属性)
		- 为对象添加属性、方法
		- 合并多个对象
		- 为属性指定默认值
		- 尽量不要用for...in循环，而用Object.keys()代替
			-for...in循环：只遍历对象自身的和继承的可枚举的属性
    		-Object.keys()：返回对象自身的所有可枚举的属性的键名
    		-JSON.stringify()：只串行化对象自身的可枚举的属性
	* 属性的遍历
		- for...in循环遍历对象自身的和继承的可枚举属性（不含 Symbol 属性）
		- Object.keys返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 Symbol 属性）
		- Object.getOwnPropertyNames返回一个数组，包含对象自身的所有属性（不含 Symbol 属性，但是包括不可枚举属性）。
		- Object.getOwnPropertySymbols返回一个数组，包含对象自身的所有 Symbol 属性
		- Reflect.ownKeys返回一个数组，包含对象自身的所有属性，不管属性名是 Symbol 或字符串，也不管是否可枚举。
	* Object.keys()/Object.values()/Object.entries()可用for of遍历
	* Object.getOwnPropertyDescriptor(obj, 'p')返回某个对象属性的描述对象
			
##Symbol
	* 是一种类似字符串的数据类型
	* 是一个Symbol函数，不能用new.  let s=Symbol('abc')
	* 作为对象的属性名用中括号语法，（唯一性，避免冲突）
	* 只有Object.getOwnPropertySymbols方法Reflect.ownKeys方法返回
	* Symbol.for方法
		- 可以返回同一个Symbol值，没有创建有就返回，
		- Symbol.keyFor方法返回一个已登记的 Symbol 类型值的key
		- Symbol.for运用在Singleton模式
	* 内置的Symbol值
		- 对象的Symbol.hasInstance属性 instanceof
		- 对象的Symbol.isConcatSpreadable属性使用concat()时，是否可以展开
		- 对象的Symbol.species属性，指向当前对象的构造函数，采用get读取器
		- 对象的Symbol.match属性 str.match(myObject)存在返回
		- 对象的Symbol.replace属性 str.replace(myObject)
		- 对象的Symbol.search属性 str.search(myObject)
		- 对象的Symbol.split属性
		- 对象的Symbol.iterator属性，指向该对象的默认遍历器方法
		- 对象的Symbol.toPrimitive属性 被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值
		- 对象的Symbol.toStringTag属性 定制[object Object]或[object Array]中object后面的那个字符串
		- 定制[object Object]或[object Array]中object后面的那个字符串
##Set和Map数据结构
	* Set、Map是构造函数
	* new Set()它类似于数组，但是成员的值都是唯一的
	* 可接受数组、类数组作为参数
	* 实例属性
		- constructor :构造函数，默认就是Set函数。
		- size: 返回Set实例的成员总数。
		- add(value)：添加某个值，返回Set结构本身。
		- delete(value)：删除某个值，返回一个布尔值，表示删除是否成功
		- has(value)：返回一个布尔值，表示该值是否为Set的成员。
		- clear()：清除所有成员，没有返回值。
	* 数组去重Array.from(new Set(arr))
	* 遍历操作(插入顺序)：keys()/values()/entries()/forEach()
	* WeakSet 只能add对象 不可遍历
	* Map数据结构类似对象，键的值可以是任意类型
	* Map实例属性、方法
		- size
		- set(key,value)
		- get(key)
		- has(key)
		- delete(key)
		- clear()
		- 遍历(插入方法)方法 keys()/values(）/entries()/forEach()
	* WeakMap 只接受对象作为键名 不可遍历
##Proxy
	* 用于修改某些操作的默认行为,代理器
	* var proxy = new Proxy(target, handler);
	* 实例方法
		- get方法用于拦截某个属性的读取操作
		- set方法用来拦截某个属性的赋值操作
		- apply方法拦截函数的调用、call和apply操作
		- has方法用来拦截HasProperty操作，即判断对象是否具有某个属性时，这个方法会生效
		- construct方法用于拦截new命令，下面是拦截对象的写法
		- deleteProperty方法用于拦截delete操作，如果这个方法抛出错误或者返回false，当前属性就无法被delete命令删除
		- defineProperty方法拦截了Object.defineProperty操作
		- getOwnPropertyDescriptor方法拦截Object.getOwnPropertyDescriptor()，返回一个属性描述对象或者undefined
		- getPrototypeOf方法主要用来拦截获取对象原型
		- isExtensible方法拦截Object.isExtensible操作
		- ownKeys方法用来拦截对象自身属性的读取操作
##Reflect
	*  将Object对象的一些明显属于语言内部的方法放到Reflect对象上
	*  静态方法
## Promise对象
    * Promise对象代表一个异步操作，有三种状态：Pending（进行中）、Fulfilled（已成功）和Rejected（已失败）
	，可以将异步操作以同步操作的流程表达出来
    * Promise对象是一个构造函数，用来生成Promise实例。
    * Promise.prototype.then()
    * Promise.prototype.catch() (相当于then中的rejectFn,但一般rejectFn直接用catch)
    * Promise.all([p1,p2,p3])用于将多个 Promise 实例，包装成一个新的 Promise 实例。
    * Promise.race([p1,p2,p3])方法同样是将多个Promise实例，包装成一个新的Promise实例。
    * Promise.resolve方法将现有对象转为Promise对象，
    * Promise.resolve('foo') 等价于new Promise(resolve => resolve('foo'))
    * Promise.reject(reason)方法也会返回一个新的 Promise 实例，该实例的状态为rejected。
    * 应用：done(),finally(),图片加载

## Iterator 和 for...of 循环
	* 是一种接口，为for...of消费
		- 遍历时创建一个指针对象，调用一个next方法就返回{value:arr[index++],done:false},done:true为遍历结束
	* 默认的 Iterator 接口部署在数据结构的Symbol.iterator属性
	    ` const obj = {
	    	[Symbol.iterator] : function (arr) {
	    		var nextIndex = 0;
				return {
					next: function () {
						return nextIndex< arr.length? 
						{value : arr[index++],done: false}:
						{value : undefined,done: true}
					}
				}
	    	}
	    }`
	    - 原生具备 Iterator 接口的数据结构:Array/Map/Set/String/TypedArray/arguments/NodeList 对象/
	    - 一个对象如果要具备可被for...of循环调用的 Iterator 接口，就必须在Symbol.iterator的属性上部署遍历器生成方法
	* 调用Iterator的场合
		- 解构赋值（数组和 Set 结构）
		- 扩展运算符
		- yield*后面跟的是一个可遍历的结构，它会调用该结构的遍历器接口
		- 其他:(for...of/Array.from()/Map(), Set(), WeakMap(), WeakSet()（比如new Map([['a',1],['b',2]])）/Promise.all()/Promise.race()
	* 字符串的Iterator接口
	* Iterator接口与Generator函数
	* for ...of 只返回具有数字索引的属性
	  - set和map结构Set 结构用for..of遍历时，返回的是一个值，而 Map 结构遍历时，返回的是一个数组,
	  - 并不是所有类似数组的对象都具有 Iterator 接口，一个简便的解决方法，就是使用Array.from方法将其转为数组。
	  - 对于普通的对象，for...in循环可以遍历键名，for...of循环会报错。(使用Object.keys方法将对象的键名生成一个数组)
	  - 没有for...in那些缺点（会遍历手动添加的其他键，甚至包括原型链上的键
	  ）。
        不同于forEach方法，它可以与break、continue和return配合使用。
        提供了遍历所有数据结构的统一操作接口。
## Generator 函数
	* Generator 函数除了状态机，还是一个遍历器对象生成函数
	* yiled表达式
		-  Generator 函数返回的遍历器对象，只有调用next方法才会遍历下一个内部状态，所以其实提供了一种可以暂停执行的函数。yield表达式就是暂停标志。yield表达式后面的表达式，只有当调用next方法、内部指针指向该语句时才会执行
	* 与Iterator的联系  对象的Symbol.iterator方法，等于该对象的遍历器生成函数
	* next方法的参数：参数就会被当作上一个yield表达式的返回值。
	* Generator.prototype.throw() 函数体外抛出错误，然后在 有try...catch的Generator 函数体内捕获
	* Generator.prototype.return()可以返回给定的值，并且终结遍历Generator函数
	* yield*表达式，用来在一个 Generator 函数里面执行另一个 Generator 函数。
	* 作为对象属性的Generator函数
	* Generator 状态机
	* 应用
		- 控制流
		- 部署iterator接口
		- Generator 使得数据或者操作，具备了类似数组的接口。
## Genertor函数的异步应用
	* 传统方法
		- 回调函数
		- 事件监听
		- 发布、订阅
		- promise
	* Genertor函数
		- 数据交换和错误处理机制：next()方法的value和参数
		- Thunk函数（传名调用），is中多参数函数将其替换成一个只接受回调函数作为参数的单参数函数
		- Thunkify 模块
		- co模块 函数返回一个Promise对象，因此可以用then方法添加回调函数。
## Async函数
	* async 函数它就是 Generator 函数的语法糖,async函数就是将 Generator 函数的星号（*）替换成async，将yield替换成await
	* 语法
		- 返回promise对象
		- await命令 后面一般是promise对象,运行结果可能是rejected，所以最好把await命令放在try...catch代码块中。
	* 实现原理：generator函数和自动执行器包装在一个函数里面
	* for await ... of
	* 异步Generator函数 是async与generator的结合
## Class的基本用法
	* 类
		- 类的所有方法都定义在类的prototype属性上面。
		- 类的内部所有定义的方法，都是不可枚举的（non-enumerable）。	
		- 类和模块中默认为严格模式
		- constructor方法是类的默认方法,通过new命令生成对象实例时，自动调用,constructor方法默认返回实例对象（即this）
		- 类必须使用new调用,否则会报错
		- class表达式
	* 不存在变量提升
	* 私有方法
	* 私有属性 es6暂时不支持
	* this的指向 默认指向类的实例，但是不能单独使用
	* class的存值函数和取值函数 set get 
	* class的generator方法 *[Symbol.iterator]
	* class的静态方法
		- 类相当于实例的原型(this为类) static 直接通过类来调用
		- 父类的静态方法，可以被子类继承。
		- 静态方法也是可以从super对象上调用的。
	* class的静态属性 和实例属性
		- Class 本身的属性 Class 内部只有静态方法，没有静态属性。
	* new target
		- Class 内部调用new.target，返回当前 Class。
		- 子类继承父类时，new.target会返回子类。
## class的继承
	* class可以通过extends关键字实现继承
	* Object.getPrototypeOf方法可以用来从子类上获取父类。判断，一个类是否继承了另一个类。
	* super关键字既可以当作函数使用，也可以当作对象使用
		- super作为函数调用时，代表父类的构造函数,ES6 要求，子类的构造函数必须执行一次super函数。作为函数时，super()只能用在子类的构造函数之中
		- super作为对象时，在普通方法中，指向父类的原型对象；在静态方法中，指向父类。
		- 通过super调用父类的方法时，super会绑定子类的this
		- 果通过super对某个属性赋值，这时super就是this，赋值的属性会变成子类实例的属性。
		- super作为对象，用在静态方法之中，这时super将指向父类
	* 类的prototype和__proto__
		- 子类的__proto__属性，表示构造函数的继承，总是指向父类。
		- 子类prototype属性的__proto__属性，表示方法的继承，总是指向父类的prototype属性。
	* extends的继承目标
	* 实例的__proto__
		- 子类实例的__proto__属性的__proto__属性，指向父类实例的__proto__属性。
	* 原生构造函数的继承
	* Mixin 模式：将多个类的接口“混入”（mix in）另一个类
## decorator修饰器
	* 






