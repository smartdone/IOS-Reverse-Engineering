# class-dump

下载地址 [http://stevenygard.com/projects/class-dump/](http://stevenygard.com/projects/class-dump/)

class-dump是用来dump目标对象的class信息的工具，他利用objective-c语言的runtime特性，将存储在Mach-O文件中的头文件信息提取出来，并生成对应的.h文件。

导出头文件命令

```
class-dump -S -s -H 可执行文件 -o 输出目录 
```

