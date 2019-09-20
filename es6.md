[TOC]

















### 变量

#### var：

- 可以重复声明
- 无法限制修改
- 没有块级作用域

#### let：

- 不能重复声明，变量可以修改，块级作用域

#### const:

- 不能重复声明，常量不可修改，块级作用域





### 函数---箭头函数

原函数：function 名字(){

}

箭头函数：()=>{

}//去掉function,再在括号后加=>;函数的简写形式

#### 特殊情况

- 如果只有一个参数，()可以省
- 如果函数中只有一个return语句，{}可以省

#### 例子

- window.onload=function(){

  alert('abc')

  }

  window.onload=()=>{

  alert('abc')

  }

- 带参数形式

  let show=function(a,b){

  alert(a+b)

  }

  show(12,6)

  等于

  let show=(a,b)=>{

  alert(a+b)

  }

- 特殊情况

  let show=function(a){

  return a*2

  }

  alert(show(12))

  箭头函数：

  let show=a=>a*2;



### 函数的参数

#### 参数扩展

1. ##### 收集参数：

   function show(a,b,...args){}

      ****Rest Parameter必须是最后一个

   ###### 例子：

   ​      function show(a,b,...args//*后面不能在接参数*){

   ​          alert(a);

   ​          alert(b);

   ​         alert(**args**);

   ​    }

      show(12,15,**6,9,10**)//args中存的内容就是6,9,10

2. ##### 展开数组:

   var arr=[1,2,3]

   ...arr=>1,2,3

   ****展开后的效果，跟直接把数组中的内容写在这儿一样

   ###### 例子：

   ​    let arr=[1,2,3]

   ​    show(...arr)//等价于show(1,2,3)

      function show(a,b,c)

     {

   ​      alert(a);

   ​      alert(b);

   ​      alert(c);

     }

3. ##### 例子：

   function show(...args//收集参数){

   ​      fn(...args//展开成数组);

   }

   function fn(a,b){

   ​     alert(a+b);

   }

   show(12,5)

#### 默认参数

function show(a,b=5,c=12){

console.log(a,b,c)

}

show(80)//当没有b,c的实参时则输出默认参数5,12若有b,c的实参，则输出相应的实参



### 解构赋值

1. 左右两边结构必须一样

2. 右边必须是合法的语句

3. 声明与赋值不能分开（必须在一句话里完成）

4. 例子：

   let [a,b,c]=[12,5,8]

   let {a,b,c}={a:12， b:5，c:8}

   let [{a,b}, [p1,p2], num, c]=[{a:8, b:4}, [2,4], 2,'str'] 









### 数组

#### 1.map 

**映射   ===> 一个对一个**

​       例如：[12,     58,   99,   86,   45,   92]

​                [不及格，不及格，及格，及格，不及格，及格]

##### 例：

1. let arr=[12, 5, 8];

   let result=arr.map(function(item)//`item是参数，接受arr中的值`

   {

   ​      return item*2;

   })

   alert(result);

2. let score=[19, 85, 99, 25, 67]

   let result=score.map(item=>item>=60?'及格':'不及格')；

   alert(result);

#### 2.reduce

**汇总====>一堆出来一个**//`算平均值或总和``（三个参数）`

##### 例：

1.  let arr=[12, 69, 180, 8763]

   let result=arr.reduce(function(**temp**//`中间结果(第一位数默认为中间结果 )`, **item**//`做加法时的下一次需要加的数` , **index**//`循环次数`)

   {

   ​      return temp+item;

   })

   alert(result);

   ![56499160864](C:\Users\DELL\AppData\Local\Temp\1564991608648.png)

2. 求平均值：

   let arr=[12, 69, 180, 8763]

   let result=arr.reduce(function(temp，item ，index）

   {

   ​      if(index!=arr.length-1){

   ​           return temp+item

   ​     }else{

   ​            return(temp+item)/arr.length

   ​     }

   });

   alert(result);

#### 3.filter

**过滤器**

##### 例：

1. let arr=[12,5,8,99,27,36,75,11]

   let result=arr.filter(item=>{

   ​      if(item%3==0){

   ​             return true;

   ​      }else{

   ​             return false;

   ​      }

   })

   alert(result);

#### 4.foreach

**循环（迭代）**

##### 例：

1. let arr=[12,5,8,9]

   let result=arr.forEach((item, index)=>{

   ​      alert(index+': '+item);

   });

   alert(result);




### 字符串

#### startsWith

***`用于判断字符串的开头或者网址的的类型`***

例：let str='<https://www.baidu.com/>'

​        if (str.startsWith('https://')){

​                alert('普通网址')

​         }else if(str.startsWith('https://')){

​                alert('加密网址')

​         }else{

​                 其他

​          }

#### endsWith

`用于判断字符串的结尾`

例:    let str ='1.txt'

​         if(str.endsWith('.txt')){

​                alert('文本文档')

​        }  else if(str.endsWith('.jpg')){

​                alert('图片文档')

​       }else{

​               alert('其他')

​        }

#### 字符串模板

`用于连接字符串`

符号：${};

例：let a=12;

​        let str=`a${a}bc

​        alert(str)//`a12bc`

​         



### 面向对象

`**class关键字、构造器与类分开**`

`**class里面直接加方法**`

- **js写法**：

  function User(name, pass){

  ​      this.name=name;

  ​      this.pass=pass;

  }

  User.prototype. showname=function(){

  ​       alert(this.name)

  }//`blue`

  User.prototype. showpass=function(){

  ​       alert(this.pass)

   }//`12344`

  var u1=new User(blue,12344)

  u1.showname()

  u1.showpass()

- **es6写法：**

  class User{

  ​      constructor(name ,pass){

  ​             this.name=name;

  ​             this.pass=pass;

  ​      }

  ​      showname(){

  ​             alert(this.name) 

  ​      }

  ​       showpass(){

  ​               alert(this.pass)

  ​       }

  }

  var u1=new User(blue,12344)

  u1.showname()

  u1.showpass()

- **继承写法**：

  class User{

  ​      constructor(name ,pass){

  ​             this.name=name;

  ​             this.pass=pass;

  ​      }

  ​      showname(){

  ​             alert(this.name) 

  ​      }

  ​       showpass(){

  ​               alert(this.pass)

  ​       }

  }

  class VipUser extends User{

  ​       constructor(name, pass, level){

  ​              super(name, pass);//`代表调用user的`                                 

  ​              `构造函数`

  ​             this.level=level//`自身的属性`

  ​       }

  ​        showLevel(){

  ​               alert(this.level)

  ​        }

  }

  var v1=new User(blue,12344,2)

  v1.showname()//`blue`

  v1.showpass()//`12344`

  v1. showLevel();//`2`

  ​

  ​

​      

   





