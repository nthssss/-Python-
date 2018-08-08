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
    1. 标题和章节都被包含在```&lt;div class="mulu"&gt; ```;
    - 标题位于其中的```&lt;div class="mulu-title"&gt; ```下的```&lt;h2&gt;```中；
    - 章节位于其中的```&lt;div class="box"&gt; ```下的```&lt;a&gt;```中。
```python
soup = BeautifulSoup(r.text, 'html.parser',
                     # from_encoding='utf-8'
                     )  # html.parser
for mulu in soup.find_all(class_="mulu"):
    h2 = mulu.find('h2')
    if h2 != None:
        h2_title = h2.string  # 获取标题
        for a in mulu.find(class_='box').find_all('a'):  # 获取所有a标记中url和章节内容
            href = a.get('href')
            box_title = a.get('title')
            # print href,box_title
```
- 将提取到的标题、章节和链接进行JSON存储：
完整代码：


```python
# -*- coding: utf-8 -*-
import json
from bs4 import BeautifulSoup
import requests
user_agent = 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/68.0.3440.84 Safari/537.36'
headers = {'User-Agent':user_agent}
r = requests.get('http://seputu.com/', headers=headers)
# print r.text  # 可以打印查看文档内容
soup = BeautifulSoup(r.text, 'html.parser',
                     # from_encoding='utf-8'
                     )  # html.parser
content = []
for mulu in soup.find_all(class_="mulu"):
    h2 = mulu.find('h2')
    if h2 != None:
        h2_title = h2.string  # 获取标题
        list = []
        for a in mulu.find(class_='box').find_all('a'):  # 获取所有a标记中url和章节内容
            href = a.get('href')
            box_title = a.get('title')
            # print href,box_title
            list.append({'href':href, 'box_title':box_title})
        content.append({'title':h2_title,'content':list})
with open('zhiyu.json','wb') as fp:
    json.dump(content,fp=fp,indent=4)
```



    


