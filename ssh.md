# ios10经过yalu越狱之后无法连接ssh

1. ios设备上安装mterminal，运行su，输入密码进入root查看进程dropbear是否存在
   ```shell
   ps aux | grep dropbear
   ```
   如果进程不存在，执行`/usr/local/bin/dropbear -F -R -p 22`

2. 如果进程存在，并且进程是这样的`/usr/local/bin/dropbear -F -R -p 127.0.0.1:22`
   这种就说明只能通过数据线重定向连接ssh，如果想通过wifi可以访问，就通过文件管理修改`/private/var/containers/Bundle/Application/{UUID}/yalu102.app/dropbear.plist`这个文件，把里面的一个参数`127.0.0.1:22`改成`22`即可

3. 修复scp
   yalu102自带的ssh可能无法使用，原因缺少了scp，首先在cydia里面安装wget，然后执行下面的命令来获取scp
   ```shell
   wget mila432.com/scp
   ldid -S scp
   chmod 777 scp
   mv scp /usr/bin/scp
   killall SpringBoard
   ```

