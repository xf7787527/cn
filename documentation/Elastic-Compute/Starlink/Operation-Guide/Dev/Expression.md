# 表达式语法
目前星链平台支持的表达式是Aviator Script，AviatorScript的完整文档可参考[AviatorScript编程指南(5.0)](https://www.yuque.com/boyan-avfmj/aviatorscript/cpow90)  
在星链中，表达式用于：
1. 给输入参数赋值
2. 条件表达式

表达式支持：
> - 表达一个常量
> - 访问环境变量
> - 访问请求入参
> - 访问前面节点的执行结果
> - 构造一个集合对象（包含List，Map等），支持丰富的集合运算
> - 支持若干内置函数
> - 支持使用条件/循环进行运算
> - 支持使用函数
> - ......
## 表达式极简说明
```JavaScript
//内置变量
env.jdbcUrl //访问环境变量，前缀env.
req.pin //访问请求入参，前缀req.
state.node1.result //访问节点输出，前缀state.{nodeAlias}.
 
//字符串
"hello world" //常量字符串，双引号
'hello world' //常量字符串，单引号
req.pin + "hello" //字符串拼接
req.pin != nil //判断是否为空
//比较/逻辑运算 ==, !=, !, >, >=, <, <=, &&, || 
req.pin != nil && state.node1.code == '0000'
req.pin != nil ? req.pin : 'tester' //三元运算符
 
//List
seq.list(1, 2, 3) //创建List
count(list) //list长度
list[0] = 100 //访问list成员
 
//Map，创建seq.map(k1, v1, k2, v2, ...)
seq.map("a", 1, "b", 2, "c", 3)
map.a //访问键a
map["a"] //另一种访问键a语法
 
//日期
sysdate() //返回当前日期对象 java.util.Date
now() //返回 System.currentTimeMillis() 调用值
//日期-字符串格式转换   
date_to_string(sysdate(),'yyyy-MM-dd HH:mm:ss') 
string_to_date('2021-10-20 20:15:19','yyyy-MM-dd HH:mm:ss')
```
## 更多说明
| 场景         | 用法         | 示例        |
|--------------|--------------|-------------|
| 访问请求入参 | 通过req.前缀 | req.orderId |
| 访问环境变量 | 通过env.前缀 | env.jdbcUrl |
| 访问节点输出 | 通过state.{nodeAlias}.前缀 | state.node1.result.data |
| 字符串常量 | 单引号或者双引号括起来 | "hello world"  或者 'hello world' |
| 判断字符串是否相同 | ==, != | state.node1.result.code == "0000" |
| 字符串拼接 | 使用+ | "hello" + "world" |
| 判断变量是否为null | 与nil比较 | if a == nil |
| 正则表达式 | / / 括起来<br>匹配用 =~ 运算符 | let p = /^(.*)\.av$/ <br> "regexp.av" =~ p |
| 加减乘除和取模 | +,-,*,/,% |  |
| 布尔类型和逻辑运算 | >,>=,<,<=,==,!=,&&,!x |  |
| 三元运算符 | test ? stmt1: stmt2  |  |
| 访问对象属性 | 通过.访问 | a.b.c |
| 数组元素为对象，访问其属性 | 前缀加# | #foo.bars[1].name |
| 注释 | 连续的两个# | ## 这是一行注释 |
| 定义局部变量 | 使用let | let a = 1; |
| 多行表达式 | 以分号;隔开整体返回结果是最后一个表达式的结果，不加分号。或者最后调用return并加上分号 | let a = 1;<br>let b = 2;<br>c = a + b<br>或者最后一行为：<br>return a+b; |
| 条件语句 | 使用if / elsif / else,代码块都必须用大括号包起来，if后面连着的表达式的括号可以忽略 | let a = rand(1100);<br>if (a > 1000) {<br>println("a is greater than 1000.");<br>} elsif a > 100 {<br>println("a is greater than 100.");<br>} else {<br>println("a is less than 100 ");<br>} |
| 循环 | for, while | for i in range(0, 10) {<br>println(i);<br>}<br>let sum = 1;<br>while sum < 1000 {<br>sum = sum + sum;<br>} |
| 异常处理 | try / catch / finally | try {<br>throw "an exception";<br>} catch(e) {<br>pst(e);<br>} finally {<br>p("finally");<br>} |
| 函数 | fn | fn add(x, y) {<br>return x + y;<br>} |
| List | 创建：seq.list<br>遍历：for<br>元素个数：count<br>访问：[] | let list = seq.list(1, 2, 3);<br>for x in list {<br>println(x);<br>}<br>println("元素个数 "+ count(list));<br>list[0] = 100;<br>println("list[0] = " + list[0]); |
| Map | 创建：seq.map(k1, v1, k2, v2 ...)<br>访问：用 m.{key} 的方式来访问，也可以使用类似数组的语法 map[key]<br>keys：seq.keys(m) 函数<br>values：用 seq.vals 函数 | let m = seq.map("a", 1, "b", 2, "c", 3, 4, 5);<br>println("m.a = " + m.a);<br>m["a"] = 'aviator';<br>p("key set: " + seq.keys(m));<br>p("value set: " + seq.vals(m)); |
| 构造复杂对象 | 对象用seq.map()，数组用seq.list，如构造：<br>{<br>"name": "zhangsan",<br>"age": 10,<br>"orders": [<br>{"id": "10001", "totalPrice": 100},<br>{"id": "10002", "totalPrice": 100}<br>]<br>} | seq.map(<br>"name", "zhangsan",<br>"age", 10,<br>"orders", seq.list(<br>seq.map("id", "10001", "totalPrice", 100),<br>seq.map("id", "10002", "totalPrice", 100)<br>)<br>) |