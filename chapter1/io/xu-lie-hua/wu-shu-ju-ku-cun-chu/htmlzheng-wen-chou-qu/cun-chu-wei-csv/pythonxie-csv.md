# python写CSV
---
```python
import csv
headers = ["ID","UserName","Password","age","country"]
rows = [(1001,"zhiyu","zhiyu_pass",23,"China"),
        (1002,"Mary","Mary_pass",20,"USA"),
        (1003,"Mark","Mark_pass",20,"USA")
]
with open('zhiyu02.csv','w') as f:
    f_csv = csv.writer(f)
    f_csv.writerow(headers)
    f_csv.writerows(rows)
```
rows列表中的数据元组，也可以是字典数据。


```python
import csv
headers = ["ID","UserName","Password","age","country"]
rows = [{"ID":1001,"UserName":"zhiyu","Password":"zhiyu_pass","age":23,"country":"China"},
        {"ID":1002,"UserName":"Mary","Password":"Mary_pass","age":20,"country":"USA"},
        {"ID":1003,"UserName":"Mark","Password":"Mark_pass","age":20,"country":"USA"}
]
with open('zhiyu02.csv','w') as f:
    f_csv = csv.DictWriter(f,headers)
    f_csv.writeheader()
    f_csv.writerows(rows)
```



