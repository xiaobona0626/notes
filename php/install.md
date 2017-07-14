## centos7 mini 版安装

* 安装依赖包
```
$ yum install wget gcc gcc-c++ libxml2 libxml2-devel openssl openssl-devel bzip2 bzip2-devel libcurl libcurl-devel libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel gmp gmp-devel libmcrypt libmcrypt-devel readline readline-devel libxslt libxslt-devel
```

* php 下载,解压，并进入php目录
```
$ wget http://php.net/distributions/php-7.1.7.tar.gz
$ tar -zxvf php-7.1.7.tar.gz
$ cd php-7.1.7
$ ./configure --prefix=/usr/local/php --with-config-file-path=/etc --enable-fpm --with-fpm-user=nginx  --with-fpm-group=nginx --enable-inline-optimization --disable-debug --disable-rpath --enable-shared  --enable-soap --with-libxml-dir --with-xmlrpc --with-openssl --with-mcrypt --with-mhash --with-pcre-regex --with-sqlite3 --with-zlib --enable-bcmath --with-iconv --with-bz2 --enable-calendar --with-curl --with-cdb --enable-dom --enable-exif --enable-fileinfo --enable-filter --with-pcre-dir --enable-ftp --with-gd --with-openssl-dir --with-jpeg-dir --with-png-dir --with-zlib-dir  --with-freetype-dir --enable-gd-native-ttf --enable-gd-jis-conv --with-gettext --with-gmp --with-mhash --enable-json --enable-mbstring --enable-mbregex --enable-mbregex-backtrack --with-libmbfl --with-onig --enable-pdo --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-zlib-dir --with-pdo-sqlite --with-readline --enable-session --enable-shmop --enable-simplexml --enable-sockets  --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-wddx --with-libxml-dir --with-xsl --enable-zip --enable-mysqlnd-compression-support --with-pear --with-libdir=lib64 --enable-opcache
$ make && make install
```
配置环境变量
```
$ vim /etc/profile
```
在尾部添加

```
export PATH=/usr/local/php/bin:$PATH
```
执行命令使得改动立即生效
```
$ source /etc/profile
```

配置php-fpm  需要在安装软件包目录
```
cp php.ini-production /etc/php.ini
cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf
cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf
cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm
chmod +x /etc/init.d/php-fpm
```
启动php-fpm
```
/etc/init.d/php-fpm start
```

# 编译问题

* 如果 php7编译报错 define struct flock on this system, set --enable-opcache=no
```
$ wget https://downloads.sourceforge.net/project/mcrypt/Libmcrypt/2.5.8/libmcrypt-2.5.8.tar.gz
$ tar -zxvf libmcrypt-2.5.8.tar.gz
$ cd libmcrypt-2.5.8
$ ./configure --prefix=/usr/local/
$ make && make install
$ cd ~

$vim /etc/ld.so.conf
```
/etc/ld.so.conf 尾部新增/usr/local/lib;示例如下
```
include ld.so.conf.d/*.conf
/usr/local/lib
```




