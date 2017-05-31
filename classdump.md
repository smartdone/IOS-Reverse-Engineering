# class-dump

下载地址 [http://stevenygard.com/projects/class-dump/](http://stevenygard.com/projects/class-dump/)

class-dump是用来dump目标对象的class信息的工具，他利用objective-c语言的runtime特性，将存储在Mach-O文件中的头文件信息提取出来，并生成对应的.h文件。

下载dmg，然后将里面的class-dump复制出来，更改权限为可执行，并且加到环境变量。

导出头文件命令

```
class-dump -S -s -H 可执行文件 -o 输出目录 
```

## Usage

```
class-dump 3.5 (64 bit)
Usage: class-dump [options] <mach-o-file>

  where options are:
        -a             show instance variable offsets
        -A             show implementation addresses
        --arch <arch>  choose a specific architecture from a universal binary (ppc, ppc64, i386, x86_64, armv6, armv7, armv7s, arm64)
        -C <regex>     only display classes matching regular expression
        -f <str>       find string in method name
        -H             generate header files in current directory, or directory specified with -o
        -I             sort classes, categories, and protocols by inheritance (overrides -s)
        -o <dir>       output directory used for -H
        -r             recursively expand frameworks and fixed VM shared libraries
        -s             sort classes and categories by name
        -S             sort methods by name
        -t             suppress header in output, for testing
        --list-arches  list the arches in the file, then exit
        --sdk-ios      specify iOS SDK version (will look in /Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS<version>.sdk
        --sdk-mac      specify Mac OS X version (will look in /Developer/SDKs/MacOSX<version>.sdk
        --sdk-root     specify the full SDK root path (or use --sdk-ios/--sdk-mac for a shortcut)
```

