# 存储为JSON
---
1. requests访问`http://seputu.com/`，获取HTML文档内容。
```python
# -*- coding: utf-8 -*-
import requests
user_agent = 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/68.0.3440.84 Safari/537.36'
headers = {'User-Agent':user_agent}
r = requests.get('http://seputu.com/', headers=headers)
# print r.text  # 可以打印查看文档内容，可以直接`ctrl+u`查看网页源码。
```
- 分析首页HTML结构，确定要抽取标记的位置：
    1. 标题和章节都被包含在```<div class="mulu">```;
    - 标题位于其中的```<div class="mulu-title">```下的```<h2>```中；
    - 章节位于其中的```<div class="box">`下的```<a>```中