---
title: Hexo及主题的相关配置
date: 2022-11-22 14:50:40
categories: Hexo主题
tags: [Hexo,yern,博客]
top: true
archives: Hexo及主题的相关配置
---
介绍如何安装Hexo及下载主题和配置主题，并且上传到Github成功访问
<!-- more -->
## 1. 下载Hexo
打开cmd窗口  

    npm intall -g hexo
<br/>

## 2. 文件初始化
进入你要创建博客的文件夹中

    hexo init #初始化项目
    hexo clean #清除缓存
    hexo g #生成静态文件
    hexo s #启动端口并预览 http://localhost:4000/


{% asset_img image.jpg [title] %}

![Hexo第一次初始化的博客](/images/source/hexoInit.png "Philadelphia's Magic Gardens")

## 3. 将Hexo部署到Github
### 1. Github创建个人仓库
>首先，需要有一个github账号。登上账号后建一个仓库：仓库名为你的用户名.github.io，  
举例如下：  
创建一个和你用户名相同的仓库，后面加.github.io，
只有这样，将来要部署到GitHub的时候，才会被识别，也就是xxxx.

![Github创建个人仓库](/images/source/resdory.png "Github创建个人仓库")

### 2. 生成ssh添加到Github
打开cmd窗口，执行如下命令

    git config --global user.name "yourname"
    git config --global user.email "youremail"

防止输错可以检查：

    git config user.name
    git config user.email

接着就会发现C:\Users\libinbin下多了一个.ssh目录，打开后有一个公钥，一个私钥。id_rsa.pub是公钥，我们需要打开它，复制里面的内容。

然后进入github：
点击setings

进行以下操作

![设置SSH](/images/source/ssh1.png "设置SSH")

发现我们需要一个密钥，把我们刚刚复制的密钥粘进去，title随便起

![设置SSH](/images/source/ssh2.png "设置SSH")

### 3. 进行部署

修改根目录的配置文件_config.yml

    deploy:
        type: git
        repo: git@github.com:goubin18/goubin18.github.io.git
        branch: main

### 4. 安装deploy-git,也就是部署命令，这样你才能用命令部署到GitHub

    npm install hexo-deployer-git --save

### 5. 然后依次执行以下命令：

    hexo c   #清除缓存文件 db.json 和已生成的静态文件 public
    hexo g       #生成网站静态文件到默认设置的 public 文件夹(hexo generate 的缩写)
    hexo d       #自动生成网站静态文件，并部署到设定的仓库(hexo deploy 的缩写)

>例如：我的用户名是lixiaolong521，那么我的博客地址就是lixiaolong521.github.io

## 常见问题
### 1. fatal: unable to access

![fatal: unable to access](/images/source/gitError1.png "fatal: unable to access")
解决方案：把_config.yml中的git仓库链接改成了ssh链接
### 2. 安装插件
##### 添加Live2d小人（在根目录而不是主题根目录）

    npm install --save hexo-helper-live2d

##### 添加配置文件（根目录_config.yml）

    live2d:
    enable: true  # 是否启动
    scriptFrom: local # 默认
    pluginRootPath: live2dw/  # 插件在站点上的根目录(相对路径)
    pluginJsPath: lib/  # 脚本文件相对与插件根目录路径
    pluginModelPath: assets/  # 模型文件相对与插件根目录路径
    tagMode: false  # 标签模式, 是否仅替换 live2d tag标签而非插入到所有页面中
    debug: false  # 调试, 是否在控制台输出日志
    model:
        use: live2d-widget  ## 模型文件
    display:
        position: right # 定位方向 left right top bottom
        width: 150  # 小人宽度
        height: 300 #  小人高度
        hOffset: -15  # 向 偏移
        vOffset: -15  # 像 偏移
    mobile:
        show: true  # 手机端是否显示
    react:
        opacity: 0.7  # 模型透明度


##### 选择你喜欢的模型

    live2d-widget-model-chitose
    live2d-widget-model-epsilon2_1
    live2d-widget-model-gf
    live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
    live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
    live2d-widget-model-haruto
    live2d-widget-model-hibiki
    live2d-widget-model-hijiki
    live2d-widget-model-izumi
    live2d-widget-model-koharu
    live2d-widget-model-miku
    live2d-widget-model-ni-j
    live2d-widget-model-nico
    live2d-widget-model-nietzsche
    live2d-widget-model-nipsilon
    live2d-widget-model-nito
    live2d-widget-model-shizuku
    live2d-widget-model-tororo
    live2d-widget-model-tsumiki
    live2d-widget-model-unitychan
    live2d-widget-model-wanko
    live2d-widget-model-z16

然后通过npm install --save live2d-widget-model-xxx来安装你喜欢的模型 比方说作者喜欢的是koharu这个那就使用npm install --save live2d-widget-model-koharu进行安装

安装后把配置里的这条修改成安装的模型名字

    model:
    use: live2d-widget-model-koharu

然后使用
    
    hexo clean
    hexo g
    hexo s

就可以预览了