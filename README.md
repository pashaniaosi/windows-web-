# 用虚拟机搭建windows的web开发环境
   利用虚拟机搭建虚拟服务器，并实现在windows本地下的web开发

## 用虚拟机安装虚拟服务器
* 我使用的是vmware安装ubuntu server 16.04，具体实现可以根据自己的习惯与需求自行调解
* ubuntu服务器的下载地址：[ubuntu server](https://www.ubuntu.com/download/server)
## windows本地实现虚拟服务器的远程连接
* 参考地址: [原文链接](http://www.linuxidc.com/Linux/2017-01/139530.htm)
1. 由于vmware支持ubuntu系统的简易安装，如果选择的是简易安装则需要继续以下步骤，否则可以省略，因为非简易安装可以自行选择需要的软件，
  如ssh服务和LAMP server，帮助我们安装好所需的环境
  ![software](http://images2015.cnblogs.com/blog/855959/201611/855959-20161115001841310-1770251240.png)<br>
2. 安装ssh服务和配置虚拟网络，实现虚拟机的远程连接，具体操作可以参考链接的内容，之后我们可以在cmd中测试虚拟机的ip的ping值来检验是否成功实现远程连接<br><br>
`cmd中的命令为: ping your ip-address`<br><br>
如果ping没问题，那么远程连接成功了，这个时候我们就可以使用xshell或putty等软件连接并实现对系统的操作<br><br>
3. 但是普通用户无法对服务器中的文件实现上传和下载，这样就会影响到我们的本地开发(这里可以使用winscap软件来便捷地实现对服务器文件的操作)，所以我们修改ssh的配置文件，允许使用root用户(首先要创建ubuntu的root用户)远程连接或是新建一个拥有管理员权限的用户<br>
这里我们实现一下第一种方法：修改`/etc/ssh/sshd_config`ssh的配置文件，将PermitRootLogin的值改成yes，因为为root账户设置了密码，所以还要更改PermitEmptyPasswords为no，这个时候给我们就可以使用root用户远程连接
