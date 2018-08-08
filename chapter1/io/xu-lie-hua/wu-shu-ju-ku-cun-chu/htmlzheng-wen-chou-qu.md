# HTML正文抽取
---
1. 存储为JSON
- 存储为CSV


- `http://seputu.com/`
- 静态网站
    - 即标题、章节、章节名称都不是由JS动态加载的，下面本例工作的前提 。
- 本例使用BeautifulSoup和lxml两种方式进行解析抽取。

---
> 1. 存储CSV文件时需要统一存储数据类型。
    - 代码中使用encode('utf-8')将title、real_title、href、date变量统一为str。
- BeautifulSoup为不同的解析器提供了相同接口，但解析器本身有区别，同一篇文档被不同的解析器解析后可能会生成不同结构的树型文档。
    1. BeautifulSoup如果使用lxml作为解析库，会发现解析出来的HTML内容缺失；
    - 如果遇到缺失的情况：
        - BeautifulSoup可以使用html.parser作为解析器；
        - 或者单独使用lxml进行解析即可。
