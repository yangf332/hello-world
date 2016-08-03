SVN
====================

### 安装

#### CentOS安装配置
* 安装：yum install subversion -y
* mkdir -p /opt/data/
* 创建：svnadmin create /opt/data/svn
* 配置：
  - vim conf/svnserve.conf
    - anon-access = none    #未鉴定的用户无权限访问该仓库
    - auth-access = write   #鉴定后的可读写仓库
    - password-db = passwd  #使用的密码文件是同级路径的passwd文件
    - authz-db = authz#使用的权限控制文件是同级路径的authz文件
    - realm = svn1 #realm 指定版本库的仓库名
  - vim conf/passwd
    - {uesrname} = {password}
  - vim conf/authz
    - [groups] {usergroup}={user1},{user2}
    - [repository:/baz/fuz] 
      - [{svnname}:/] @{usergroup} = rw
      - {user1} = rw
      - \* =
* 启动： svnserve -d -r /opt/data # -d:指放在后台运行 -r：指定仓库目录

### 相关书籍


### 相关资料
[HTTP基本认证](https://zh.wikipedia.org/wiki/HTTP基本认证)


