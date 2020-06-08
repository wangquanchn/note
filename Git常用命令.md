# Git Reference



## 设置和配置 Setup and Config



## 获取和创建项目 Getting and Creating Projects

### init

```shell
git init
```

git初始化



## Basic Snapshotting

## Branching and Merging

## Sharing and Updating Projects

### remote

设置remote地址

```shell
git remote add origin 地址
```

查看远程分支信息

```shell
git remote -v
```

设置项目远程仓库地址

```	shell
git remote set-url origin 项目地址
```

更新远程分支列表

```shell
git remote update origin --prune
```





## Inspection and Comparison

## Patching

## Debugging

## Guides

## Email

## External Systems

## Administration

## Server Admin

## Plumbing Commands















获取远程仓库master分支上的内容

git pull origin master

将当前分支设置为远程仓库的master分支

git branch --set-upstream-to=origin/master master



将全部文件加入git版本管理 .的意思是将当前文件夹下的全部文件放到版本管理中

git add .

提交文件 使用-m 编写注释

git commit -m "注释"

推送到远程分支

git push







