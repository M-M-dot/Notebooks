# github 的常见用法

[toc]

https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html

用户名/密码： M-M-dot    github1314520



## 常见命令

###  create a new repository on the command line

```
echo "# bustub2" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:M-M-dot/bustub2.git
git push -u origin main
```

###   push an existing repository from the command line

```
// 在本地添加远程仓库  名字是origin 链接是git url 
git remote add origin git@github.com:M-M-dot/bustub2.git
// 
git branch -M main
// 
git push -u origin main

```

###  TAG

```
// 新建标签 v1.4 备注是 my version 1.4
git tag -a v1.4 -m "my version 1.4"
// 当前所有的标签
git tag 
// 使用 git show 命令可以看到标签信息和与之对应的提交信息
git show v1.4 
//切换标签版本 
 git checkout v1.4
 //将标签同步到远程仓库
 git push remote_name  --tags  // 同步所有标签
 git push remote_name tagname // 同步tagname 这个标签 
```



## 常见报错

1. ```
   $ git push --mirror https://github.com/M-M-dot/bustub.git
   报错： 用户名密码一直输入不对
   报错： fatal: unable to access 'https://github.com/M-M-dot/bustub.git/': Failed to connect to github.com port 443: Timed out
   解决方法： 设置ssh-key 使用ssh的方式push 上去
   $ git push git@github.com:M-M-dot/bustub.git
   ```

## 设置ssh-key 

```cmd
ssh-keygen -t rsa -C "10175300204@stu.ecnu.edu.cn"
```

一直回车，生成id_rsa.pub 

将id_rsa.pub 的内容复制到github-setting - ssh- newsshkey 中，就可以生成ssh-key . 

其作用是加密传输内容

设置ssh-key 之后，就可以通过git@lru 的方式进行push 和clone 















