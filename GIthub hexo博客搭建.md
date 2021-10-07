# Github hexo 博客搭建

[toc]

### 1. github 个人域名等

还没兴趣做，等以后想做的时候可以做

### 2. 安装Node.js

```
# 下载Node js 
https://nodejs.org/en/download/
# 检查Node.js 是否安装成功
> node -v
# 检查npm 是否安装成功 
> npm -v
```

![image-20210316153922992](GIthub%20hexo%E5%8D%9A%E5%AE%A2%E6%90%AD%E5%BB%BA/image-20210316153922992.png)

###  3. 安装hexo及其使用

hexo 简介： 



```
# 安装hexo
> npm install -g hexo-cli 
# 在电脑中创建一个文件夹 Blog
在这个文件中，打开cmd, 运行以下命令
# 初始化我们的博客
> hexo init blog 

# 新建一个博客的步骤
hexo n "我的博客" == hexo new "我的博客" #新建文章
hexo g == hexo generate #生成
hexo s == hexo server #启动服务预览
hexo d == hexo deploy #部署

hexo s 之后可以在 localhost:4000  预览自己的博客
# 其他命令
hexo server #Hexo会监视文件变动并自动更新，无须重启服务器
hexo server -s #静态模式
hexo server -p 5000 #更改端口
hexo server -i 192.168.1.1 #自定义 IP
hexo clean #清除缓存，若是网页正常情况下可以忽略这条命令
```

### 4. 将hexo 与github 关联起来

```
# 配置
blog/_config.yml 是站点配置文件
blog/themes/_config.yml  是主题配置文件

将我们的Hexo与GitHub关联起来，打开站点的配置文件_config.yml，翻到最后修改为：
deploy:
type: git
repo: 这里填入你之前在GitHub上创建仓库的完整路径，记得加上 .git
branch: master 
```

![preview](GIthub%20hexo%E5%8D%9A%E5%AE%A2%E6%90%AD%E5%BB%BA/v2-279ac5149b577f04dc099defbb12eaa8_r.jpg)

```
# 保存站点配置文件
其实就是给hexo d 这个命令做相应的配置，让hexo知道你要把blog部署在哪个位置，很显然，我们部署在我们GitHub的仓库里。最后安装Git部署插件，输入命令：
> npm install hexo-deployer-git --save
# 部署
hexo clean 
hexo g 
hexo d
# 检验
打开存放个人网站的仓库缩写， 如 m-m-dot.github.io
如有结果则是成功的
```

### 5. 主题配置

如果你不喜欢Hexo默认的主题，可以更换不同的主题，主题传送门：[Themes](https://link.zhihu.com/?target=https%3A//hexo.io/themes/) 我自己使用的是Next主题，可以在blog目录中的themes文件夹中查看你自己主题是什么。现在把默认主题更改成Next主题，在blog目录中（就是命令行的位置处于blog目录）打开命令行输入：

```bash
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

这是将Next主题下载到blog目录的themes主题下的next文件夹中。打开**站点**的_config.yml配置文件，修改主题为next

参考： 

https://zhuanlan.zhihu.com/p/26625249  



### 6. 问题板块

参考 https://segmentfault.com/a/1190000015962368

**nvm 是用于WIndows 管理 NodeJs 版本的工具**

*  The "mode" argument must be integer.

  ![image-20210316163658311](GIthub%20hexo%E5%8D%9A%E5%AE%A2%E6%90%AD%E5%BB%BA/image-20210316163658311.png)**解决方法：** 

  ```
  原因是 nodejs 和hexo 的版本不匹配，可以降低nodejs 的版本为 12.14 
  在控制面版-程序，将node js 卸载了
  下载nvm : https://github.com/coreybutler/nvm-windows/releases
  下载 nvm-setup.zip , 解压安装 
  > nvm install 12.14 
  > nvm use 12.14 
  ```

* **nvm 的常见命令**

  ```
  nvm                  // 会提示nvw下的相关命令
  nvm ls               // 查看已安装node版本
  nvm install vXX      // 安装对应vXX版本的node
  nvm uninstall vXX    // 卸载对应vXX版本的node
  nvm use xxx          // 选择使用XXX版本
  ```

* 在利用nvm 安装node 的时候可能出现的问题

  -  **[踩坑 A ]**

    ：很多人反馈只有在git cmd 或 git bash（或某指定的文件夹）可以使用，但在项目文件下使用NVM无法切换

    **[问题原因]**：在安装nvm前安装了node版本或者安装了全局node

    **[解决方案]**：卸载已安装的node版本后重新安装NVM （控制面板--> 卸载程序）

  - **[ 踩坑 B ]：**当执行nvw install xxx 安装完指定版本时，您满心欢喜的要使用时 nvm use ...报错了，提示信息：

    exit status 乱码...

    **[问题原因]**：网上有些说安装要使用原默认目录c：盘符，也有些说要安装在根目录，其实是因为安装nvm时使用路径存在空格导致解析出错 （如：Program Files）

    **[解决方案]**：重新安装nvm避免路径存在空格，**安装完记得重启才会生效**

  - **[踩坑C]**：执行install 时node安装成功，但npm没成功

    **[问题原因]**：npm下载连接失败

    **[解决方案]**：nvm uninstall vxxx 卸载对应版本后 打开nvm文件夹中下的settings.txt添加以下代码添加淘宝镜像下载：

    ```
    root: D:\nvm
    path: D:\nvm\nodejs
    node_mirror: https://npm.taobao.org/mirrors/node/
    npm_mirror: https://npm.taobao.org/mirrors/npm/
    ```

    

