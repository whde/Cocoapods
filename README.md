# Cocoapods
Cocoapods学习日志及文章
<p align="center">![Cocoapods](http://upload-images.jianshu.io/upload_images/1623336-1482dba0c4f71e4d.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<p>文章所有者:Whde<p>
<p>原文链接:http://www.jianshu.com/p/7b33bd1092d5<p>
<p>这里不啰嗦Cocoapods有什么用,直接上如何使用,关于有什么用,相信各大搜索引擎比我解释更全面;<p>
## Cocoapods安装
<p>1.Mac终端输入<p>
```objective-c
sudo gem install cocoapods
```
<p>2.输入电脑密码即可开始安装,等待...<p>
   <p align="center">-------界面出现-------<p>
<p>![](http://upload-images.jianshu.io/upload_images/1623336-a8fd4a8315bf431b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
<p>3.继续终端输入<p>
```objective-c
pod setup
```
<p>等待界面出现<p>
<p align="center">-------安装成功-------<p>
<p>![安装成功](http://upload-images.jianshu.io/upload_images/1623336-b2c343af14d1fa05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
<p>4.终端输入以下代码,查看版本号<p>
```objective-c
--version
```
<p>##写自己的库<p>
<p>写完代码, 将自己的库上传到github,要生成一个Release版本<p>
<p align="center">-------进入Release仓库-------<p>
<p align="center">![进入Release仓库](http://upload-images.jianshu.io/upload_images/1623336-ad494032b26c9b31.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
<p align="center">-------创建新Release版本-------<p>
<p align="center">![创建新Release版本](http://upload-images.jianshu.io/upload_images/1623336-6fd535b6a5b305a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
<p align="center">-------填写信息,发布Release版本-------<p>
<p align="center">![填写信息,发布Release版本](http://upload-images.jianshu.io/upload_images/1623336-65ef7cdc47d7a438.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
<p align="center">-------版本信息-------<p>
<p align="center">![版本信息](http://upload-images.jianshu.io/upload_images/1623336-29e6ad8bd5aa8aa3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
<p>接下来就看怎么将这个Release版本弄到Cocoapods上.<p>
##创建.podspec文件
<p>终端cd到项目文件夹下<p>
<p align="center">-------文件结构-------<p>
<p align="center">![文件结构](http://upload-images.jianshu.io/upload_images/1623336-a75c551ef8c2eef2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
<p align="center">-------我的项目就cd到WhdeLocalized文件夹下-------<p>
<p align="center">![我的项目就cd到WhdeLocalized文件夹下](http://upload-images.jianshu.io/upload_images/1623336-85c2774a37da9435.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
<p>终端输入代码创建.podspec文件,代码中Language对应项目名<p>
```objective-c
pod spec create Language
```
<p>用Xcode打开这个Language.podspec文件, 填写以下代码:<p>
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
<p>key对应的信息<p>
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
##检查.podspec文件是否有问题
<p>终端输入<p>
```objective-c
pod spec lint Language.podspec
```
<p>有什么问题, 会提示出来, 按照它的提示去修改, 不会改, 注意和给出的事例对比, 直到出现以下的结果<p>
<p align="center">![这个结果表示.podspec文件没有问题](http://upload-images.jianshu.io/upload_images/1623336-a7be54c5829f7fb3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
##上传.podspec文件
<p>终端输入<p>
```objective-c
pod trunk push Language.podspec
```
<p align="center">![出现这个结果表示已经上传上去了](http://upload-images.jianshu.io/upload_images/1623336-58d44db01f8795f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
##检查上传结果
<p>终端输入<p>
```objective-c
pod search Language
```
<p align="center">![上传结果及信息](http://upload-images.jianshu.io/upload_images/1623336-fdf90cf2d71b63d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)<p>
##使用
<p>在这里就不详细说Cocoapods使用了, 附上代码<p>
```objective-c
pod 'Language', '~> 1.0.4'
```
