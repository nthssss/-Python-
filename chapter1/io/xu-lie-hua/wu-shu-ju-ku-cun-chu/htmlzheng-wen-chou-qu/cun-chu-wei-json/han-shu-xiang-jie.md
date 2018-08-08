# 函数详解
---
## dumps、dump


```python
# -*- coding: utf-8 -*-
import json
str = [{"username":"知鱼","age":24}, (2,3), 1]
json_str = json.dumps(str, ensure_ascii=False)
print json_str
with open('zhiyu.txt','w') as fp:
    json.dump(str,fp=fp,ensure_ascii=False)
```

