# [IPAPatch](https://github.com/Naituw/IPAPatch)

>  IPAPatch是一个比较神奇的东西，他可以把ipa文件当做一个动态库来执行，所以在ios的Objective-C运行时里面你就可以为所欲为

## 配置使用

### 第一步，下载工程

使用git克隆工程`git clone https://github.com/Naituw/IPAPatch.git`

### 第二步，准备一个砸了壳的ipa文件

载pp助手里面去下载没有课的ipa或者手动去吧ios应用商店下载的ipa的壳给砸开

### 第三步，替换掉工程里面的app.ipa文件

将上一步砸开壳之后的ipa文件重名名为app.ipa，然后放到I`PAPatch/Assets/app.ipa`

### 第四步，放置三方framework（可选）

放置三方framework到`IPAPatch/Assets/Frameworks`这里面，放在这里面会被自动链接

### 第五步，配置

打开 IPAPatch，在 IPAPatch-DummyApp 这个 Target 里，配置好 BundleID 和代码签名。Display Name 会作为前缀添加到原来的 App 上

### 第六步，编写你的patch

编写的入口在`IPAPatchEntry.m`文件的load方法，你可以在这里改变应用的行为，比如去掉https证书校验什么的，总之可以做你任何想做的时

### 第七步，编译运行

点击run按钮就可以了