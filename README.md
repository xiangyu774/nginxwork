nginx 的安装
下载地址: http://nginx.org/download/nginx-1.10.2.tar.gz      下载时选择 stable verson的  代表稳定版本
安装准备: nginx依赖于pcre库,要先安装pcre          //pcre 语言兼容包 安装Nginx而且用到Rewrite功能，如果没有装pcre，会报缺少PCRE library
yum install pcre pcre-devel                     //安装时候要安装头文件pcre-devel 后面的很多安装都要带-devel
 cd /usr/local/src/
 wget http://nginx.org/download/nginx-1.10.2.tar.gz   // wget文件下载工具
tar zxvf nginx-1.10.2.tar.gz                     //对下载的压缩包进行解压
cd nginx-1.10.2                                                      
./configure --prefix=/usr/local/nginx          //进入解压后的文件  对源码进行编译  其中--prefix是对编译好的文件存放地址进行设置
//如果上一步出现了 error: C compiler cc is not founnd   那么输入yum install gcc gcc-c++ ncurses-devel perl -y   这是c与C++语音的编译器
make && make install                          //对源码进行安装
启动:
cd /ulsr/local/nginx, 看到如下4个目录
./
 ....conf 配置文件 
 ... html 网页文件
 ...logs  日志文件
 ...sbin  主要二进制程序
[root@localhost nginx]# ./sbin/nginx   //执行nginx的启动操作
nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
....
nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
nginx: [emerg] still could not bind()   如果出现这个报错就是不能绑定80端口,80端口已经被占用
//执行进程查看命令  netstat -antp  后面会有进程编号以及  进程名称
之后执行   kill -9 进程编号/进程名   杀掉占用的进程
这里我碰到一个问题有时候进程会不显示编号  可能是nginx重复启动了  把nginx杀掉在执行启动就好了
