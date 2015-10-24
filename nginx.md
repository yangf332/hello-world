Nginx
====================

## 安装
* for mac 使用brew
  - brew update
  - brew install nginx
* 编译安装
  - 安装pcre 
    - 在www.pcre.org下载最新版本
    - tar zxvf pcre-{v}.tar.gz
    - ./configure --prefix=/usr/local
    - make && make install
  - 安装nginx
    - 在nginx.org下载最新版本
    - ./configure
    --sbin-path=/usr/local/nginx/nginx
    --conf-path=/usr/local/nginx/nginx.conf
    --pid-path=/usr/local/nginx/nginx.pid
  - make && make install
* 设置自启动
  - for mac 
    - vim /Library/LaunchDaemons/org.nginx.plist
    - launchctl load /Library/LaunchDaemons/org.nginx.plist

## 使用
* 启动 /usr/local/nginx/nginx
* 重启 nginx -s reload
* 关闭 nginx -s stop
* 查看编译参数 nginx -V
* 查看配置文件是否正确 nginx -t
* 加入环境变量 vim ~/.bash_profile; export PATH=$PATH:/usr/local/nginx; source .bash_profile



## 配置
/var/www/vhost/{domain}.conf
/var/www/sites/{domain}/
/var/www/logs/{domain}_access.log, {domain}_error.log



### 相关书籍


### 相关资料
[官网](http://nginx.org/)


