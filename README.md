# Git和GitHub的使用





## Git是什么？

- 每一段代码的改动，Git都会帮你记录下来，就像是在写日记。
- 如果出现问题或者想查看之前的版本，Git可以带你找到任意时间点的代码状态。



## Git的主要特点

1.**版本控制：**每次提交就像写了一篇新日记，保存你的开发成果。

2.**分支管理：**分支就像章节，可以并行开发而互不干扰。

3.**分布式：**每个人都拥有完整的“日记本”，即使没有网络也可以工作。



## 安装Git

[Git官网](https://git-scm.com/)

[Sourcetree官网](https://www.sourcetreeapp.com/)

[GitHub官网](https://github.com)



## GitHub是什么？

**GitHub：全球化的代码社交云平台**

- 比喻：GitHub是“全球代码图书馆”。
- 可以把代码上传到GitHub，随时随地访问，并与他人协作开发，甚至分享到全世界。
- 优势：拥有庞大的开源社区。是学习和参与开源项目的最佳平台。



## Git常用命令

```shell
# 配置用户名和邮箱
git config --global user.name "名字"
git config --global user.email "邮箱"

# 初始化仓库
git init

# 添加文件到暂存区
git add .
git add /your/file

# 提交到本地仓库
git commit -m "提交说明"

# 推送代码到远程仓库
git push -u origin main

# 克隆远程仓库
git clone 仓库地址

# 添加远程仓库
git remote add origin git@github.com/yourrepository.git

# 验证远程仓库配置
git remote -v

# 查看当前分支
git branch

#切换并创建分支
git switch -C 分支名

# 将远程仓库的更改与本地更改合并，并创建一个新的合并并提交
git merge master
```



## SSH配置步骤

1.配置个人信息

```shell
git config --global user.name "名字"
git config --global user.email "邮箱"
```

2.生成SSH密钥

```shell
ssh-keygen -t rsa -C "邮箱"
```

- `-t rsa`: 使用RSA算法生成密钥。
- `-C`: 添加备注，通常为邮箱地址。

3.将GitHub的SSH端口改为443

```shell
# Linux
echo -e "Host githb.com\n Hostname ssh.github.com\n Port 443" >> /root/.ssh/config
```



## 创建Git仓库

```shell
# 创建一个目录
mkdir reposttory && cd repository

# 初始化仓库
git init

# 创建README.md
touch README.md

# 添加文件到暂存区
git add .

# 提交到本地仓库
git commit -m "Update README.md"

# 查看冲突文件
git status

# 添加远程仓库
git remote add origin git@github.com:Aurorapyc/repository.git

#将本地的main分支推送到远程仓库origin上
git push -u origin main 
```

使用`git push -u`的优势：

- 设置了上游分支，可以直接使用`git push`或`git pull`



## 设置网络代理

```shell
# 设置全局代理
git config --global http.proxy http://127.0.0.1:10808
git config --global https.proxy https://127.0.0.1:10808

# 验证配置
git config --global --get http.proxy
git config --global --get https.proxy

# 取消代理
git config --global --unset http.proxy
git config --global --unset https.proxy
```



## 多分支协同开发

当要修改代码和文件是可以创建一个名为master的分支进行开发。

```shell
git branch -c master
```

当提交完成后，可以将master分支合并到main分支上，最后在提交到仓库里。

```shell
git switch main
git merge master
git push -u origin main
```

