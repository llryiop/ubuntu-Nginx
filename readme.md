Nginx ("engine x") 是一个高性能的 HTTP 和 反向代理 服务器，也是一个 IMAP/POP3/SMTP 代理服务器。 Nginx 是由 Igor Sysoev 为俄罗斯访问量第二的 Rambler.ru 站点开发的，第一个公开版本0.1.0发布于2004年10月4日。其将源代码以类BSD许可证的形式发布，因它的稳定性、丰富的功能集、示例配置文件和低系统资源的消耗而闻名。

安装Nginx依赖库

安装gcc g++的依赖库
ubuntu平台可以使用如下命令。

apt-get install build-essential
apt-get install libtool
centeros平台可以使用如下命令。


centos平台编译环境使用如下指令
安装make：
yum -y install gcc automake autoconf libtool make
 
安装g++:
yum install gcc gcc-c++　　
安装 pcre依赖库（http://www.pcre.org/）
1
2
sudo apt-get update
sudo apt-get install libpcre3 libpcre3-dev
安装 zlib依赖库（http://www.zlib.net）
1
apt-get install zlib1g-dev
安装 ssl依赖库
1
apt-get install openssl
安装Nginx（http://nginx.org）


#下载最新版本：
wget http://nginx.org/download/nginx-1.11.3.tar.gz
#解压：
tar -zxvf nginx-1.11.3.tar.gz
#进入解压目录：
cd nginx-1.11.3
#配置：
./configure --prefix=/usr/local/nginx 
#编辑nginx：
make
注意：这里可能会报错，提示“pcre.h No such file or directory”,具体详见：http://stackoverflow.com/questions/22555561/error-building-fatal-error-pcre-h-no-such-file-or-directory
需要安装 libpcre3-dev,命令为：sudo apt-get install libpcre3-dev
#安装nginx：
sudo make install
#启动nginx：
sudo /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
注意：-c 指定配置文件的路径，不加的话，nginx会自动加载默认路径的配置文件，可以通过 -h查看帮助命令。
#查看nginx进程：
ps -ef|grep nginx
Nginx常用命令

启动 Nginx

/usr/local/nginx/sbin/nginx
 
./sbin/nginx　
停止 Nginx

./sbin/nginx -s stop
 
./sbin/nginx -s quit
-s都是采用向 Nginx 发送信号的方式。
Nginx重新加载配置
./sbin/nginx -s reload
指定配置文件
./sbin/nginx -c /usr/local/nginx/conf/nginx.conf
-c表示configuration，指定配置文件
查看 Nginx 版本
有两种可以查看 Nginx 的版本信息的参数。第一种如下：
./sbin/nginx -v
 
nginx: nginx version: nginx/1.0.0
另一种显示的是详细的版本信息：

poechant@ubuntu:/usr/local/nginx$ ./sbin/nginx -V
nginx: nginx version: nginx/1.0.0
nginx: built by gcc 4.3.3 (Ubuntu 4.3.3-5ubuntu4)
nginx: TLS SNI support enabled
nginx: configure arguments: --with-http_ssl_module --with-openssl=/home/luming/openssl-1.0.0d/
检查配置文件是否正确

poechant@ubuntu:/usr/local/nginx$ ./sbin/nginx -t
nginx: [alert] could not open error log file: open() "/usr/local/nginx/logs/error.log" failed (13: Permission denied)
nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
2012/01/09 16:45:09 [emerg] 23898#0: open() "/usr/local/nginx/logs/nginx.pid" failed (13: Permission denied)
nginx: configuration file /usr/local/nginx/conf/nginx.conf test failed
如果出现如上的提示信息，表示没有访问错误日志文件和进程，可以sudo（super user do）一下：

poerchant@ubuntu:/usr/local/nginx$ sudo ./sbin/nginx -t
nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
nginx: configuration file /usr/local/nginx/conf/nginx.conf test is successful
如果显示如上，则表示配置文件正确。否则，会有相关提示。
显示帮助信息

poechant@ubuntu:/user/local/nginx$ ./sbin/nginx -h
或者：
poechant@ubuntu:/user/local/nginx$ ./sbin/nginx -?