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
3. 但是普通用户无法对服务器中的文件实现上传和下载，这样就会影响到我们的本地开发(这里可以使用winscap软件来便捷地实现对服务器文件的操作)，所以我们修改ssh的配置文件，允许使用root用户(首先要创建ubuntu的root用户)远程连接或是新建一个拥有管理员权限的用户<br><br>
这里我们实现一下第一种方法：修改`/etc/ssh/sshd_config`ssh的配置文件，将PermitRootLogin的值改成yes，因为为root账户设置了密码，所以还要更改PermitEmptyPasswords为no，这个时候给我们就可以使用root用户远程连接
## 搭建php的开发环境
* 这个时候我们只需在xshell或putty的命令行中安装配置php的开发环境([参考链接](http://www.cnblogs.com/wenanry/archive/2012/11/13/2767779.html))
## 实现本地开发
1. 我们可以使用winscp软件(注意要有root权限)将服务器中web开发的根目录(apache服务器默认的DocumentRoot: `/var/www/html`，具体的配置可以自行修改)复制到本地进行开发，之后上传至服务器中，只需在本地的浏览器访问服务器的ip就可以查看自己的开发成果
2. 推荐使用IDE实现上诉操作，如phpstorm中在`Tools->Deployment->Configuration`配置好远程连接的服务器、复制的文件夹路径以及本地的路径(同是root权限)，就可以方便的使用自带的`Download`和`Upload`功能实现下载和上传，便可以方便地进行本地开发，甚至可以用`Tools->Start SSH session`实现ssh连接(xshell和utty都省了)
