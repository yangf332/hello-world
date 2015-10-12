SSH
====================



## FAQ
* warning:unprotected private key file!
  - 权限问题，修改为chmod 700 {filename}
* 多文件切换
  - ~/.ssh/config
  - Host xxx
  - Hostname ip
  - Port 22
  - User username    
  - IdentityFile ~/.ssh/{filename}


### 相关资料
[SSH原理与运用（一）：远程登录](http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html)

[SSH原理与运用（二）：远程操作与端口转发](http://www.ruanyifeng.com/blog/2011/12/ssh_port_forwarding.html)

