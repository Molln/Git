# Gitlab

## 一 相关网址

### 1 官网

<https://about.gitlab.com/>

### 2 安装说明

<https://about.gitlab.com/install/>

### 3 下载地址

<https://packages.gitlab.com/gitlab/gitlab-ce>

### 4 版本说明

GitLab CE	GitLab Community Edition

GitLab EE	GitLab Enterprise Edition

## 二 安装

### （一）官方推荐步骤

#### 1 安装和配置必要的依赖项

开启 HTTP，HTTPS，SSH 访问

````
sudo yum install -y curl policycoreutils-python openssh-server
sudo systemctl enable sshd
sudo systemctl start sshd
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo systemctl reload firewalld
````

接下来，安装 Postfix 发送通知电子邮件。如果要使用其他解决方案发送电子邮件，请跳过此步骤并 在安装GitLab之后 [配置外部SMTP服务器](https://docs.gitlab.com/omnibus/settings/smtp.html) 。

````
sudo yum install postfix
sudo systemctl enable postfix
sudo systemctl start postfix
````

在 Postfix 安装过程中，可能会出现一个配置屏幕。选择“ Internet网站”，然后按Enter。使用服务器的外部DNS作为“邮件名”，然后按Enter。如果出现其他屏幕，请继续按Enter接受默认设置。

#### 2 添加GitLab软件包存储库并安装软件包

添加GitLab软件包存储库。

````
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh | sudo bash
````

接下来，安装 GitLab 软件包。更改 `https://gitlab.example.com` 为您要访问GitLab实例的URL。安装将自动配置并在该 URL 上启动 GitLab。

对于 `https://`URL，GitLab 将 [使用Let's Encrypt](https://docs.gitlab.com/omnibus/settings/ssl.html#lets-encrypthttpsletsencryptorg-integration) 自动 [请求证书](https://docs.gitlab.com/omnibus/settings/ssl.html#lets-encrypthttpsletsencryptorg-integration) ，这需要入站HTTP访问和有效的主机名。您也可以 [使用自己的证书](https://docs.gitlab.com/omnibus/settings/nginx.html#manually-configuring-https) 或仅使用http：//。

````
sudo EXTERNAL_URL="https://gitlab.example.com" yum install -y gitlab-ee
````

#### 3 浏览到主机名并登录

首次访问时，您将被重定向到密码重置屏幕。

提供初始管理员帐户的密码，您将被重定向回登录屏幕。使用默认帐户的用户名`root`登录。

有关 [安装和配置的详细说明](https://docs.gitlab.com/omnibus/README.html#installation-and-configuration-using-omnibus-package) 请参见 [文档](https://docs.gitlab.com/omnibus/README.html#installation-and-configuration-using-omnibus-package) 。

#### 4 设置您的通信首选项

请访问 GitLab 的 [电子邮件订阅首选项中心](https://about.gitlab.com/company/preference-center/) 以告知我们何时与您联系。我们有明确的电子邮件接收政策，因此您可以完全控制我们向您发送电子邮件的时间和频率。

我们每月两次发送您需要了解的GitLab新闻，包括新功能，集成，文档以及我们开发团队的幕后故事。有关与错误和系统性能有关的重要安全更新，请注册我们的专用安全新闻。

#### 官方推荐步骤命令合集

````
sudo yum install -y curl policycoreutils-python openssh-server
sudo systemctl enable sshd
sudo systemctl start sshd
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo systemctl reload firewalld
sudo yum install postfix
sudo systemctl enable postfix
sudo systemctl start postfix
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh | sudo bash
sudo EXTERNAL_URL="https://gitlab.example.com" yum install -y gitlab-ee
````

问题：yum 安装 gitlab-ee(或 ce)时，需要联网下载几百 M 的安装文件，非常耗时，所以应提前把所需 RPM 包下载并安装好。

### （二）调整后命令

````
sudo yum install -y curl policycoreutils-python openssh-server
sudo systemctl enable sshd
sudo systemctl start sshd
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo systemctl reload firewalld
sudo yum install postfix
sudo systemctl enable postfix
sudo systemctl start postfix
sudo rpm -ivh /opt/gitlab-ce-12.7.8-ce.0.el7.x86_64.rpm
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh | sudo bash
sudo EXTERNAL_URL="https://gitlab.example.com" yum install -y gitlab-ce-12.7.8-ce.0.el7.x86_64.rpm
````

重启

## 三 GitLab 服务操作

### 1 初始化配置 GitLab

````
gitlab-ctl reconfigure
````

### 2 启用 GitLab

````
gitlab-ctl start
````

### 3 停止 GitLab

````
gitlab-ctl stop
````

## 四 访问

访问 Linux 服务器 IP 地址即可，如果想访问 EXTERNAL_URL 指定的域名还需要配置域名服务器或本地 hosts 文件。初次登录时需要为 gitlab 的 root 用户设置密码。

## 五 参考文档

<https://blog.csdn.net/iyouju/article/details/104114951>