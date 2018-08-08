# Email提醒
---
## 作用
Email在爬虫开发中：报告爬虫在运行过程中遇到异常或者服务器遇到问题。
## 协议
SMTP协议发送邮件，Python内置对SMTP的支持，可以发送 

1. 纯文本邮件；
- HTML邮件；
- 带附件的邮件。

## 步骤

### 申请163邮箱，开启SMTP功能；
### 构造纯文本邮件；
1. 构造MIMEText对象需要三个参数
    1.  邮件正文；
    - MIME的subtype，传入“plain”表示纯文本，最终的MIME就是“text/plain”；
    - 设置编码格式，UTF-8编码保证多语言兼容性。


```python
from email.mime.text import MIMEText
msg = MIMEText('Python爬虫运行异常，异常信息为遇到HTTP 403', 'plain', 'utf-8')
```


    
2. 接着设置邮件的发件人、收件人和邮件主题等信息，并通过STMP发送出去：
# -*- coding: utf-8 -*-
from email.header import Header
from email.mime.text import MIMEText
from email.utils import parseaddr, formataddr

import smtplib

def _format_addr(s):
    name, addr = parseaddr(s)
    return formataddr((Header(name, 'utf-8').encode(), addr))

# 发件人地址
from_addr = 'jiesan123@163.com'
# SMTP授权码（书上写的是邮箱密码，错了）
password = 'zhiyu1234'
# 收件人地址
to_addr = '710873879@qq.com'
# 163网易邮箱服务器地址
smtp_server = 'smtp.163.com'
# 设置邮件信息
msg = MIMEText('Python爬虫运行异常，异常信息为遇到HTTP 403', 'plain', 'utf-8')
msg['Form'] = _format_addr('1#爬虫<%s>' % from_addr)
msg['To'] = _format_addr('管理员<%s>' % to_addr)
msg['Subject'] = Header('1#爬虫运行状态', 'utf-8').encode()
# 发送邮件
server = smtplib.SMTP(smtp_server, 25)
server.login(from_addr, password)
server.sendmail(from_addr, [to_addr], msg.as_string())
server.quit()
"""
发送HTML邮件，将异常网页信息发送回去：
构造MIMEText对象时
    把HTML字符串传进去
    再把第二个参数由'plain'变为'html'
"""

msg = MIMEText('<html><body><h1>Hello</h1>' +
               '<p>异常网页<a href="http://www.cnblogs.com">cnblogs</a>...</p>'+
               '','html','utf-8')