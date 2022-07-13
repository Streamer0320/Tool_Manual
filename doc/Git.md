[返回](../../U2Note.md)

# Git

[TOC]

## 远程仓库的连接

### 本地配置

**说明：** 本地配置是利用 Git 在当前计算机生成 SSH 公钥和私钥文件，然后在 GitHub 远程库保存 SSH 公钥，该过程一次配置，长期有效。

**步骤：**

```git
# Your Name 为当前计算机对所配置远程库提交的 Name，可自定义
git config --global user.name "Your Name"

# email@example.com 为远程库认证的邮箱，需要在 GitHub 上认证
git config --global user.email "email@example.com"
```

使用git config --list可查看配置的相关信息

###  连接 GitHub

生成 SSH 公钥:

```git
ssh -keygen -t rsa -C "email@example.com"  
```

公钥就在 id_rsa.pub 文件中，在 GitHub 新建 SSH keys 填入该文件所有内容，SSH keys 名称任意

### 验证

```git
ssh -T git@github.com
```


## 本地库和初始化

**说明：** 该过程是在 GitHub 创建空库，然后克隆到本地库的过程，本地库实质是一个被初始化的文件夹，由于初始化配置完成后相关配置信息都在该文件夹内的 .Git 隐藏文件夹中，所以该本地库不受绝对定位的影响。

### 远程库创建

创建空的远程库，复制 Code 的 ssh 地址 ```git@github.com:github.user/repository.git```

其中 ```github.user``` 为 GitHub 用户名，```repository``` 为仓库名

### 本地库初始化

```git
# 初始化本地库，创建本地库配置框架
git init
# 链接远程库，本地库配置框架中记录远程库信息
git remote add origin git@github.com:github.user/repository.git
# 添加一个本地命名为origin的、远程链接为git@github.com:github.user/repository.git的库
```



## Git 操作手册

[参考引用](https://tsejx.github.io/devops-guidebook/code/git)

![Git 操作逻辑关系](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015120901.png)

**Git 基本概念**

**Workspace**: 工作区 - 就是你在电脑里能看到的目录

**Index / Stage**: 暂存区 - 一般存放在 .git 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）

**Repository**: 仓库区（或本地库）- 工作区有一个隐藏目录 .git，这个不算工作区，而是 Git 的本地版本库，仓库所有版本信息都会存在这里
Remote: 远程仓库

---

### git 命令

```git status``` 查询 ```git add``` 后 ```git commit``` 前的内容

```git log``` 查询分支操作日志

```git reflog``` 查询库操作日志

```git reset --hard <commit_id>``` 回滚到某一个版本

>  ```<commit_id>``` 为操作的 hash 值（可通过 ```git log``` 或 ```git reflog``` 查看）

```git checkout <commit_id> <path> ```

> ```<path>``` 为操作文件的路径
