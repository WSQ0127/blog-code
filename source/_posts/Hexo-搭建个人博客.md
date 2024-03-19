---
title: Hexo 搭建个人博客
date: 2023-12-01 20:23:36
categories: 前端
tags:
  - 前端
  - Hexo
  - github
  - blog
  - 个人博客
abbrlink: 553355a7
cover: https://cdn.jsdelivr.net/gh/xiaoliblog/image@88d6104165d7beac0f2c2844a539c0feffa4f33d/2021/01/24/993832d0c82e0ea4f5f7d61fb74320a6.png
---
## 写在最前

### 什么是 blog？

博客，仅音译，英文名为 Blogger，为 Web Log 的混成词，又名 blog。其正式名称为网络日记；又音译为部落格或部落阁等，是社会媒体网络的一部分。通常由个人管理、不定期张贴新的文章的网站。

### 为什么要写 blog？

**个人：** 博客的作用很就是记录生活，记录自己都日常。随手记录下每个不同人生阶段的感悟或莫名其妙的灵感。用语文老师的话：
> 提高写作能力

**他人：** 博客的目的是在互联网上提供内容，回答潜在客户的问题并帮助他们了解您的产品或服务，从而达到引流的效果。

## 准备工作

> 工欲善其事，必先利其器

Hexo 是基于 node.js 的静态博客框架
github 不用我多说了吧，基于 git,是全球最大的开源社区

既然要搭建 github pages+Hexo 的博客，那么——

[下载 node.js](https://nodejs.org)

[下载 git](https://git-scm.com/downloads)

下载好后，打开终端，依次输入

```powershell
node -v
npm -v
git --version
```

如果输出了版本号，说明下载完成，进入下一步吧


## 链接 github

### 注册 github

不多说了，三号网址上连接~~
{% link 注册 github, https://github.com/ %}

### 添加 SSH 秘钥
桌面任意处右键，打开 `Open Git Bush here`

依次执行（不加引号）
```powershell
git config --global user.name "你的 Github 用户名"
git config --global user.email "你的 Github 邮箱"
```

执行 `ssh-keygen -t rsa -C "你的 Github 邮箱"` 

然后一路回车，遇到 `(y,n)?` 时输入 `y`

打开资源管理器，点击 `查看` 勾选 `显示“隐藏的项目”`
![](https://cdn.luogu.com.cn/upload/image_hosting/1z1p92u3.png)

进入 `[C:\Users\用户名\.ssh]` 目录，用任意方法打开，复制所有内容

登陆 Github ，点击头像，进入 Settings，选择左边的 `SSH and GPG keys`，点击 `New SSH key`，随便起一个名字，粘贴进你刚才复制的内容，点击 `Add SSH key`

回到本地输入 `ssh -T git@github.com` ，回答 `yes`

输出 `Hi xxx! You've successfully authenticated. ……` 即连接成功。


## 创建仓库
进入主页，点击右上角加号，选择 `New repository`

之后在根据图中提示填写：
![](https://cdn.luogu.com.cn/upload/image_hosting/ll3v4cce.png)


## 链接 Hexo
### 下载 Hexo
在任意位置新建一个文件夹用来存放博客，例如 `Hexo-blog` ，打开文件夹，右键打开 `Open Git Bush here`（**之后所有指令都在这里执行**） ，输入 `npm install -g hexo-cli` 安装 Hexo

### 初始化 Hexo

```powershell
hexo init      # 初始化
npm install    # 安装组件
```
接下来输入
```powershell
hexo g   # 生成页面
hexo s   # 启动预览
```

访问 `http://localhost:4000`，如果访问成功并出现初始化面，恭喜你，安装成功！
![](https://hexo.io/themes/screenshots/landscape@2x.jpg)

## 部署
首先输入 `npm install hexo-deployer-git --save` 安装 hexo-deployer-git
然后将 `_config.yml` 文件末尾的 Deployment 部分修改成
```yaml
deploy:
  type: git
  repository: git@github.com:用户名/用户名.github.io.git
  branch: main
```
接下来记住这三句话，以后每次更改都需要输入一遍（有的人可能需要三遍 ~~别猜了，就是我，破防了~~）

```powershell
hexo clean     # 清空配置
hexo g         # 更新配置
hexo d         # 上传配置
```
这时访问你的地址就可以看到网站了
## 使用
进入博客所在目录，右键打开 `Git Bash Here` 输入 `hexo new "My New Post"` 创建一篇名为 `My New Post.md` 的博文。

创建的博客开头有以下几个属性组成
```markdown
title: Hello World # 标题
date: yyyy/mm/dd hh:mm:ss # 时间
categories: # 分类
- …… # 只能有一个
tags: # 标签
- ……
- ……
- …… # 可以有多个
---
随着配置插件等，属性也可能增加，例如 `password` 等