---
title: Git
description: linux下git建立仓库的使用
tags: basic
---


## github的安装

sudo apt-get install git

## github

建立仓库，以github.io命名

## 本地仓库

**生成密钥**
ssh-keygen -t rsa -C "XXX@qq.com"

    双引号内是你的github注册地址，所有提示可直接回车默认选项
    若有多个密钥则可设定位置


**查看密钥**
cat ~/.ssh/id_rsa.pub
需复制全部内容

**复制密钥**

打开github-用户-setting-SSHKEY-add-复制

**检查链接**

ssh -T git@github.com

    成功标志
    You’ve successfully authenticated, but GitHub does not provide shell access

**身份验证**

    git config --global user.name ""   //配置用户名
    git config --global user.email "2460205801@qq.com"    //配置email

**仓库下载**

    git clone http

**上传文件**

    git add 文件名
    git commit -m "注释"
    git push

若需要输入用户名以及密码：

    username：邮箱地址
    password：Account setting-> Developer setting-> Fine-grained token 创立密钥并输入
