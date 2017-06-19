# OC基础语法

---

```objective-c
#import <Foundation/Foundation.h>

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        // insert code here...
        NSLog(@"Hello, World!");
    }
    return 0;
}
```

- OC程序和入口
> C程序的源文件后缀名为.c，OC程序源文件后缀名为.m，m就是message的意识。因为OC是完全兼容C的，所以在OC中入口仍然是mian函数
- `#import`指令
> 这是一个增强的`#include`指令，用户和`#include`指令相同，并且`#import`在包含文件的时候会先判断这个文件是否被包含，如果没有被包含，就包含进来，如果被包含就不会重复包含。
- Foundation框架

>提供了一些OC最基础的功能，`Foundation.h`这个文件中包含了所有的`Foundation`框架中的头文件，`#import`相当于包含了所有的Foundation框架的头文件

- `@autoreleasepool`
>他是一个自动释放池，管理内存的
- NSLog函数

> 是printf函数的增强版，作用也是向控制台输出信息。
>
> 1. NSLog输出完毕信息之后会默认加一个\n，如果我们手动加了一个\n，NSLog的自动换行就会失效。
> 2. 在输出信息的同时还会输出一些与程序有关的其他信息(系统时间、程序名、进程ID、线程ID)。
> 3. NSLog函数支持printf函数的全部格式控制符，其用法也相同。
> 4. NSLog函数的字符串参数前面必须要加一个@符号，这是OC里的字符串格式。
> 5. NSLog可以使用%@格式控制符输出对象，而printf不能输出对象。
> 6. NSLog函数的第一个参数是NSString类型的指针，所以必须给一个OC字符串。

## OC中的字符串

C语言使用字符数组和字符指针的方式来存储字符串，oc中专门设计了一个新的数据类型`NSString`来保存字符串。

1. OC字符串签名必须加一个前缀`@`。
2. OC的字符串常量使用NSString类型的指针变量来保存地址。
3. NSString类型的变量的指针变量只能保存OC字符串的地址。
4. 使用`%@`格式控制符输出NSSTring类型的字符串


