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
`cmd中的命令为: ping your ip-address`<br>
如果ping没问题，那么远程连接成功了，这个时候我们就可以使用xshell或putty软件连接并实现对系统的操作<br>
3. 
