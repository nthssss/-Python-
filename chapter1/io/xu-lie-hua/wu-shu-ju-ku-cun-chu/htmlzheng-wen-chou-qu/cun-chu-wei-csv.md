# 存储为CSV
---
- Comma-Separated Values；
- 逗号分隔值、字符分隔值（字符可以不是逗号）。
- 纯文本形式存储表格数据：
    - 数字和文本；
    - 该文件是一个字符序列，不含必须像二进制那样被解读的数据。
- CSV文件由任意数目的记录组成，记录间以某种换行符分隔；
- 每条记录由字段组成，字段间的分隔符是其他字符或字符串，最常见的是逗号或制表符。
- 通常，所有记录都有完全相同的字段序列。

```csv
ID,UserName,Password,age,country
1001,"zhiyu","zhiyu_pass",23,"China"
1002,"Mary","Mary_pass",20,"USA"
1003,"Mark","Mark_pass",20,"USA"
```
Python：csv库，writer对象。
