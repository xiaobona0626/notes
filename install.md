yum install gcc-c++
yum install -y pcre pcre-devel
yum install -y zlib zlib-devel
yum install -y openssl openssl-devel
wget http://nginx.org/download/nginx-1.15.6.tar.gz
tar -zxvf nginx-1.15.6
cd nginx-1.15.6
./configure --prefix=/usr/local/nginx 
make
make install

vi /etc/rc.local
/usr/local/nginx/sbin/nginx
chmod 755 rc.local
