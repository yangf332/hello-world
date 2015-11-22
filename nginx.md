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
* 目录结构
  - /var/www/vhost/{domain}.conf
  - /var/www/sites/{domain}/
  - /var/www/logs/{domain}_access.log, {domain}_error.log

#### 配置401认证
    htpasswd -b[cmBdpsDv] [-C cost] passwordfile username password
    vim nginx.conf
    location / {
      auth_basec "401";
      auth_basic_user_file [passwordfile];
    }
    service nginx restart
    

## FAQ
* 静态资源访问报错：ERR_INCOMPLETE_CHUNKED_ENCODING，查看日志：open() "/nginx/fastcgi_temp/1/02/0000000021" failed (13: Permission denied) while reading upstream, client: x.x.x.x
  - 原因是nginx配置信息里的user与fastcgi_temp所属用户不一致引起
  - 修改，例如：chown -R www:www fastcgi_temp

### 相关书籍


### 相关资料
[官网](http://nginx.org/)


