---
title: CentOS 7 下 安装 Python3.7
tags:
  - 安装Python3.7
categories:
  - Python3.7
abbrlink: b40cfc72
date: 2019-03-15 19:12:41
---
<h1>
CentOS 7 安装 Python3
</h1>

<h2>
一、 直接安装
</h2>

### 1. 添加源(非必须)(命令添加epel扩展源) ###
### 2. 更新软件包 ###
### 3. 安装yum-utils ###
### 4. 安装 "Development"/"Development tools" 软件组,(因为使用源码方式在 CentOS 7 系统中安装 Python 3.7，所以必须安装 GCC 编译器和 make 编译工具，这些软件包包含在 “Development tools” 软件组中，可以直接安装 “Development tools” 软件组) ###
### 5. 添加IUS源,(包含IUS为RHEL和CentOS编译单独的包) ###
### 6. 安装python36,(若出问题，可跳过) ###

```js
#运行这个命令添加epel扩展源
sudo yum -y install epel-release
#运行这个命令更新软件包
sudo yum update
#运行这个命令安装yum-utils
sudo yum install yum-utils
#运行这个命令安装 "Development"软件组
sudo yum groupinstall development
sudo yum groupinstall "Development tools"
#运行这个命令添加IUS源
sudo yum install https://centos7.iuscommunity.org/ius-release.rpm
#运行这个命令安装python36
sudo yum install python36u
```

<h2>
二、 从源码编译安装
</h2>

### 1. 我们先看看现有的 python2在哪里 ###

```js
[root@lidan /]# whereis python
python: /usr/bin/python /usr/bin/python2.7 /usr/bin/python.bak /usr/lib/python2.7 /usr/lib64/python2.7 /etc/python /usr/include/python2.7 /usr/share/man/man1/python.1.gz
```
```js
[root@lidan bin]# ll python*
lrwxrwxrwx. 1 root root    9 5月  27 2016 python2 -> python2.7
-rwxr-xr-x. 1 root root 7136 11月 20 2015 python2.7
lrwxrwxrwx. 1 root root    7 5月  27 2016 python.bak -> python2
```

### 2. 接下来我们要安装编译 Python3的相关包 ###

```js
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make libffi-devel
```

#### 这里面有一个包很关键libffi-devel，因为只有3.7才会用到这个包，如果不安装这个包的话，在 make 阶段会出现如下的报错： ####

```js
# ModuleNotFoundError: No module named '_ctypes'
```

### 3. 安装pip，因为 CentOs 是没有 pip 的。 ###

```js
#运行这个命令添加epel扩展源 
yum -y install epel-release 
#安装pip 
yum install python-pip
```

### 4. 可以用 python 安装一下 wget ###

```js
pip install wget
```

### 5. 我们可以下载 python3.7的源码包了 ###

```js
wget https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tgz
```

```js
#解压缩
tar -zxvf Python-3.7.2.tgz

#进入解压后的目录，依次执行下面命令进行手动编译
./configure prefix=/usr/local/python3 
make && make install
```

#### 如果最后没提示出错，就代表正确安装了，在/usr/local/目录下就会有python3目录 ####

### 6. 添加软链接 ###

```js
#添加python3的软链接 
ln -s /usr/local/python3/bin/python3.7 /usr/bin/python3.7
ln -s /usr/local/python3/bin/python3-config /usr/bin/python3-config
cd /usr/bin
ln -s python3.7 /usr/bin/python3
rm -rf python python-config
ln -s python3 /usr/bin/python
ln -s python3-config /usr/bin/python-config
#添加 pip3 的软链接 
ln -s /usr/local/python3/bin/pip3.7 /usr/bin/pip3.7
cd /usr/bin
ln -s pip3.7 /usr/bin/pip3
#测试是否安装成功了 
python -V
```

### 7. 更改yum配置，因为其要用到python2才能执行，否则会导致yum不能正常使用（不管安装 python3的那个版本，都必须要做的） ###

```js
vi /usr/bin/yum 
把 #! /usr/bin/python 修改为 #! /usr/bin/python2 
vi /usr/libexec/urlgrabber-ext-down 
把 #! /usr/bin/python 修改为 #! /usr/bin/python2
```
