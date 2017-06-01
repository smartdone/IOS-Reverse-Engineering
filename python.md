# 安装python

1. 在cydia中搜索libffi安装
2. 下载[http://python.mila432.com/python_2.7.13-1_iphoneos-arm.deb](http://python.mila432.com/python_2.7.13-1_iphoneos-arm.deb)到设备上并且安装
3. 执行下列命令

```shell
dpkg -i python_2.7.13-1_iphoneos-arm.deb
ldid -S /usr/bin/python
ldid -S /usr/lib/libpython2.7.dylib
ldid -S /usr/lib/libssl.1.0.0.dylib
ldid -S /usr/lib/libcrypto.1.0.0.dylib
```

