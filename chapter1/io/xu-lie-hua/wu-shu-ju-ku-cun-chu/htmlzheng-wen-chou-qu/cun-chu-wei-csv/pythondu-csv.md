#python读csv
---
创建reader对象


```python
import csv
with open('zhiyu01.csv') as f:
    f_csv = csv.reader(f)
    headers = next(f_csv)
    print(headers,1)
    for row in f_csv:
        print(row,2)
```
运行结果：

```
['ID', 'UserName', 'Password', 'age', 'country'] 1
['1001', 'zhiyu', 'zhiyu_pass', '23', 'China'] 2
['1002', 'Mary', 'Mary_pass', '20', 'USA'] 2
['1003', 'Mark', 'Mark_pass', '20', 'USA'] 2
```
上面代码中row是一个列表：
- 使用索引访问某个字段，这种索引访问会引起混淆；
- 因此可以考虑使用命名元组。
