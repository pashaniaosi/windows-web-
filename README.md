# 用虚拟机搭建windows的web开发环境
   利用虚拟机搭建虚拟服务器，并实现在 windows 本地下的 web 开发

## 用虚拟机安装虚拟服务器
* 我使用的是 vmware 安装 ubuntu server 16.04，具体实现可以根据自己的习惯与需求自行选择
* ubuntu 服务器的下载地址：[ubuntu server](https://www.ubuntu.com/download/server)
## windows本地实现虚拟服务器的远程连接
* [原文链接](http://www.linuxidc.com/Linux/2017-01/139530.htm)
1. 由于 vmware 支持 ubuntu 系统的简易安装，如果选择的是简易安装则需要继续以下步骤，否则可以省略，因为非简易安装可以自行选择需要的软件，
  如 ssh 服务和 LAMP server，帮助我们安装好所需的环境
  ![software](http://images2015.cnblogs.com/blog/855959/201611/855959-20161115001841310-1770251240.png)<br>
2. 安装 ssh 服务和配置虚拟网络，实现虚拟机的远程连接，具体操作可以参考链接的内容，之后我们可以在 cmd 中测试虚拟机的 ip 的 ping 值来检验是否成功实现远程连接<br><br>
`cmd中的命令为: ping your ip-address`<br><br>
如果 ping 没问题，那么远程连接成功了，这个时候我们就可以使用 xshell 或 putty 等软件连接并实现对系统的操作<br><br>
3. 但是普通用户无法对服务器中的文件实现上传和下载，这样就会影响到我们的本地开发( 这里可以使用 winscap 软件来便捷地实现对服务器文件的操作 )，所以我们修改 ssh 的配置文件，允许使用 root 用户( 首先要创建 ubuntu 的 root 用户 )远程连接或是新建一个拥有管理员权限的用户<br><br>
这里我们实现一下第一种方法：修改 `/etc/ssh/sshd_config` ssh的配置文件，将 PermitRootLogin 的值改成yes，因为为 root 账户设置了密码，所以还要更改 PermitEmptyPasswords 为 no，重启 ssh，这个时候给我们就可以使用 root 用户远程连接
## 搭建php的开发环境
* 这个时候我们只需在 xshell 或 putty 的命令行中安装配置 php 的开发环境([参考链接](http://www.cnblogs.com/wenanry/archive/2012/11/13/2767779.html))
* 我们可以安装 phpmyadmin 实现数据库的管理，但是如果我们要在本地使用类似于 navicat 的数据库管理软件进行管理，我们还需要修改 mysql 的配置([参考链接](http://jingyan.baidu.com/article/64d05a0258526dde54f73b6a.html))，除此之外，还要修改mysql的bind-address，默认绑定的是本地地址，配置文件是 `/etc/mysql/mysql.conf.d/mysqld.cnf` ，其实质就是让 mysql 允许非本地的用户连接数据库
## 实现本地开发
1. 我们可以使用 winscp 软件( 注意要有 root 权限 )将服务器中 web 开发的根目录( apache服务器默认的 DocumentRoot:  `/var/www/html` ，具体的配置可以自行修改 )复制到本地进行开发，之后上传至服务器中，只需在本地的浏览器访问服务器的 ip 就可以查看自己的开发成果
2. 推荐使用IDE实现上诉操作，如 phpstorm 中在 `Tools->Deployment->Configuration` 配置好远程连接的服务器、复制的文件夹路径以及本地的路径( 同是 root 权限 )，就可以方便的使用自带的 `Download` 和 `Upload` 功能实现下载和上传，便可以方便地进行本地开发，甚至可以用 `Tools->Start SSH session` 实现 ssh 连接( xshell 和 putty 都省了 )
3. 现在我们就可以在 windows 环境下愉快地开发了，不用再为在 windows 下搭建 php 开发环境而烦恼( 个人觉得在 windows 下搭建 web 开发环境很麻烦 )
