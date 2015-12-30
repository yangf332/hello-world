Nginx
====================

## 安装
* for mac 使用brew
  - brew update
  - brew install nginx
* yum安装
  - rpm -ivh http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm
  - yum info nginx
  - yum install nginx
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

#### 配置环境变量
    在location ~ \.php${
        fastcgi_param {key} {value};
    }    
    // 类似于apache的 SetEnv {key} {value}
    // 另一种方式是修改.htaccess
    // SetEnv {key} {value}

#### 配置常用rewrite
* 判断
  - -f !-f 判断是否存在文件
  - -d !-d 判断是否存在目录
  - -e !-e 判断是否存在文件或目录
  - -x !-x 判断文件是否可执行
* flag标记
  - last 相当于Apache里的[L]标记，表示完成
  - break 终止匹配，不再匹配后面的规则
  - redirect 返回302临时重定向
  - permanent 返回301永久重定向
* 可用的全局变量
  - $args, $host,  $limit_rate
  - $content_lenth, $content_type
  - $document_root, $document_uri
  - $http_user_agent, $http_cookie
  - $request_body_file, $request_method, $request_filename, $request_uri
  - $remote_addr, $remote_port, $remote_user
  - $query_string, $scheme
  - $server_protocol, $server_addr, $server_name, $server_port

````
    location / {
        index  index.php index.html index.htm;
        if (-f $request_filename/index.html){
            rewrite (.*) $1/index.html break;
        }
        if (-f $request_filename/index.php){
            rewrite (.*) $1/index.php;
        }
        if (!-f $request_filename){
            rewrite (.*) /index.php;
        }
    }
    // others
    rewrite ^/(.*)([^/])$ http://$host/$1$2/ permanent;  // 后缀加'/'
    rewrite ^(.*)list-([0-9]+)-([0-9]+)\.html$ $1/list.php?catid=$2&page=$3;
````

#### 操作php-fpm
* 查看php-fpm的配置文件位置
  - ps aux | grep php-fpm
* cat /etc/php-fpm.conf 找到
  - pid = /var/run/php-fpm/php-fpm.pid
* 操作
  - kill -INT \`cat /var/run/php-fpm/php-fpm.pid\`  // 关闭
  - kill -USR2 \`cat /var/run/php-fpm/php-fpm.pid\` // 重启

## FAQ
* 静态资源访问报错：ERR_INCOMPLETE_CHUNKED_ENCODING，查看日志：open() "/nginx/fastcgi_temp/1/02/0000000021" failed (13: Permission denied) while reading upstream, client: x.x.x.x
  - 原因是nginx配置信息里的user与fastcgi_temp所属用户不一致引起
  - 修改，例如：chown -R www:www fastcgi_temp

### 相关书籍


### 相关资料
[官网](http://nginx.org/)


