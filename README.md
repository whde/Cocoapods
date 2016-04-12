# Cocoapods
Cocoapods学习日志及文章
![Cocoapods](http://img.blog.csdn.net/20160321102112344)
**文章所有者:Whde**
这里不啰嗦Cocoapods有什么用,直接上如何使用,关于有什么用,相信各大搜索引擎比我解释更全面;
#Cocoapods安装
 **1.Mac终端输入** 
```objective-c
sudo gem install cocoapods
```
 **2.输入电脑密码即可开始安装,等待...** 
![界面出现](http://img.blog.csdn.net/20160321102212833)
 **3.继续终端输入** 
```objective-c
pod setup
```
 等待界面出现 
![安装成功](http://img.blog.csdn.net/20160321102350252)
 **4.终端输入以下代码,查看版本号** 
```objective-c
--version
```
#写自己的库 
 写完代码, 将自己的库上传到github,要生成一个Release版本 
![进入Release仓库](http://img.blog.csdn.net/20160321102431627)
![创建新Release版本(http://img.blog.csdn.net/20160321102506430)
![填写信息,发布Release版本](http://img.blog.csdn.net/20160321102633268)
![版本信息](http://img.blog.csdn.net/20160321102721659)
 接下来就看怎么将这个Release版本弄到Cocoapods上. 
#创建.podspec文件
 终端cd到项目文件夹下 
![文件结构](http://img.blog.csdn.net/20160321102747628)
![我的项目就cd到WhdeLocalized文件夹下](http://img.blog.csdn.net/20160321102819137)
 终端输入代码创建.podspec文件,代码中Language对应项目名 
```objective-c
pod spec create Language
```
 用Xcode打开这个Language.podspec文件, 填写以下代码: 
```objective-c
Pod::Spec.new do |s|
s.name          = "Language"
s.version       = "1.0.4"
s.summary       = "iOS Language."
s.homepage      = "https://github.com/whde/WhdeLocalized"
s.license       = 'MIT'
s.author        = { "Whde" => "460290973@qq.com" }
s.platform      = :ios, "7.0"
s.source        = { :git => "https://github.com/whde/WhdeLocalized.git", :tag => s.version.to_s }
s.source_files  = 'Language/Language/Language/*'
s.frameworks    = 'Foundation'
s.requires_arc  = true
s.description   = <<-DESC
It is a Language used on iOS, which implement by Objective-C.
DESC
end
```
 key对应的信息 
```objective-c
s.name(项目名称)
s.version(Release版本号,必须和Github上的Release版本号对于)
s.summary(对项目总结性的语言)
s.homepage(Github上项目的地址)
s.license(默认'MIT')
s.author(用户信息;自己的名字,自己的邮箱)
s.platform(支持的版本)
s.source(项目的git地址)
s.source_files(告诉别人,使用你的库,需要添加的文件在哪里)
s.frameworks(这项目需要添加的库)
s.requires_arc(是否支持ARC)
s.description   = <<-DESC
(更详细的描述)
DESC
end
```
#检查.podspec文件是否有问题
 终端输入 
```objective-c
pod spec lint Language.podspec
```
 有什么问题, 会提示出来, 按照它的提示去修改, 不会改, 注意和给出的事例对比, 直到出现以下的结果 
![](http://img.blog.csdn.net/20160321102858269)
#上传.podspec文件
 终端输入 
```objective-c
pod trunk push Language.podspec
```

![出现这个结果表示已经上传上去了](http://img.blog.csdn.net/20160321103804820)
#检查上传结果
 终端输入 
```objective-c
pod search Language
```
![](http://img.blog.csdn.net/20160321103001442)
#使用
 在这里就不详细说Cocoapods使用了, 附上代码 
```objective-c
pod 'Language', '~> 1.0.4'
```
