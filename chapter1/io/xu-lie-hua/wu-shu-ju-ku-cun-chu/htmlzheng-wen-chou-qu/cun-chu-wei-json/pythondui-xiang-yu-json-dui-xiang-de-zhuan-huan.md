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
> Python的一些基本类型:
    - 通过编码之后，tuple类型就转成了list类型了，
    - 再将其转回为python对象时：
        - list类型也并没有转回tuple类型，
        - 而且编码格式也发生了变化，变成了unicode编码。

### dump、dumps
|Python|JSON|
|-|-|
|dict|object|
|list,tuple|array|
|str,unicode|string|
|int,long,float|number|
|True|true|
|False|false|
|None|null|
### load、loads
|JSON|Python|
|-|-|
|object|dict|
|array|list|
|string|unicode|
|number(int)|int,long|
|number(real)|float|
|true|True|
|false|False|
|null|None|

