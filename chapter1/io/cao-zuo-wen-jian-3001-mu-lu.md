操作文件、目录
---
## os

|代码|功能|
|-|-|
|os.getcwd()|获得当前Python脚本工作的目录路径|
|os.listdir()|返回指定目录下所有文件＆目录名|
|os.remove(filepath)|删除一个文件|
|os.removedirs(r"d:\python")|删除多个空目录|
|os.path.isfile(filepath)|检验给出路径是否是一个文件|
|os.path.isdir(filepath)|检验给出路径是否是一个目录|
|os.path.isabs()|判断是否是绝对路径|
|os.path.exists(r"d:\python")|检验路径是否真的存在|
|os.path.split(r"/home/qiye/qiye.txt")|分离文件名<br>返回一个元组:("/home/qiye/","qiye.txt")|
|os.path.splitext(r"/home/qiye/qiye.txt")|分离`.扩展名`<br>返回一个元组("/home/qiye/qiye",".txt")|
|os.path.dirname(filepath)|获取路径名|
|os.path.basename(filepath)|获取文件名|
|os.path.getsize(filename)|获取文件大小|
|os.getenv()<br>os.setenv()|读取环境变量<br>获取环境变量|
|os.linesep|获取当前平台行终止符：<br>Windows：`\r\n`<br>Linux：`\n`<br>Mac：`\r`|
|os.name|获取当前平台：<br>Windows：`nt`<br>Linux/Unix：`posix`|
|os.rename(old,new)|重命名文件或目录|
|os.makedirs(r"c:\python\test")|创建多级目录|
|os.mkdir("test")|创建单个目录|
|os.stat(file)|获取文件属性|
|os.chmod(file)|修改文件权限与时间戳|
|os.rmdirs("dir")|删除目录<br>只能删除空目录<br>|
## shutil
|代码|功能|
|-|-|
|shutil.copytree("olddir", "newdir")|复制文件夹<br>oldder和newdir都只能是目录<br>newdir必须不存在|
|shutil.copyfile("oldfile", "newfile")|复制文件<br>oldfile和newfile都只能是文件|
|shutil.copy("oldfile", "newfile")|复制文件<br>oldfile只能是文件<br>newfile可以是文件，也可以是目标目录|
|shutil.move("oldpos","newpos")|移动文件|
|shutil.rmtree("dir")|空目录、有内容的目录都可以删|
