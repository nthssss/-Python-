# 多媒体文件抽取
---
## 存储多媒体文件（两种方式）
1. 只获取文件的URL链接；
- 直接将媒体文件下载到本地。

## urlretrieve()函数（urllib模块）
urlretrieve()将远程数据直接下载到本地：


```
urlretrieve(url, filename=None, reporthook=None, data=None)
```


|参数|参数说明|
|-|-|
|filename|指定存储本地路径:<br>如果参数未指定，urllib会生成一个临时文件保存数据。|
|reporthook|回调函数：<br>当连接上服务器以及相应的数据块传输完毕时触发该回调函数；<br>可以利用该回调函数显示当前下载进度。|
|data|post到服务器的数据，该方法返回一个包含两个元素的元组`(filename,header)`：<br>filename表示保存到本地的路径；<br>header表示服务器响应头。|


以天堂图片网`http://www.ivsky.com/tupian/ziranfengguang/`为例，提取当前网址中的图片链接，并将图片下载到当前目录下：

1. 提取当前网址将img标记中的src属性；
- urllib.urlretrieve函数下载，自动回调schedule函数，显示当前下载的进度。



```python
# -*- coding: utf-8 -*-
import urllib
import requests
from lxml import etree
def schedule(blocknum,blocksize,totalsize):
    '''
    :param blocknum:已经下载的数据块
    :param blocksize: 数据块的大小
    :param totalsize: 远程文件的大小
    :return:
    '''
    per = 100.0 * blocknum * blocksize / totalsize
    if per > 100:
        per = 100
    print '当前下载进度：%d' % per
user_agent = 'ozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/68.0.3440.84 Safari/537.36'
headers = {'User-Agent':user_agent}
r = requests.get('http://www.ivsky.com/tupian/ziranfengguang/', headers=headers)
# 使用lxml解析网页
html = etree.HTML(r.text)
img_urls = html.xpath('.//img/@src')  # 先找到所有的img
i = 0
for img_url in img_urls:
   urllib.urlretrieve(img_url, 'img'+str(i)+'.jpg',schedule)
   i+=1

```

