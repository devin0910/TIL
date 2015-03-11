## UBUNTU14.04环境快速搭建LEMP

### 更改源
 1. 备份源文件
 `cp /etc/apt/sources.list /etc/apt/sources.list.backup`
 2. 覆盖源文件内容

deb http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse

 3. 更新源
	 `apt-get update`

### 安装PHP5.6

 1. 安装python-software-properties
 `sudo apt-get update && sudo apt-get install python-software-properties`
 2. 添加新的PPA
 `sudo add-apt-repository ppa:ondrej/php5-5.6`
 3. 更新源
 `sudo apt-get update && sudo apt-get upgrade`
 4. 安装PHP
 `sudo apt-get install php5 php5-fpm`
 5. 安装PHP开发工具集
 `sudo apt-get install php5-dev`

### 安装MySQL
 `sudo apt-get install mysql-server php5-mysql`

 `sudo mysql_install_db`

 `sudo /usr/bin/mysql_secure_installation`

### 安装Nginx
 `echo "deb http://ppa.launchpad.net/nginx/stable/ubuntu $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/nginx-stable.list`

 `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C300EE8C`
 
 `sudo apt-get update`
 
 `sudo apt-get install nginx`
