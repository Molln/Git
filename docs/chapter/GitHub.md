# GitHub

### 一 账号注册

https://github.com/

### 二 创建远程库

New Repository

### 三 创建远程库别名

查看当前所有远程地址别名

````
git remote -v
````

添加远程库别名

````
git remote add [别名] [远程地址]
````

### 四 推送

````
git push [别名] [分支名]
````

### 五 克隆

````
git origin [远程地址]
````

* 完整的将远程库下载到本地
* 创建 origin 远程地址别名
* 初始化本地库

### 六 团队成员邀请

### 七 拉取

pull=fetch+merge
git fetch [远程库地址别名] [远程分支名]
git merge [远程库地址别名/远程分支名]
git pull [远程库地址别名] [远程分支名]

### 八 冲突解决

如果不是基于 GitHub 远程库的最新版所做的修改，不能推送，必须先拉
取。
拉取下来后如果进入冲突状态，则按照“分支冲突解决”操作解决即可。

### 九 跨团队协作

Fork

* 团队2 Fork 团队1 的项目
* 团对2 进行修改并创建一个 Pull Request
* 团对1 审核并合并代码

### 十 SSH 登录

#### 1 进入当前用户的家目录

````
$ cd ~ 
````

#### 2 删除.ssh 目录

````
$ rm -rvf .ssh
````

#### 3 运行命令生成.ssh 密钥目录

````
$ ssh-keygen -t rsa -C atguigu2018ybuq@aliyun.com
````

[注意：这里-C 这个参数是大写的 C]

#### 4 进入.ssh 目录查看文件列表

````java
$ cd .ssh
$ ls -lF
````

#### 5 查看 id_rsa.pub 文件内容

`````
$ cat id_rsa.pub
`````

#### 6 GitHub 设置

复制 id_rsa.pub 文件内容，登录 GitHub，点击用户头像→Settings→SSH and GPG keys New SSH Key 输入复制的密钥信息

#### 7 回到 Git bash 创建远程地址别名

````
git remote add origin_ssh git@github.com:atguigu2018ybuq/huashan.git
````



