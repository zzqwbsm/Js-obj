# Js-obj
##  对象

 - 对象是js的一种数据类型，对应的以一种“名/值”的形式存储数据的结构。
 - js的对象具有继承的属性，可以从一个称为“原型”的对象中继承属性。“原型式继承”也是js的核心属性。
 - js的对象是动态的 
 - 除了基本数据类型（numder,string,boolean,null,undefined）以外都是对象，甚至numder,string,boolean和不可变对象都非常相似。
 - 对象具有 创建、设置（set）、查找（query）、删除（delete）、检查（test）和枚举（enumerate）等用法。
 - 对象不能存在两个同名的属性，每个属性还具有“可写”、“可枚举”、“可配置”的‘属性特性’。
 可写：是否可以设置属性值。
 可枚举：是否可以通过for/in循环返回属性。
 可配置：是否可以删除或者修改该属性。
 - 对象都具有“对象原型”、“对象的类”、“对象的扩张标记”的‘对象特性’。
 对象原型：本对象的属性继承自本对象的原型对象。
 对象的类：是一个标示对象类型的字符串。
 对象的扩展标记：是否对该对象添加新属性。
 - js的3对象2属性
 内置对象：ECMAScript规范定义的对象：数组、函数、日期、正则表达式。
 宿主对象：浏览器厂商定义的，兼容性的坑爹！
 自定义对象：编程人员自己定义创建的对象。
 自有属性：直接在对象中定义的属性。
 继承属性：对象原型中定义的属性，可继承给对象。

[图解原型链](http://www.cnblogs.com/shuiyi/p/5305435.html)
[图解原型链-简书](http://www.jianshu.com/p/aa1ebfdad661)

获得对象原型的两种方法
```javascript
function F(){};
var foo = new F();
alert(foo.__proto__ == F.prototype);//IE11才支持
alert(foo.constructor.prototype == F.prototype);
```

### 创建对象

#### 创建对象直接量
```javascript
  var obj1 = {};
  var obj2 = {x:13 , y:"駂"};
  var obj3 = {x:obj2.x , y:obj2.y};
  var book = {
    "title":"zzq钨丝城堡",
    "for":"all person",
    author:{
      firstname:"z",
      lastname:"zq"
    }
  };
```

#### new创建对象
使用new去通过构造函数（对象的模板）来构建一个对象。js中原型类型都包含了内置构造函数。
```javascript
  var o = new Object();
  var a = new Array();
  var d = new Date();
```
还可以通过自定义构造函数来初始化新对象。
```javascript
  function my_obj(){
    this.value = 122;
  }

  var my1 = new my_obj();
  console.log(my1.value);
```

#### 原型
1、每个对象都有一个继承自本对象的原型对象（Object.prototype）。
2、如果你是通过直接量{} 或者 通过new Object()创建，这个对象都继承自 Object.prototype。又如果你是通过 new Array()创建的对象就是继承自Array.prototype。
3、基本上所有的对象（内置对象）都是继承自Object.prototype，所以Object没有原型。
4、通过 new Array()创建的对象就是继承自Array.prototype。而Array对象有继承自Object.prototype，这样就形成了“原型链”。
[js的类方法、对象方法、原型方法](http://www.cnblogs.com/yjf512/archive/2011/06/03/2071914.html)
