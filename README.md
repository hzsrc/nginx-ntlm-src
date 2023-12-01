# nginx-ntlm-src
基本情况是这样的：

用户使用AD域用户登录了Windows系统，打开网站外网域名（非内网IP）时，需要使用这个登录的AD帐号自动进入Web系统。外网域名映射到一台安装了nginx的Linux服务器，通过nginx负载均衡分发到两台Windows服务器上。

由于nginx默认不支持NTLM认证，导致打开网站域名时认证失败，一直重复弹出帐号密码输入框。

经过网上查阅了大量资料，并反复尝试，解决的方法是需要启用一个nginx-ntlm-module的nginx模块，办法如下：

1、下载nginx源码及依赖的源码包。有点麻烦，见后面提供的源码包。    
2、下载nginx-ntlm-module源码：https://github.com/gabihodoroaga/nginx-ntlm-module 。    
3、编译源码为可执行文件，并安装到linux。    
4、按模块说明的配置nginx.conf。    
![](https://segmentfault.com/img/bVc7Ho7)

为方便起见，我整理了一个源码包，将其放到Linux上解压缩，执行里面_build_install_linux.sh即可完成编译并安装到/usr/local/nginx/目录。


