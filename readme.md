Nginx ("engine x") ��һ�������ܵ� HTTP �� ������� ��������Ҳ��һ�� IMAP/POP3/SMTP ����������� Nginx ���� Igor Sysoev Ϊ����˹�������ڶ��� Rambler.ru վ�㿪���ģ���һ�������汾0.1.0������2004��10��4�ա��佫Դ��������BSD���֤����ʽ�������������ȶ��ԡ��ḻ�Ĺ��ܼ���ʾ�������ļ��͵�ϵͳ��Դ�����Ķ�������

��װNginx������

��װgcc g++��������
ubuntuƽ̨����ʹ���������

apt-get install build-essential
apt-get install libtool
centerosƽ̨����ʹ���������


centosƽ̨���뻷��ʹ������ָ��
��װmake��
yum -y install gcc automake autoconf libtool make
 
��װg++:
yum install gcc gcc-c++����
��װ pcre�����⣨http://www.pcre.org/��
1
2
sudo apt-get update
sudo apt-get install libpcre3 libpcre3-dev
��װ zlib�����⣨http://www.zlib.net��
1
apt-get install zlib1g-dev
��װ ssl������
1
apt-get install openssl
��װNginx��http://nginx.org��


#�������°汾��
wget http://nginx.org/download/nginx-1.11.3.tar.gz
#��ѹ��
tar -zxvf nginx-1.11.3.tar.gz
#�����ѹĿ¼��
cd nginx-1.11.3
#���ã�
./configure --prefix=/usr/local/nginx 
#�༭nginx��
make
ע�⣺������ܻᱨ����ʾ��pcre.h No such file or directory��,���������http://stackoverflow.com/questions/22555561/error-building-fatal-error-pcre-h-no-such-file-or-directory
��Ҫ��װ libpcre3-dev,����Ϊ��sudo apt-get install libpcre3-dev
#��װnginx��
sudo make install
#����nginx��
sudo /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
ע�⣺-c ָ�������ļ���·�������ӵĻ���nginx���Զ�����Ĭ��·���������ļ�������ͨ�� -h�鿴�������
#�鿴nginx���̣�
ps -ef|grep nginx
Nginx��������

���� Nginx

/usr/local/nginx/sbin/nginx
 
./sbin/nginx��
ֹͣ Nginx

./sbin/nginx -s stop
 
./sbin/nginx -s quit
-s���ǲ����� Nginx �����źŵķ�ʽ��
Nginx���¼�������
./sbin/nginx -s reload
ָ�������ļ�
./sbin/nginx -c /usr/local/nginx/conf/nginx.conf
-c��ʾconfiguration��ָ�������ļ�
�鿴 Nginx �汾
�����ֿ��Բ鿴 Nginx �İ汾��Ϣ�Ĳ�������һ�����£�
./sbin/nginx -v
 
nginx: nginx version: nginx/1.0.0
��һ����ʾ������ϸ�İ汾��Ϣ��

poechant@ubuntu:/usr/local/nginx$ ./sbin/nginx -V
nginx: nginx version: nginx/1.0.0
nginx: built by gcc 4.3.3 (Ubuntu 4.3.3-5ubuntu4)
nginx: TLS SNI support enabled
nginx: configure arguments: --with-http_ssl_module --with-openssl=/home/luming/openssl-1.0.0d/
��������ļ��Ƿ���ȷ

poechant@ubuntu:/usr/local/nginx$ ./sbin/nginx -t
nginx: [alert] could not open error log file: open() "/usr/local/nginx/logs/error.log" failed (13: Permission denied)
nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
2012/01/09 16:45:09 [emerg] 23898#0: open() "/usr/local/nginx/logs/nginx.pid" failed (13: Permission denied)
nginx: configuration file /usr/local/nginx/conf/nginx.conf test failed
����������ϵ���ʾ��Ϣ����ʾû�з��ʴ�����־�ļ��ͽ��̣�����sudo��super user do��һ�£�

poerchant@ubuntu:/usr/local/nginx$ sudo ./sbin/nginx -t
nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
nginx: configuration file /usr/local/nginx/conf/nginx.conf test is successful
�����ʾ���ϣ����ʾ�����ļ���ȷ�����򣬻��������ʾ��
��ʾ������Ϣ

poechant@ubuntu:/user/local/nginx$ ./sbin/nginx -h
���ߣ�
poechant@ubuntu:/user/local/nginx$ ./sbin/nginx -?