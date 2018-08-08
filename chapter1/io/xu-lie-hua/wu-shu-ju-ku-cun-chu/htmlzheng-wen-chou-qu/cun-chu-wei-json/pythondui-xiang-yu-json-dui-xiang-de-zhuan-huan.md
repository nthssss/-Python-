# Python对象与JSON对象的转换。
--- 
## 介绍
1. 编码:Python对象转换为JSON对象（dump、dumps）:
    - dump:
        1. 把Python对象转换成JSON对象，
        - 将JSON对象通过fp文件流写入文件中；
    - dumps：生成一个字符串。

- 解码：JSON对象转换成Python对象（load、loads,区别同dump,dumps）：

## 类型变化规则(左列向右列转换)
|Python|JSON|
|-|-|
|dict|object|
|list,tuple|array|
|str,unicode|string|
|int,long,float|number|
|True|true|
|False|false|
|None|null|

|JSON|Python|
|-|-|
|||
|||
|||
|||
|||
|||
|||
