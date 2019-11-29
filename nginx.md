# Nginx install step
```
mkdir /usr/local/nginx
cd /usr/local/nginx/
wget http://nginx.org/download/nginx-1.12.2.tar.gz
wget https://github.com/arut/nginx-rtmp-module/archive/master.zip
tar -zxvf nginx-1.12.2.tar.gz
unzip master.zip
yum install gcc-c
yum install pcre pcre-devel
yum install zlib zlib-devel
yum install openssl openssl--devel
cd nginx-1.12.2/
yum search openssl*
yum install xmlsec1-openssl-devel.x86_64
./configure --add-module=/usr/local/nginx/nginx-rtmp-module-master
ll
cd ..
make
make install




```
