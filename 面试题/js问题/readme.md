# 1.js数组上有哪些方法？
1. 增加：push()、unshift()、splice()、concat()
2. 删除：shift()、pop()、splice()、slice()
3. 修改：reverse()、sort()
4. 查找：indexOf()、lastIndexOf()、includes()、find()
5. 转换：join()
6. 迭代：forEach()、map()、filter()、some()、every()
7. 其他：Array.from() // 从可迭代的对象构造一个新的数组实例
        Array.of() // 创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型

1. shift // 移除数组第一个元素并返回该元素的值
2. unshift // 在数组的开头添加一个或多个元素，并返回新的长度
3. pop // 移除数组最后一个元素并返回该元素的值
4. push // 在数组的末尾添加一个或多个元素，并返回新的长度
5. splice // 删除元素、插入元素、替换元素
6. reverse // 反转数组元素的顺序
7. sort // 对数组元素进行排序
8. concat // 合并两个或多个数组，并返回一个新的数组
9. slice // 选择数组的某个片段，并返回一个新的数组
10. indexOf // 返回某个指定的元素在数组中的索引值，如果找不到该元素，则返回-1
11. lastIndexOf // 返回某个指定的元素在数组中的最后一个的索引值，如果找不到该元素，则返回-1
12. includes // 判断某个元素是否在数组中，返回true或false
13. forEach // 遍历数组的所有元素并执行回调函数
14. map // 遍历数组的所有元素并执行回调函数，返回一个新的数组
15. filter // 遍历数组的所有元素并执行回调函数，返回一个新的数组，新数组中的元素是通过回调函数的判断条件全部筛选出来的
16. some // 遍历数组的所有元素并执行回调函数，返回true或false，只要有一个元素通过了回调函数的判断，就返回true
17. every // 遍历数组的所有元素并执行回调函数，返回true或false，只要有一个元素没有通过回调函数的判断，就返回false
18. join // 将数组的所有元素连接成一个字符串并返回这个字符串

# 2. js字符串有哪些方法？
1. 增加：concat()
2. 删除：slice()、substring()、substr()
3. 修改：replace()、toLowerCase()、toUpperCase()、trim()、trimLeft()、trimRight()、padStart()、padEnd()
4. 查找：indexOf()、lastIndexOf()、includes()、find()、endWith()、startWith()

在JavaScript中，字符串具有以下内置方法：

1. `charAt(index)`：返回指定索引处的字符。
2. `charCodeAt(index)`：返回指定索引处的字符的Unicode编码。
3. `concat(str)`：将另一个字符串连接到当前字符串。
4. `endsWith(search)`：检查字符串是否以指定字符串结尾。
5. `every(callback)`：检查字符串中的每个字符是否满足给定的回调函数。
6. `filter(callback)`：过滤字符串中的字符，只保留满足回调函数的字符。
7. `fromCharCode(code)`：根据Unicode编码将字符转换为字符串。
8. `includes(search)`：检查字符串是否包含指定字符串。
9. `indexOf(search)`：返回指定字符串在字符串中的首次出现位置。
10. `lastIndexOf(search)`：返回指定字符串在字符串中的最后一次出现位置。
11. `localeCompare(locale)`：比较两个字符串，根据指定的语言环境返回一个负数、零或正数。
12. `match(regex)`：根据正则表达式匹配字符串。
13. `normalize(form)`：根据指定的Unicode字符集标准将字符串标准化。
14. `repeat(count)`：将字符串重复指定次数。
15. `replace(regex, str)`：用另一个字符串替换所有匹配正则表达式的字符。
16. `search(regex)`：根据正则表达式搜索字符串。
17. `slice(start, end)`：返回字符串的一部分。
18. `split(separator, limit)`：根据指定的分隔符将字符串分割成子字符串。
19. `substring(start, end)`：返回字符串的一部分，范围从指定的start到指定的end。
20. `toCharCode(code)`：将字符转换为Unicode编码。
21. `toLocaleLowerCase()`：将字符串转换为本地小写。
22. `toLocaleUpperCase()`：将字符串转换为本地大写。
23. `toLowerCase()`：将字符串转换为小写。
24. `toUpperCase()`：将字符串转换为大写。
25. `trim()`：删除字符串首尾的空白字符。

# 3. 谈谈js中的类型转换机制
- 是什么？
    js中有原始类型和引用类型：
    原始类型：
        - number    - string    - symbol    - boolean   - null  - undefined - BigInt
    引用类型：
        - object    - function  - array     - Date      - RegExp( 正则表达式)   - Set    - Map
    通常开发过程中，会用到一些手段来完成逻辑开发 --- 显示类型转换，在v8执行过程中还存在另一种类型转换 --- 隐式类型转换
        - 显示类型转换：
            - Number() - String() - Boolean() - parseInt() - parseFloat() - JSON.stringify() - JSON.parse()
        - 隐式类型转换：
            - 比较运算符( > < >= <= == === != !== if while)
            - 算数运算符(+ - * / %)
            - 条件判断语句( [] == ![] 为true, [] === ![] 为true)

在ES6中，[] == ![] 的结果是 true，实际上它可以通过类型转换来解释。

首先，让我们分析一下 ![]。! 是逻辑非操作符，它会将操作数转换为布尔值并取反。因为它是一个对象，而所有对象在JavaScript中都会被视为真值。在逻辑上，空数组代表着“存在”，所以它会被转换为布尔值 true，然后取反就变成了 false。

接着，我们来看 [] == false。当使用双等号进行比较时，如果两边的操作数类型不同，JavaScript 会尝试对它们进行类型转换。在这个例子中，左边是一个对象（数组），右边是一个布尔值，JavaScript 将布尔值转换为数字，即 false 被转换为 0。

综上所述，[] == ![] 可以转换为 [] == false，进而转换为 [] == 0。接下来，JavaScript 会尝试对数组和数字进行比较，此时会将数组转换为字符串，即 ''，然后再将其转换为数字，即 0。所以最终的比较变成了 0 == 0，因此结果为 true。

这种行为可能会带来一些混淆，因此在编写代码时，最好使用严格相等操作符 === 来避免类型转换带来的意外结果。

如下：!不会触发隐式转换，而 == 触发 隐式类型转换，即引用类型转换为原始类型，用js自带的toprimitive()方法转换为原始类型
[] == ![]
[] == !true
[] == false
'' == false
0 == 0

# 4. == 和 === 的区别？
- == 是比较两个值是否相等，不考虑类型，=== 是比较两个值和类型是否相等
- == 存在类型转换
- === 不存在类型转换

# 5. 深拷贝和浅拷贝的区别？如何实现一个深拷贝？
- 深浅拷贝通常只针对引用类型

- 浅拷贝：只拷贝一层对象，复制这一层对象中的原始值，如果有引用类型，拷贝的是引用地址，所以两个对象的引用地址是相同的
    - Object.assign concat slice [...arr]
- 深拷贝：层层拷贝，拷贝 包括对象中的原始值和引用值，如果有引用类型，拷贝的是引用地址，但是两个对象的引用地址是不同的
    - JSON.parse(JSON.stringify(obj)) --- 无法处理 undefined Symbol function -- 无法处理循环引用

# 6. 请说说你对闭包的理解？
- 是什么
    当一个函数中的内部函数被拿到函数外部调用，又因为在js中内层作用域总是能访问外层作用域的，该内部函数就拥有了外层函数的作用域中的变量的引用，内部函数的作用域访问外层函数的作用域中的变量，这些变量的集合就是闭包。

- 使用场景:
    1. 创建私有变量 (全局变量不易维护)
    2. 延长变量的生命周期
    3. 实现柯里化 (颗粒)

- 缺点：会造成内存泄漏

# 7. 什么是柯里化？
- 是什么
    将接受多个参数的函数转换成多个只接受一个参数（最初函数的第一个参数）的函数。

# 8. 说说你对作用域的理解
- 是什么：
    变量和函数能够生效的区域。这个区域叫作用域

- 作用域有哪些？
    1. 全局作用域
    2. 函数作用域
    3. 块级作用域 (let const for循环 {内部})

- 作用域链：作用域只能从内到外的访问，这种访问规则形成的链状关系我们称为作用域链。

- 词法作用域：指的是函数或变量定义的区域，函数定义的区域称为函数作用域，块级作用域称为块级作用域，全局作用域称为全局作用域。

# 9. 说说你对原型的解释
- 是什么：
    1. 显示原型指的是函数身上自带prototype属性，通常可以将一些书型盒方法添加在显示原型上，可供实例对象继承到
    2. 隐式原型__proto__是对象这种结构上的一个属性，其中包含了创建该对象时，隐式继承的属性

- 原型链：创建一个实例对象时，实例对象的隐式原型===创建该实例对象的构造函数的显示原型，在js中对象的查找规则是先在对象中查找，
        找不到再去对象的隐式原型上查找，顺着隐式原型一层层往上找，直到找到null为止，这种查找规则我们就叫原型链

- 可用来实现属性的继承

# 10. 说说js中的继承
- 是什么：在js中继承指的是让一个子类可以访问父类的属性和方法

- 继承有哪些方式？
- 构造函数继承
    1. 原型链继承：构造函数的显示原型等于实例对象的隐式原型 
        (1.无法给父类灵活传参 2.多个实例对象共用了一个原型对象，无法实现私有属性 3.无法实现多继承)
    2. 构造函数继承
        (1. 只能继承到父类身上的属性，无法继承到父类原型上的属性)
    3. 组合继承(经典继承)：
        (1. 存在多次父类函数的调用，多造成了性能开销)
    4. 原先式继承：
        (1. 因为是浅拷贝，父类中的引用类型在子类之间公用了，会相互影响)
    5. 寄生式 继承：(1. 同上)
    6. 寄生组合式继承：没有缺点
    7. class继承：extends关键字,super()

# 11. 说所说js中的this
- 是什么：this是函数在运行过程中自动生成的一个对象，用来代指作用域的指向

- 绑定规则：
    1. 默认绑定： 当函数独立调用时，函数的this一定指向window (函数的词法作用域在哪，this就指向哪个词法作用域)
    2. 隐式绑定： 当函数被一个对象所调用时，函数的this指向该对象
    3. 隐式丢失： 当函数调用前有多个对象，函数的this指向该最近的对象
    4. 显示绑定： call(直接使用), apply, bind(需要创建一个变量,它返回一个函数体)
    5. new绑定： this指向实例对象

- 箭头函数：箭头函数没有自己的this，箭头函数的this继承自外层函数的this 


# 12. new的实现原理
- 构造函数有返回值，且为引用类型时会覆盖new当中的返回值

# 13. call, apply, bind的原理

# 14. 说说js中的事件模型
- 什么事件流

- 分类

1. DOM0级事件模型：onclick (无法控制事件捕获冒泡)
2. DOM1级事件模型：addEventListener (可以控制事件实执行在哪个阶段执行)
3. IE事件模型：attachEvent (无法控制事件在捕获冒泡哪个阶段执行)

# 15. 说说typeof和instanceof的区别？
- typeof：能判断除了null之外的所有原始类型，但是无法判断引用数据类型中的具体类型, 都判断为object, 但function判断为function
- instanceof：判断引用类型的具体, 通过原型链循环判断
- 手写instanceof
- Object.prototype.toString.call(?)
    1. [].toString.call() 数组版本的toString
    2. Object.prototype.toString.call([]) 对象版本的同String 
    
    该方法会让变量 ？ 调用对象的toString方法，然后返回结果
- Array.isArray()

# 16. 说说Ajax的原理
- 什么是Ajax？
    Async JavaScript and XML，是一种异步js和网页的交互的技术，在不刷新整个网页的情况下，能够更新部分网页。

- 实现过程
    1. 创建XHR实例对象
    2. 调用实例对象中的open方法于服务器建立链接
    3. 调用实例对象中的send方法发送请求
    4. 监听实例对象中的onreadystatechange事件，通过判断readyState属性的值，判断请求是否完成，然后执行回调函数
    5. 将数据更新到html页面

# 17. 怎么实现上拉加载下拉刷新？
- 什么是上拉加载下拉刷新？
    1. 监听 touchstart touchmove touchend 事件，记录手指移动的距离，大于临界值时实现刷新操作，其中使用 transfrom: translateY 来添加各处的动画
    2. 根据手指移动的距离，判断是上拉还是下拉，然后执行对应的操作

# 18. 防抖节流？

# 19. 事件代理
 - 事件委托 （多个子容器需要绑定相同的事件）
    1. 事件冒泡指在在一个对象上触发某类事件，如果此对象绑定了事件，就会触发事件，如果没有，就会向这个对象的父级对象传播，最终父级对象触发了事件。

    2. 事件委托本质上是利用了浏览器事件冒泡的机制。因为事件在冒泡过程中会上传到父节点，并且父节点可以通过事件对象获取到目标节点，因此可以把子节点的监听函数定义在父节点上，由父节点的监听函数统一处理多个子元素的事件，这种方式称为事件代理。

# 20. 说说js中的事件循环
 - 什么是事件循环？
    1. js引擎在执行js放入过程中会区分同步和异步代码，先执行同步再执行异步，异步中同样按照先执行同步再执行异步的策略，以此往复循环
    2. js是单线程的，所以同一时间只能做一件事，如果遇到耗时操作，就会阻塞后续操作

 - 异步
     - 微任务队列要优先于宏任务队列。微任务队列的代表就是，Promise.then，MutationObserver，宏任务的话就是setImmediate setTimeout setInterval

    1. 宏任务 <script> setTimeout() setInterval() setImmediate I/O UI-rendering postMassage MessageChannel
    2. 微任务 .then() nextTick() MutationObserver

 - Event-Loop
    1. 执行同步代码 （也叫宏任务）
    2. 执行微任务 （完毕）
    3. 有需要的话就渲染页面
    4. 执行宏任务 （下一次事件循环的开始）

