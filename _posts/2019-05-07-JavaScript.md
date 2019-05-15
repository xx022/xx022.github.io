---
layout: post
title:  "JavaScript相关"
date:   2019-05-07 09:37:21 +0800
tags:   前端
color: rgb(193,255,193)
cover: '../assets/lifetree.jpg'

---


##  JavaScript

### JavaScript设置或者获取所选内容的值

（1）text();设置或者获取所选元素的文本内容；

（2）html();设置或者获取所选元素的内容（包括html标记）；

（3）val();设置或者获取表单字段的值（前提是表单设置了value属性）；

（4）text()和html()的区别是：前者是处理的文本内容，只能写文本如果写了上面的标记则会以文本形式输出；后者可以解析文本中的html标记，如添加像<a></a>、<p></p>等标记，最后会解析为其效果。


### JavaScript解析json字符串并将其转换成数组读取

（1）通过eval() 函数可以将JSON字符串转化为对象
```
    var t="{'firstName': 'cyra', 'lastName': 'richardson', 'address': { 'streetAddress': '1 Microsoft way', 'city': 'Redmond', 'state': 'WA', 'postalCode': 98052 },'phoneNumbers': [ '425-777-7777','206-777-7777' ] }";
    var jsonobj=eval('('+t+')'); //转换之后，jsonobj变成了json对象
    alert(jsonobj.firstName); //可以通过对应的key进行获取值
    alert(jsonobj.lastName);
```

```
    var t2="[{name:'zhangsan',age:'24'},{name:'lisi',age:'30'},{name:'wangwu',age:'16'},{name:'tianqi',age:'7'}] ";
    var myobj=eval(t2);  //转换之后，jsonobj变成了装有json对象的json数组
    for(var i=0;i<myobj.length;i++){
        alert(myobj[i].name);
        alert(myobj[i].age);
    }
```

（2）parse方法和stringify方法

* parse():将json文本转换成一个json对象

* stringify():将一个json对象转换成json文本

```
  var jsonStr = '{"name":"张三", "age":"18"}';

  var jsonObject = JSON.parse(jsonStr);//将json字符串转换成json对象

  var jsonStringAgain = JSON.stringify(jsonObject);//将json对象转换成json字符串

```

（3）eval和parse

* eval和parse都可以将json字符串转换成json对象

```
    var jsonData = '{"data1":"Hello,", "data2":"world!"}';
    var evalJson = eval('('+jsonData+')');//可以通过evalJson.data1获取值
    var jsonParseJson = JSON.parse(jsonData);//也可以通过evalJson.data1获取值
```

* 但是二者方法的区别是：

```
    var value = 1;
    var jsonstr = '{"data1":"hello","data2":++value}';
    var data1 = eval_r('('+jsonstr+')');
    console.log(data1);//这时value值为2
    var data2 = JSON.parse(jsonstr);
    console.log(data2);//报错
```
eval解析json字符串时，会执行字符串的代码，这样json字符串的内容就改变了，所以使用eval应该要谨慎

* 总结: 在代码中使用eval是很危险的，特别是用它执行第三方的JSON数据（其中可能包含恶意代码）时，尽可能使用JSON.parse()方法解析字符串本身

<hr>
