# sin-coder.github.io
Personal Blog Website（Hugo）  
基于Hugo框架搭建的个人博客系统  
该网站部署在Github上，在公网上可通过csuyzz.com访问  

### 关键词：Hugo 、Git、Github、域名解析

[TOC]

## 概述

#### 1.Hugo简介

> Hugo是基于Go语言开发的静态网站生成器，简单、易用、快速部署，主要用于构建个人博客

#### 2.Git简介

> Git是目前主流的分布式版本控制工具，有关Git的使用请查看Git的来龙去脉这篇文章

#### 3.Github简介

> Github是在外网环境下的一个代码托管库，有关Github的介绍请查看开始玩起Github这篇文章

## 具体过程

#### 1.准备工作

- 下载Git并安装、配置环境变量

  > 完成后在终端执行"git"命令来测试是否安装成功，有关git的安装请看Git的来龙去脉

- 下载Hugo并安装、配置环境变量

  > 完成后在终端执行"hugo version"命令来测试是否安装成功，终端提示如下信息表示安装成功

  ```bash
  C:\Users\Administrator>hugo version
  Hugo Static Site Generator v0.59.1-D5DAB232 windows/amd64 BuildDate: 2019-10-31T15:22:43Z
  ```

  > Hugo最好安装在英文目录下

  > 下载时可能由于网络问题失败，附上Hugo、Git、主题m10c的下载包链接: [下载链接](https://www.lanzous.com/i8iy3xg)

- 注册Github官网（已有账号请忽略）

#### 2.生成个人站点

#### （1）在终端执行命令

```bash
C:\Users\Administrator>hugo new site E:\hugo\Sites\myblog
```

> 出现以下提示信息表示创建成功：

```bash
C:\Users\Administrator>hugo new site E:\hugo\Sites\myblog
Congratulations! Your new Hugo site is created in E:\hugo\Sites\myblog.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

> 命令执行完毕后即可在myblog目录下生成以下文件s

```bash
E:\hugo\Sites\myblog>tree /f
卷 CSUYZZ 的文件夹 PATH 列表
卷序列号为 2C3A-5572
E:.
│  config.toml
│
├─archetypes
│      default.md
│
├─content
├─data
├─layouts
├─static
└─themes
```

> 注意："E:\hugo\Sites\myblog"为该博客的根目录，这个概念接下来将会多次用到

####      （2）文件简介

> 了解根目录下的文件将有助于个性化地定制博客

+ config.toml:全局配置文件，结合所用的主题进行配置(后面会讲解)
+ themes:主题存放的位置，主题中的文件也可进行个性化定制
+ static:存储图片、js、css等静态资源文件
+ layouts:存放用来渲染博客内容的模板文件
+ data:存放相关数据文件
+ contents:所有博客内容(md文件)默认的存放目录

####      （3）设置主题

> Hugo框架有许多酷炫的主题，可以在[主题官网](themes.gohugo.io)上进行挑选

> 每个主题的详情页均会列出使用该主题的方法，这里m10c主题为例

> 在根目录下执行如下命令:

```bash
 git clone https://github.com/vaga/hugo-theme-m10c.git  themes/m10c
```

> 终端出现如下结果表示下载成功，同时在themes文件夹会出现m10c文件夹

```bash
E:\hugo\Sites\myblog>git clone https://github.com/vaga/hugo-theme-m10c.git themes/m10c
Cloning into 'themes/m10c'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 276 (delta 0), reused 2 (delta 0), pack-reused 270Receiving objects:  52% (144/276), 308.01 KiB | 165.00 KReceiving objects:
Receiving objects: 100% (276/276), 447.95 KiB | 231.00 KiB/s, done.
Resolving deltas: 100% (88/88), done.
```

> 在进行测试前需要在config.toml文件中添加 theme = "m10c",文件内容如下所示

```txt
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"

theme = "m10c"
```

####      （4）本地启动测试

> 在在根目录下执行命令

> hugo server -t m10c --buildDrafts 

> 会出现以下信息

```bash
E:\hugo\Sites\myblog>hugo server -t m10c --buildDrafts
Building sites …
                   | EN
+------------------+----+
  Pages            |  7
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  1
  Processed images |  0
  Aliases          |  3
  Sitemaps         |  1
  Cleaned          |  0

Total in 13 ms
Watching for changes in E:\hugo\Sites\myblog\{archetypes,content,data,layouts,static,themes}
Watching for config changes in E:\hugo\Sites\myblog\config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

> 复制http://localhost:1313/ 在浏览器中打开即可看到如下界面 

![本地测试预览](https://s2.ax1x.com/2020/01/27/1u3sSI.png)

####     （5）个性化定制

> 以上生成的界面即为模板，需要我们个性化定制一波，相关参数在config.toml中配置

> 在[m10c主题界面](https://themes.gohugo.io/hugo-theme-m10c)有介绍相关参数的配置介绍，config.toml文件如下

```base
baseURL ="http://example.org/
languageCode="en-us"
title="sin-coder"  //昵称

theme="m10c"       //主题

paginate=10        //分页，每页最大博客数目
[params]
	author="csuyzz"
	description="I always remember that Talk is cheap，show me the code'"#个人描述
	avatar="cat.jpg"  //头像文件，将置换的头像文件置于themes\m1ec\static\目录下，捋文件名作为avatar的参数

[[params.social]]
name="github"        //github的社交链接，还可配置twitter
ur1="https://github.comsin-coder"  //Github主页地址

[params.style]                     //配置界面颜色
	darkestColor="#d35050"
	darkColor="#212121"
	lightColor="#f5e3e0"
	lightestColor="#f5f5f5"
	primaryColor="fff"
```

> **注意：** “//”后的内容只是解释该参数的作用，在实际配置文件中不应该存在

> 参数配置完成后进行测试的效果

![本地测试配置](https://s2.ax1x.com/2020/01/27/1u3ylt.png)

> 当然，可配置的参数还有许多，比如文章分类、评论系统等功能，这个希望大家继续研究

#### （6）创建博客文章

> 在根目录下执行命令

```
 E:\hugo\Sites\myblog>hugo new post/firstblog.md
```

> 出现以下提示信息表示创建成功

```bash
E:\hugo\Sites\myblog>hugo new post/firstblog.md
E:\hugo\Sites\myblog\content\post\firstblog.md created
```

> 系统默认是在content目录下创建文件的,为了方便管理，将所有的文章至于post目录下

> 创建成功后，在content/post即可看到firstblog.md了

> 接下来就是使用markdown进行编写博客了，编写完之后在根目录下重新执行命令

> hugo server -t m10c --buildDrafts即可预览到以下界面

<img src="https://s2.ax1x.com/2020/01/27/1u366P.md.png" alt="1u366P.png" style="zoom: 102%;" />

![1u3cOf.png](https://s2.ax1x.com/2020/01/27/1u3cOf.png)

#### （7）本地部署测试命令总结

> 注意所有的命令均应该在根目录下执行

```
hugo new site myblog
git clone https://github.com/vaga/hugo-theme-m10c.git themes/m10c
hugo server -t m10c --buildDrafts
hugo new post/firstblog.md
hugo server -t m10c --buildDrafts
```

#### 3.部署到Github上

####      （1）创建仓库

> 在Github上创建仓库 ,命名必须为 用户名.github.io，如sin-coder.github.io

####      （2）生成最终html界面 

> 在根目录下执行命令

```
 E:\hugo\Sites\myblog> hugo --theme=m10c --baseUrl="https://sin-coder.github.io" --buildDrafts
```

> 会在blog目录下生成一个public文件夹，文件夹中即是firstblog转换成的html文件

> public文件夹即是公开出来让别人能看到的文件，也是需要上传到仓库中的文件夹

####      （3）将文件推送到Github仓库

```bash
cd public  #先进入到public文件夹
git init     #初始化
git remote add origin https://github.com/sin-coder/sin-coder.github.io.git  #本地仓库链接到远程仓库
git config --global user.email  邮箱地址   #这里设置的签名和远程登陆库与Github 的账号和密码无关
git config --global user.name 名字      #作用仅仅是区分不同的开发人员
git add -A
git commit -m "描述" 
git push -u origin master
```

> 这里操作中可能出现的错误就是与git有关了 建议先去学下git的基本命令

####      （4）查看界面

> 在浏览器中输入  “用户名.github.io" 即可查看界面

####      （5）新建/修改 博客

> **新建博客执行命令**

​        （根目录）  

```bash
hugo new post/filename.md
hugo --theme=m10c --baseUrl="https://sin-coder.github.io" --buildDrafts 
```

​           (public 目录) 

```bash
cd public
git add -A 
git commit -m 
git push -u origin master
```

> **修改博客执行命令**

> **与新建博客基本相同，只是不执行第一条命令**

>  **删除博客命令**

> 在本地将**content/post/filename.md**文件删除

​            **（根目录）** 

```
hugo --theme=m10c --baseUrl="https://sin-coder.github.io" --buildDrafts 
```

​           **（public目录）**

```ba'sh
git add -A
git commit -m "描述"
git push -u origin master
```

#### 4.域名解析

####       （1）申请域名、域名认证

> 在域名网站注册并购买自己的域名，同时进行域名认证

####       （2）配置域名

> 在github仓库中添加CNAME文件，并在文件中填写绑定的域名

> 注意填写的内容不能包括https://www,  只能写上csuyzz.com

<img src="https://s2.ax1x.com/2020/01/27/1u3DfA.png" alt="1u3DfA.png" style="zoom:80%;" />

> 进入设置Settings 找到Custom domain添加域名后进行保存，默认自动保存

<img src="https://s2.ax1x.com/2020/01/27/1u30FH.png" alt="1u30FH.png"  />

####       （3）域名解析

> 在命令行下执行命令：ping 用户名.github.io  获取对应的IP地址

> 然后修改域名解析记录，添加两个A记录，绑定域名和IP地址 

> 主机记录www 和@各一个，www表示解析域名为www.csuyzz.com ,@则表示解析域名为csuyzz.com

<img src="https://s2.ax1x.com/2020/01/27/1u3BYd.png" alt="1u3BYd.png" style="zoom:80%;" />

<img src="https://s2.ax1x.com/2020/01/27/1u3dTe.png" alt="1u3dTe.png" style="zoom:80%;" />



