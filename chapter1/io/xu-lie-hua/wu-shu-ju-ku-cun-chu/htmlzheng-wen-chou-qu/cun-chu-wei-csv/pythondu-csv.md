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



```
['ID', 'UserName', 'Password', 'age', 'country'] 1
['1001', 'zhiyu', 'zhiyu_pass', '23', 'China'] 2
['1002', 'Mary', 'Mary_pass', '20', 'USA'] 2
['1003', 'Mark', 'Mark_pass', '20', 'USA'] 2
```

