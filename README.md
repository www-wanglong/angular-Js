AngularJS权威学习

## 三、模块
    1.`angular.module('myApp', [])`
      这个方法相当于AngularJs模的setter方法，是用来定义模块的。 第二个是依赖列表，也就是可以被注入到模块中的对象列表
    2. `angular.module('myApp'）`
      获取模块
## 四、作用域 -- Scope
    1.$scope 对象在AngularJs中充当数据模型，$scope并不负责处理和操作数据，他只是视图和HTML之间的桥梁，他是视图和控制器之间的胶水
    2.angularJs模板的标记：指令、值绑定{{}}、过滤器、表单控件
### 1.作用域的基本功能
    1.提供观察者以见识数据模型的变化
    2.可以奖数据模型的变化通知给整个应用，甚至是系统外的组件
    3.可以进行嵌套，隔离业务功能和数据
    4.给表达式提供运算时所需的执行环
### 2.$scope的生命周期
    1.创建: 在创建控制器或指令时，$injector创建新的作用域，并在这个新的控制器或指令运行时将作用域传递进去
    2.链接：$switch函数
    3.更新：每个监控函数都会检查变化。如变化，$scope函数就会出发指定的回调函数
    4.销毁：不需要时
## 五、控制器 -- 增强视图
    1.指令内部创建的作用域被称作孤立作用域。除了孤立作用域外，所有的作用域都是通过原型继承的
    2.默认情况下，Angular在当前作用域中无法找到某个属性时，便会在父级作用域找
## 七、表单验证
    1.未修改的表单 $pristine
    2.修改过的表单 $dirty
    3.合法的表单 $valid
    4.不合法的表单 $invalid
    5.错误的信息 $error
## 八、指令
    指令就是angularJs扩展具有自定义功能的HTML元素的途径。
    子控制器是复制父控制的值，而非应用
    JavaScope对象要么是值复制要么是引用复制。字符串、数字和布尔变量是值复制。数组和函数则是引用复制。
    ng-repeat: $index $first $middle $last $even $add
## 十、指令详解
    特定DOM元素上运行的函数，指令可以扩展这个元素的功能。
    一个JavaScript对象由键和值组成。当给定键的值被设置为一个字符串、布尔值、数字、数组、对象时，我们把这个键成为属性。当把键设置为函数时，我们把它叫做方法。
    restrict(字符串)
    10.4 AngularJs的生命周期
      在AngularJs应用启动钱，它们以HTML文本的形式保存在文本编辑器中。应用启动后会进行编译和链接，作用域会同html进行绑定，应用可以对用户在HTML中进行的操作进行实时响应。
    两个阶段：
      1.编译阶段：AngularJs会遍历整个HTML文档并根据JavaScript中的指令定义来处理页面上声明的指令。
       每一个指令的模板中都可能含有另外一个指令，另外一个指令也有可能会有自己的模板。当AngularJs调用HTML文档根部的指令时，会遍历其中所有的模板，模板中也有可能包含带有模板的指令。
       一旦对指令和其中的子模板进行遍历或编译，编译后的模板会返回一个叫做模板函数的函数。我们有机会在指令的模版函数被返回前，对编译后的DOM树进行修改。
       在这个时间点DOM树还没有进行数据绑定，意味着如果此时对DOM树进行操作只会有很少的性能开销。基于此点，ng-repeat和ng-transclude等内置指令对DOM进行操作。
      2.链接阶段：编译后的DOM传递给链接阶段
        一个指令的表现一旦编译完成，马上就可以通过编译函数对其进行访问，编译函数的签名包含访问指令声明所在的元素及该元素其他属性的方法。这个编译函数返回前面提到的模版函数，其中含有完整的解析树。 由于每个指令都可以有自己的模版和编译函数，每个模版返回的也都是自己的模版函数。链条顶部的指令会将内部子指令的模版合并在一起成为一个模版函数并返回，但在树的内部，只能通过模版函数访问其所处的分支。
      最后，模版函数被传递给编译后的DOM树中每个指令定义规则中指定的链接函数。
## 十一、多重视图和路由
    ng-view是由ngRoute模块提供的一个特殊指令，它的独特作用是在HTML中给$route对应的视图内容占位。
## 十二、$location
    用于以解析地址拦中的URL，并让你可以访问应用当前路径所对应的路由。还提供了修改路径和处理各种形式导航的能力。
## 十三、依赖注入
    angularJS使用$injector来管理依赖关系的查询和实例化。事实上，$injector负责实例化AngularJs中所有的组件，包括应用的模块、指令和控制器。
## 十四、创建服务
    factory: 创建和配置服务的最快捷方式
    service: 组册一个支持构造函数的服务
    provider: 所有服务工厂都是由$provider服务创建的，$provider服务负责在运行时初始化这些提供者。
    constant: 可以将一个已经存在的变量值服务注册为服务
    value：
    constant和value方法之间最主要的区别是，常量可以注入到配置函数中，而值不行。通常情况下可以通过value()来注册服务对象或函数，用constant()来配置数据

    decorator:
## 十六 XHR实践
    跨域和同源策略
      浏览器在全局层面禁止了页面加载或执行与自身来源不同的域的任何脚本。
      同源策略允许页面从同一个站点加载和执行特定的脚本。浏览器通过对比每一个资源的协议、主机名个端口号来判断资源是否与页面同源。
      cors:跨域资源共享。
      jsonp：一种可以绕过浏览器的安全限制，从不同的域请求数据的方法。jsonp的原理是通过<script>标签发起一个get请求来取代xrh请求。jsonp生成一个<script>标签插到DOM中，然后浏览器会接管并向src属性所指向的地址发送请求。
    身份验证：
      通过令牌授权来实现客户端身份验证，服务端需要做的是给客户端应用提供令牌。
    常见非状态码：
      200 正常
      401 未授权
      403 禁止的请求
      404 页面找不到
      500 服务器错误
##  十七、promise
    promise是一种异步方式处理值的方法
## 二十三、 digest循环和$apply
    在标准的浏览器流程中，当事件被触发时，浏览器会执行注册给该事件的回调函数。
    页面加载、$http请求返回响应、鼠标移动以及按钮点击等情况都会触发事件。
    当事件被触发时，JavaScript就会创建一个事件对象，并执行这个事件对象所在的监听特定事件的所有函数。然后它会运行JavaScript函数内的回调方法，这会回到浏览器中，还可能更新DOM。

    当Angular混入这个流程中时，它会扩展这个标准流程，创建一个Angular上下文。这个Angular上下文指的是运行在Angular事件循环内的特定代码，该Angular事件循环通常被成为$digest循环。
    $digest循环有两个主要组成部分：$watch列表、$evalAsync列表。
### $watch列表（$$watcher）
    每当在视图中追踪一个事件时，他会给注册一个回调函数，然后希望在页面中触发该事件时调用这个回调函数。
    $scope对象上的属性只会在其被用于视图时绑定。
    对于所有绑定给同一$scope对象的UI元素，只会添加一个$watch到$watch列表中。
    这些$watch列表会在$digest循环中通过一个‘脏值检查’的程序解析。
### 脏值检查
    检查值是否发生了变化，而整个应用还没有同步该变化
    Angular应用持续跟踪当前监控的值。Angular会遍历$watch列表，如果从旧值更新后的值没有发生变化，它会继续遍历监控列表。如果值发生了变化，该应用会启用新值并继续遍历$watch列表。
    Angular遍历完整个$watch列表，只要有任何值发生变化，应用将会退回到$watch循环中，直到检测到不再有任何变化。
    为什么要再次运行这一循环？因为如果更新了$switch列表中某个用于更新另一个值的值，Angular将检测不到更新，除非再次运行这个循环。
    ![脏值检查图](images/digest.png)
### $switch
    $scope对象上的$switch方法会给Angular事件循环内的每个$digest调用装配一个脏值检查。如果在表达式上检测到变化，Angular总是会返回$digest循环。
### 页面中的$digest循环
   通过ng-model指令在视图中绑定name，Angular会设置一个隐式的监听器，将这个输入的字段绑定为当前的$scope对象
