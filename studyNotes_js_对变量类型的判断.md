# JS对变量类型的判断[参考](https://segmentfault.com/a/1190000002962215)

在JS中，有5种基本数据类型和1种复杂数据类型，基本数据类型有：undefined，Null，Boolean，Number和String;复杂数据类型是Object
Object中还细分了很多具体类型，比如：Array，Function，Date等等。下面是使用什么方法判断出变量的类型

在讲解各种方法之前，我们首先定义出几个测试变量，我们看看后面的方法究竟能把变量的类型解析成什么样子，以下是常用的几种变量：
      
      (1) var num=123;
      (2) var str='abc';
      (3) var bool=true;
      (4) var arr=[1,2,3];
      (5) var json={name:'abc',age:25};
      (6) var func=function(){console.log('this is function');};
      (7) var und=undefined;
      (8) var nul=null;
      (9) var date=new Date();
      (10) var reg=/^[a-zA-Z]{5，20}$/;
      (11) var error=new Error();

**1.使用typeof检测**

      打印上述的变量
```
        console.log(
            typeof num,   //number
            typeof str,   //string
            typeof bool,    //boolean
            typeof arr,   //object
            typeof json,    //object
            typeof func,    //function
            typeof und,    //undefined
            typeof nul,   //object
            typeof date,    //object
            typeof reg,   //object
            typeof error    //object
        );
```
      由上述可知，typeof是区分不出array和json类型的。
      
**2.使用instance检测**
  
  在JS中，判断一个变量的类型常常会用typeof运算符，在使用typeof运算符时，采用引用类型存储值会
  出现一个问题，无论引用的是什么类型的对象，它都返回“object”。ECMAScript引入另一个JAVA运算符
  instanceof来解决这个问题。instanceof运算符与typeof运算符相似，用于识别正在处理的对象的类
  型。与typeof方法不同的是，instanceof方法要求开发者明确确认对象为某特定类型，例：
```
      function Person(){}
      var Tom=new Person();
      console.log(Tom instanceof Person);   //true
      
      function Person(){}
      function Student(){}
      Student.prototype=new Person();
      var John=new Student();
      console.log(John instanceof Student);   //true
      console.log(John instanceof Person);    //true    
```
      instanceof还能检测出多层继承的关系

      用instanceof检测上述的变量
```
      console.log(
        num instanceof Number,  //false
        str instanceof String,  //false
        bool instanceof Boolean,  //false
        arr instanceof Array,   //true
        json instanceof Object,   //true
        func instanceof Function,  //true
        und instanceof Object,  //false
        nul instanceof Object,  //false
        date instanceof Date,   //true
        reg instanceof RegExp,  //true
        error instanceof Error  //true
      );
```
      从上面运行结果可知，num，str，和bool没有检测出它们的类型，但是当使用构造函数的方法时，
      是可以检测出类型的。

      同时，und和nul是检测的Object类型，才输出true,因为js中没有Undefined和Null这种全局类型，

**3.使用constructor检测**

      在使用instanceof检测变量类型时，我们检测不到number，String和Boolean类型，因此用另一
      种方法检测

      constructor本来是原型对象上的属性，指向构造函数。但是根据实例对象寻找的可向上检索机制，
      所以，实例对象也是可以使用constructor属性的。(注：undefined和null没有constructor属性)

      上述变量再次输出：
```
    console.log(
        num.constructor==Number,  //true
        str.constructor==String,  //true
        bool.constructor==Boolean,  //true
        arr.constructor==Array,   //true
        json.constructor==Object,  //true
        func.constructor==Function,   //true
        date.constructor==Date,   //true
        reg.constructor==RegExp,  //true
        error.constructor==Error  //true
    );
```
      使用constructor有一个缺点：constructor属性可以被修改。例如：
      当被检测的对象的原型指向另一个对象时，则检测不出该对象的类型.

      注：使用instanceof和constructor来判断array时，array必须是在当前页面声明的！
      原因：(1) array属于引用型数据，在传递过程中，仅仅是引用地址的传递；
           (2) 每个页面的Array原生对象所引用的地址是不一样的，在子页面声明的array，其构造
               函数是子页面的Array对象；父页面来进行判断，使用的Array并不等于子页面的Array。

**4.使用Object.prototype.toString.call**

      ECMA里的定义Object.prototype.toString的行为：首先，取得对象的一个内部属性[[Class]]，然
      后依据这个属性，返回一个类似于”[object Array]“的字符串作为结果（看过ECMA标准的应该都知道，
      [[]]用来表示语言内部用到的、外部不可直接访问的属性，称为“内部属性”）。利用这个方法，再配合
      call，我们可以取得任何对象的内部属性[[Class]]，然后把类型检测转化为字符串比较，以达到我们
      的目的。
```
    console.log(
        Object.prototype.toString.call(num),  //[object Number]' 
        Object.prototype.toString.call(str),  //[object String]'
        Object.prototype.toString.call(bool), //[object Boolean]'
        Object.prototype.toString.call(arr),  //[object Array]' 
        Object.prototype.toString.call(json), //[object Object]'
        Object.prototype.toString.call(func), //[object Function]'
        Object.prototype.toString.call(und),  //[object Undefined]' 
        Object.prototype.toString.call(nul),  //[object Null]'
        Object.prototype.toString.call(date), //[object Date]' 
        Object.prototype.toString.call(reg),  //[object RegExp]'
        Object.prototype.toString.call(error) //[object Error]'
    );
```
**5.jQuery中$.type的实现**
      
      在jQuery中提供了一个$.type的接口，例：
```
  console.log(
        $.type(num),  // number 
        $.type(str),  // string 
        $.type(bool), // boolean 
        $.type(arr),  // array
        $.type(json), // object 
        $.type(func), // function
        $.type(und),  // undefined 
        $.type(nul),  // null  
        $.type(date), // date 
        $.type(reg),  // regexp 
        $.type(error) // error     
  );
```
      除了"object"和"function"类型，其他的类型则使用typeof进行检测。即number, string,
      boolean类型的变量，使用typeof即可。 
