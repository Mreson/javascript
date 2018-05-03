# 原生js讲义week1--初识js

@(<Inbox>)

[TOC]

---
如果学不下去请抄写诫子书：
夫君子之行，静以修身，俭以养德。非澹泊无以明志，非宁静无以致远。夫学须静也，才须学也，非学无以广才，非志无以成学。淫慢则不能励精，险躁则不能冶性。年与时驰，意与日去，遂成枯落，多不接世，悲守穷庐，将复何及

####1.什么是js
>JS(javascript):全栈开发脚本“编程语言”
>编程语言具备业务逻辑和逻辑思维，我们需要学习面向对象的编程思想，标记语言只需要记住基础知识即可，以后用的时候直接拿过来用，用的多了自然而然就会有一些合并的技巧

####2.js引用方式(分三种)
>1,行内引入(不推荐)，安全性能比较低 
```
<div id="div1" style="width: 100px;height: 100px;background:red" onclick="alert('点我哦~')">
```
>2,内嵌式 将JS代码写在script脚本块中间 
```
<script type="text/javascript">alert('勿忘初心，方得始终')</script>;
```
>3,外链式 将JS代码写在外面文件中，通过src找到引入(细节：1，在外链式，script脚本块中间不可以写js代码，写了也不执行。2，我们通常将js放在boby的最后面，原因：html页面通常是从上往下加载的，js通常是获取html标签给予动态操作效果的，所以需要先加载html标签再加载我们的js代码。)  
```
<script type="text/javascript" src="js/index.js"></script>
```
####3.JS的中常用的几种输出方式
>1.alert("内容"); ——浏览器的提示框：在浏览器中弹出框显示我们的内容(alert 输出的内容是字符串格式的，不管你写的是什么格式，最后输出的都是字符串 confirm prompt document.write 也是如此)
```
alert(1+1)=>'2' (字符串2)
alert({name:小明})=>'[object object]'
```
>2.confirm：浏览器的确认提示框，和ALERT相同，输出的也是字符串
>3.prompt：基于confirm基础上增加了输入框（可以让用户输入原因或者一些其它的内容）
>4.document.write("内容"); ——在页面中输出显示我们的内容(很少用了,举例：我们见过得小广告在屏幕在飘，这个就是我们以前是用这个实现得)
>5.console.log("内容")`最常用的一种方式`  .table以表格的形式输出 .dir输出更为详细的 ;  ——在控制台输出我们的内容 F12打开控制台 console的页卡中查看我们输出的内容(谷歌浏览器)，输出的内容可以是各种格式的数据

####4.控制台工具得简单了解(以后还会详细讲解)
>首先F12打开控制台
>  **Elements**：看到当前页面的HTML结构代码和对应的CSS样式，可以在这里快速样式，来观看效果
     **Sources**：当前网站的源代码（前端）
     **Network**：不仅仅可以看到所有的文件，而且还可以知道每一个文件加载额的时间，根据这个可以进行性能优化，有时候根据这个也可以调节BUG，
     **Application**：Frames->top->images 可以看到当前网站所有的图片，在这里可以看到所有本地存储的信息和内容
     **Console**：浏览器控制台，我们可以在这里输出一些内容（提示/BUG调试需要），这里还可以直接的写JS代码.
     
####5.innerHTML/innerText: 向指定元素中动态添加内容
>  **区别**：1.innerHTML支持添加标签，innerText不支持。
> 2.innerHTML没有兼容性问题，innerText火狐低版本不兼容

####6.JS的组成和命名规范
>`js组成`
>**浏览器(window浏览器对象)——>文档(document文档对象)——>html——>head/boby——>**
**js：javascript：是一门轻量级的脚本编程语言**
>**包含：**
>1）ECMAScript(4，5)：定义了js里面的命名规范，变量，	数据类型，基本语法，操作语句等最核心的东西
>2）DOM：document object model 文档对象模型
>3）BOM：browser object model 浏览器对象模型


>`命名规范`
>1) js中严格区分大小写 （test Test系统会辨识为两个不同的变量）
>2) 使用驼峰命名法
>3) 可以使用数字，字母，下划线，**注**：
>(数字不能作为首位，\$ doller符，_ 下划线在项目里面是有特殊意义的，代表特别的变量，例如_student，var $student，)

>**var 2num(ERROR:错误) / num2(OK)**

>4) 不能使用关键字和保留字:关键字：在js中有特殊意义的字，例如：var,保留字：未来可能成为关键字的字
>**命名小技巧：**
1，命名的时候不要使用拼音
2，命名的时候一些缩略单词
info / information: 信息
imp / import: 重要的
del / delete: 删除
add / create / insert : 增加
update: 修改
insert: 插入
create: 创建
rm / remove: 移动
cl / clear: 清空
query / get / select: 获取,查询

####7.JS的变量和数据类型
>`变量重点`
变量仅仅是一个名字,它本身没有特别的意义,我们提到变量,其实都是指的它所存储的值, 
例如：alert（num）->输出的结果是代表的值而不是num这个名字
>`定义一个变量：`
>ES5语法: 
(创建/定义)变量:var [变量名]=[变量值]； 
例如：var name=”12” 
ES6语法： 
创建变量:let [变量名]=值； 
创建常量:conset [常量名]=值；（conset是常量，值不可以修改） 
    **特别注释** " = " 是赋值操作:左边是变量名 右边是变量值。(见到一个"="就是赋值什么都不用想)。
```
例如： 
var name="初心"; 定义一个变量name， 
把"初心"赋值给这个变量【这是变量的存储值】name只是一个变量名，没有自己的实际意义，只是一个代表值和存储值东西， 
console.log(name); //初心
```
>`JS中的数据类型`
>js中的数据类型分类：
> 1).基本数据类型(简称：值类型)：数字（Number）,字符串(String),布尔(Boolean),null,undefind
```
num=12; /数字
str="小明"; /字符串：双引号，单引号包起来的都是字符串，
boo=true; true/ false
n=null; /空（没有）
m=undefined; /未定义（没有）
面试题讲解：null和undefind都是代表没有得意思为什么还要两个值呢，举例说明，小明(男)：1).将来会有女朋友现在没有，这个'没有'就是null。2).小明将来会有男盆友，现在没有，这个"没有"代表永远都不会有。
概括：null表是将来会有值，而undefined代表永远都不会有。
```
>2).引用数据类型：数组（Array）,对象(Object),函数(Function(){}),正则（RegExp）
```
{name:"小明"};  / object ——普通(传统)对象，
[1,2,3,4];  / array ——数组，
/^1\d{11}$/;  /RegExp ——正则表达式，
function(){}；  /——函数数据类型，
```
####8.数据类型详讲
>`number知识点`
1.nubmer数据类型包含: 正数,负数, 0,小数，NaN， 
特别记忆：NaN:not a number 不是一个有效数字 但是他是属于number数据类型的 
NaN==NaN 是不相等的 
false,NaN和本身比较是不相等,和其他任何一个值都不相等
=是赋值 
==是判断左右两边的值是否相等

>2，isNaN(); 检测一个值是否 不是有效数字，(如果结果是true，说明真的不是有效数字，反之，结果为false代表是一个有效数字，相当于检测一个值是不是NaN,)，是有效数字(意味着不是NAN,)返回false,不是有效数字(意味着是NaN)
```
//举例说明
console.log(isNaN(12)); /返回的是false，
console.log(isNaN("zhufeng")); /返回的是true，
```
>如果检测的值非number类型的，浏览器会默认的把它转化成number类型的，然后再验证是否为非有效的数字 
```
//举例
console.log(isNaN("123")); /首先把"123"转化成number类型的
Number==>Number("123")==>123
Number==>Number(12px)==>NaN
```
>3.number数据类型的转换
>1）Number()：把非数字类型的值转换为数字类型（强制转换），要求如果是字符串，字符串中一定都需要是数字才可以转换， 
2）非强制数据类型转换 parseInt / parseFloat 
parseInt：从左到右，一个个字符查找，把是数字的转换为有效的数字，中途如果遇到了一个非有效数字，就不在继续查找了， 
parseFloat：和上面一样，可以多识别一个小数点

```
//强制类型举例
Number("12")==>12
Number("12px")==>NaN
Number("true")==>1
Number("false")==>0
Number("null")==>0
Number("undefind")==>NaN
Number(" ")==>0
Number({name:'xxx'})==>NaN

//非强制类型举例
parseInt("12px")==>12 
parseInt("12px13")==>12 
parseInt("zhufeng2015") ==>NaN 
parseInt("12.5px") ==>12 
parFloat("12.5px") ==>12.5 
Number("12.5px") ==>NaN 
Number("12.5") ==>12.5 
```
`经典案例`
```
var val=Number("12px"); /val=NaN 
if(val==12){/val=NaN≠12 
console.log(12);
} else if(val=NaN){val=NaN≠NaN 
console.log(NaN);
}else{
console.log("以上都不成立");
} 
```
>4.string字符串
所有用 ’ ’ 或者 ” ” 包含起来的都是字符串 
1, 字符串有个属性叫 : length－－代表当前字符串中有多少个字符; 
2, [string].length : 获取当前字符串中有多少个字符; 
3,字符串中的每一个字符都有自己的位置,而且对应一个数字==>”索引”:索引从0开始, 
string[ 0 ] ==> 获取第一个字符 
string[ 1 ] ==> 获取第二个字符 
string[ string.length-1 ] ==> 获取最后一个字符 
string[ 索引 ] ==> 获取指定索引位置的字符

-
>5.null和undefined
1，null：空对象指针（没有）小明的女朋友 , 以后可能会有(更加倾向于以后肯定会有) 
2，undefined：未定义（没有）小明的男朋友 , 不出意外的话 , 常规是没有的,(更加倾向于以后肯定没有)

-
>6.boolean细节知识点
>boolean：true / false ——只有这两个值 
>1）！：一个叹号：首先将其他数据类型转换为布尔类型，再把转换的结果取反 
```
//一个叹号举例
console.log(!3); /先把3转换为boolean，然后再取反
```
>2）！!：两个叹号：将其他的数据类型转换为boolean类型，相当于Boolean( )，——【两个叹号是取反，再取反，相当于取正，】 
```
//两个叹号举例
console.log(Boolean("ming")); /返回true 
console.log(!!"ming"); /返回true
两个方式是一样的，只是后者看起来帅一些哦~
```
`对象数据类型`
>1.普通得对象{}
1)，一个对象由多组[属性名和属性值]组成，或者说：（专业叫法：多组键值对）组成，或者说：由多个key（属性名/键 ）：value（属性值/值），组成，
2)，属性名和属性值是用来描述这个对象特征的 
obj：变量名，也可以叫对象名，因为是定义的对象数据类型， 
name和age：属性名（key键） 
‘小明’和18：属性值（value值）
```
var obj={name：“xiaoming”，age：18}；
var personInfo={name：“小明”，age：18，height：“180cm”，weight：“60kg”}；
```
>3).创建对象得方式
```
//两种创建方式
var obj={name：“zhufeng”}； /字面量创建方式 
var obj=new Object（）； /实例创建的方式
```
>4).增删改查
```
obj.name的意思就是obj的name，【 . 】的意思就是【的】
1.给一个对象增加一组属性名和属性值
obj.name="xiaoming"；
obj["age"]=6；
2.修改原有属性名的属性值，规定一个对象中的属性名不能重复，如果之前有就是修改，没有就是增加
obj.name="小明"；
obj["name"]="哈小小明"；
3.获取属性名和属性值，如果属性名不存在，默认返回的结果是undefined
console.log（obj["name"]）； /返回zhufengpeixu
console.log（obj.name）； /返回zhufengpeixu
4.删除属性名和属性值
obj.age=null; ——假删除：把值赋值为null，但是该属性还存在－－KEY还在, 只是VALUE变成NULL,
console.log(obj); /返回{name:"xiaoming",age:null}
delete obj.age；——真删除：把KEY和VALUE在对象中都移除了
console.log(obj); /返回{name:"xiaoming"}
```
>2.[] 数组
```
var ary = [ 12, ’ JS ‘, false, null, undefined ]; 
0 : 12 
1 : ’ JS ’ 
2 : false 
3 : null 
4 : undefined 
length:5
数组的属性名是代表某一项位置的”索引”(索引是从零开始的),索引0
```

####9.基本数据类型和引用数据类型的区别
>var num1=12； 
var num2=num1； /把num1变量代表的值给了num2变量 
num2++ /相当于num2=num2+1 在自己原有值的基础上加1，也可以写成num2+=1，

>console.log(num1);/返回的是12，（基本数据类型无论怎么引用，修改都不会改变别人，每个数据是单独分开的，）

>var obj1={name:”小明”,age:6}; 
var obj2=o1 
obj2.name=”小红”； 
console.log(obj2.name); /返回的是：小红；（引用数据类型，是共用一个数据，引用的数据的地址，任何一个变量改变值，都会改变公用数据的值，
![Alt text](./1525230510964.png)
>基本数据类型：
是把值直接的给变量，接下来在操作的过程中，直接拿这个值操作的，可能两个变量存储一样的值，但是你的是你的，我的是我的，之间没有关系，其中一个改变，另外一个没有任何的影响

>引用数据类型：
1）定义一个变量
2）开辟一个新的(内存)空间，然后把属性名和属性值保存再这个空间中，并且有一个空间地址
3）把空间的地址给了这个变量，变量并没有存储这个数值，而是存储的这个空间的引用地址
4）接下来我们把这个地址，又告诉给了另外一个变量，另外一个变量存储的也是这个地址，此时两个变量操作的是同一个空间（不是操作各自的值，而是操作的同一个空间里同一个值——共用）
5）其中一个改变了这个空间的内容，另外一个用的也是这个改变后的内容

>两者的本质区别：
>基本数据类型操作的是值，而引用数据类型操作的是共用引用的那个公共空间，

面试题：
```
var obj1={num:12};
    var obj2=obj1;
    obj2={num:13};
    console.log(obj1.num);
```

####10.数据类型得转换
>1,如果只有一个值，判断这个值是真还是假，遵循：**只有0 NaN ” ” null undefind** 这五个是假的，其余的都是真
2，如果是两个值比较是否相等，遵循这个规则： 
val1==val2 两个值可能不是同一个数据类型的，如果是==比较的话，会进行默认的数据类型转换：
```
`黄金法则`
1）对象对象：永远不相等 
2）对象字符串：先将对象转换为字符串（调用toString的方法：对象.toString()），然后再进行比较 
[]转换为字符串：" "（空数组代表一个空字符串） 
{}转化为字符串：[object Object]"（空对象） 
3）对象布尔类型：对象先转换为字符串，然后再把字符串转换为数字（调用Number的方法，空字符串Number(” “)=0），布尔类型转换为数字（true是1，false是0），最后让两个数字比较 
4）对象数字：对象先转换为字符串，然后把字符串在转换为数字 
5）数字布尔：布尔转换为数字 
6）数字字符串：字符串转化为数字 
7）字符串布尔：都转换为数字 
8）nullundefined：结果是true 
9）null或者undefined 和其他任何的数据类型比较都不相等
```
>3，除了是比较，===也是比较（绝对比较） 
val1===val2：如果数据类型不一样肯定不相等 
```
//举例
0==false /返回true
0===false /返回false
null==undefined /返回true
null===undefined /返回false
```
#### 11.JS中检测数据类型的方式
>1，typeof 用来检测数据类型的逻辑运算符
2，instanceof 检测某一个实例是否属于这个类
3，constructor 通过构造函数检测
4，Object.prototype.toString.call( )最常用的,借用Object基类原型上的toString方法,在执行这个方法的时候,让方法中的THIS指向需要检测的值,从获取到当前值所属的类,(从而)检测出对应的数据类型
typeof用来检测数据类型的：【typeof 值】 
返回值：是一个`字符串`，包含了数据类型字符： 
“number”，”string”，”boolean”，”undefined”，”object”，”function”

`特殊记忆：`
>**typeof null的结果是"object"**
**typeof{} [] /^$/ 返回的结果全是"object**
**typeof的局限性：不能具体的检查object下细分的类型，检查这些返回的都是"object"**
**typeof function(){} /返回的是"function"**
null instanceof Null报错 Null is not a defined
undefined instanceof Undefined报错 Undefined is not a defined
Object.prototype.toString.call(null)//'[object Null]'
Object.prototype.toString.call(null)//'[object Undefined]'的原型上都有toString方法，这些方法把队形的值转换成字符串
`Number String Boolean Function Array RegExp`

```
var num2=12;
console.log(typeof num2);  /把num2代表的值进行检测，检测是什么数据类型的，
```
**面试题**
```
console.log(typeof (typeof (typeof (typeof[]))))；
返回的结果是：typeof "object"==>"string"
                          typeof "string"==>"string"

typeof两个以上返回结果全部都是"string"
```

#### 12.js中的判断语句
>1，if，else if else 
if（条件）{//条件1成立执行的语句} 
else if（条件2）{//条件1不成立，条件2成立，执行的语句} 
else if（条件3）{以上条件不成立，条件3成立，执行的语句} 
。。。 
else{//以上条件都不成立执行的语句}
`每一个if，else，if else 都是拿==在比较`
```
//举例说明
var num=12
if(num>0){
console.log(12);
}
else if(num<0){
console.log(20);
}
else{
console.log(以上都不成立)；
}
```
>2，三元运算符
```
var num=12;
num>0?num++:num--;
console.log(num);
```
>**3，switch case**
>`>每一个case情况的比较都是拿===在比较  `
```
switch（变量）{
              case 1：
              如果值是1的话，做这些事情
              break；//中断结束
              case 10：
              如果值是10的话，做这些事情
              break；
              。。。
              default：
              以上都不成立，执行这个
              }
```
#### 13.循环
>1，for循环
for(设定初始值；设置循环的条件；设置累加的步长){
//->循环体：每一次重复做的事情都放在这里
}

>循环的四部曲：
1，设置初始值
2，验证是否循环的条件
3，条件成立执行循环体中内容，不成立结束循环
4，执行步长累加的操作

>循环体中会出现两个关键字：
continue
break
循环体中出现了这两个关键词，循环体关键词后面的代码都不再执行了；遇到break，整个循环都终止结束了，遇到continue当前这一轮循环结合了，继续执行下一轮循环即可，
```
for ( var i = 0 ; i < 5 ; i + + ) {
i<5?i++:null; /条件不成立我们什么都不做（不写null不符合三元运算符的语法）
break;    
console.log(i);   
}

//例子1
 for(var i=0;i<10;i++){
    if(i<5){
      i+=2;
    }else{
      i+=3;
    }
    console.log(i);
 }
 console.log(i);//2,5,9,10

  for(var i=0;i<10;i++){
     if(i<5){
       i+=2;
       continue;
     }else{
       i+=3;
       break;
     }
     console.log(i);
  }
  console.log(i);//->9

```

2，for in循环
>用来遍历一个对象中所有键值对的
 
> 变量名经常使用 key/attr ，当前设置其他的名字也可以，因为这个变量每一次循环存储的值都是obj这个对象的属性名


```
for（var key in obj）{
      / obj 中有多少组键值对，我们就循环多少次
      key => 键
      obj[key] => 值
```

3.while循环

>  **while(条件) { //->只要条件成立就会一直执行循环体中的内容 }**
```

for(var i=0 ; i<4 ;i++)
{
console.log(i);
}

//把for改成while
var i=0;
while(i<4){
console.log(i);
i++;
}
```
####14.案例开关灯
>[元素].onclick=function(){ 
给当前的某一个元素绑定点击事件,当点击这个元素的时候执行后面的方法}
>1,首先
>window.document.body:获取HTML页面中的BODY（window可以省略）

>元素 .style来获取元素的样式值，只能获取写在元素行内样式上的样式属性值，不写或者写在样式表中的样式值获取不到（如果想要获取需要使用getComputedStyle/currentStyle）;
```
var oBody=document.body;
oBody.onclick=function(){
 var bgColor=oBody.style.backgroundColor;
 oBody.style.backgroundColor = bgColor ==="white" ? "black" : "white" ;
};
```




#### 15.案例隔行变色
>**1，首先**
>// 分析规律和需要处理的业务逻辑：
让每一个 li 按照一定的规律添加class即可（奇数行+bg1，  偶数行+bg2）
**2，想要操作哪些元素，先获取到它**
// 想操作谁，先获取谁：我们需要获取 outlineBox 中的所以的 li 
**3，按照之前分析的步骤，一步步去实现即可；**
每一次循环，把变量 i 存储的值（0，1，2，，，）作为索引，到集合中获取到指定的li，而找到的li正好
>context.getElementsByTagName([标签名])：在指定的上下文中 (context-> 限定获取的范围) 通过元素的标签名获取一组元素
>var oList = outlineBox.getElementsByTagName('li')
>//oList：它是一个类数组集合（类似数组但是不是数组）
>以数字作为索引，索引从零开始，每一个索引代表某一个li，例如：0—>第一个li； 3—>第四个索引；  n-1—>第n+1个li； length-1—>最后一个li的索引；
>oList.length:获取集合的长度

>`小知识`console.log(1+'1');   返回：'11'在JS中遇到了加号，如果有一头是字符串，则代表的不是数字相加，而是字符串拼接

```
//代码实现
css
 <style>
        ul{
            width:500px;
            margin:0 auto;
        }
        li{
            list-style: none;
        }
        .bg1{
            background:lightgoldenrodyellow;
        }
        .bg2{
            background:lightblue;
        }
  </style>
  
  html
  <ul>
    <li>夫君子之行，静以修身，俭以养德。</li>
    <li>非澹泊无以明志，非宁静无以致远。夫学须静也</li>
    <li>才须学也，非学无以广才，非志无以成学。</li>
    <li>淫慢则不能励，险躁则不能冶性</li>
    <li>年与时驰，意与日去，遂成枯落，多不接世，</li>
    <li>悲守穷庐，将复何及！</li>
    <li>夫君子之行，静以修身，俭以养德。</li>
    <li>非澹泊无以明志，非宁静无以致远。夫学须静也</li>
    <li>才须学也，非学无以广才，非志无以成学。</li>
    <li>淫慢则不能励，险躁则不能冶性</li>
    <li>年与时驰，意与日去，遂成枯落，多不接世，</li>
    <li>悲守穷庐，将复何及！</li>
</ul>
var oLis=document.getElementsByTagName('li');
for (var i = 0; i < oLis.length; i++) {
	 var item = oLis[i];
     i%2===0?item.className='bg1':item.className='bg2';
 }
```
####16.函数
>函数有两部分：1，创建一个函数（购买了一台洗衣机） 2，执行函数（使用洗衣机洗衣服）
>**创建函数：**
1，创建一个函数名
2，开辟一个新的内存空间（有16进制地址），然后把函数体中实现功能的JS代码按照"字符串"的格式存储在空间中(对象存储的是属性名和属性值)
3，把空间地址赋值给函数名,此时函数名就可以和函数体本身关联在一起了

>**函数执行:**
1,函数执行的时候会形成一个私有的作用域(我的地盘我做主),提供一个环境供函数体中的代码执行 (里面创建的变量跟外面没有关系,叫 : 私有变量)
2,把创建的时候存储的字符串变为真正JS代码,在私有地盘中自上而下执行

>创建函数实现某一个功能的时候,我们发现所需要的原材料不够,需要用户执行方法的时候传递给函数才可以,此时我们可以模仿洗衣机,提供给用户几个入口==>"形参":变量

>用户执行的时候会给几个入口传递内容==>"实参": 值
``` 
function 函数名（）{
——函数体：我们把实现当前功能或者需要做事情的代码，全部的放在函数体中
}
例如：

function sum（）{

}
sum()；
sum()；
sum()；//把上面的方法执行，而且可以执行很多次
sum;//代表的就是函数本身
```
>函数其实就是一个方法或者一个功能，使用它能够做某些事情，
例如：我们可以把家里边的洗衣机理解为函数，使用它可以洗衣服

>**函数的作用:把实现一个功能的代码进行封装(封装成一个函数),以后再想实现这个功能,只需要执行函数即可,无需重复编写代码=>封装**
>**`低耦合，高内聚:减少页面中的冗余代码,提高代码的重复利用率`**

toFixed
```
var total = 168.3642 + 247.5621;
total = total.toFixed(2); /==>toFixed:保留小数点后面两位,得到的结果是字符串格式的 console.log(total);
```
####17.全局作用域

>当浏览器加载页面的时候,会给JS提供一个运行的环境,我们把这个环境称之为"全局作用域"(window--前端/global--后台)

>JS代码自上而下执行
>所有引用数据类型赋值操作的步骤 : 
1, 创建一个新的变量
2, 开辟一个新的内存空间(空间有一个16进制地址),然后依次把我们的"属性名和属性值"存储到这个内存空间中
3, 把内存空间的地址赋值给变量

>**引用数据类型(的变量)不是按值操作的, 操作的是对内存空间的引用地址, 是 " 按引用地址 " 操作的 "
**基本数据类型(的变量)是按值操作的,——基本数据类型也叫 " 值类型 "

#### 18.获取文档中的元素
```
window:浏览器对象 
document:文档对象
//通过id获取一个元素
var lampLink = window.document.getELementById([id])
//通过class类名获取一组元素
var element = document.getElementsByClassName([class]);
//通过标签名获取一组元素
var oList = docuemnt.getElementsByTagName([标签名]); 
//获取body
window.document.body==>document.body window 可以省略
```
