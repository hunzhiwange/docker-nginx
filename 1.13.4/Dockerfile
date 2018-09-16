FROM centos:latest
RUN set -x \
        && cd /home \
        && yum install -y wget \
        && wget http://nginx.org/download/nginx-1.13.4.tar.gz \
        && tar zxvf nginx-1.13.4.tar.gz \
        && cd nginx-1.13.4 \
        && yum install -y gcc openssl-devel pcre-devel zlib-devel make sudo \
        && ./configure  --prefix=/usr/local/nginx  --sbin-path=/usr/local/nginx/sbin/nginx --conf-path=/usr/local/nginx/conf/nginx.conf --error-log-path=/var/log/nginx/error.log  --http-log-path=/var/log/nginx/access.log  --pid-path=/var/run/nginx/nginx.pid --lock-path=/var/lock/nginx.lock  --user=www --group=www --with-http_ssl_module --with-http_stub_status_module --with-http_gzip_static_module --http-client-body-temp-path=/var/tmp/nginx/client/ --http-proxy-temp-path=/var/tmp/nginx/proxy/ --http-fastcgi-temp-path=/var/tmp/nginx/fcgi/ --http-uwsgi-temp-path=/var/tmp/nginx/uwsgi --http-scgi-temp-path=/var/tmp/nginx/scgi --with-pcre \
        && make \
        && make install \
        && /usr/local/nginx/sbin/nginx -v \
        && groupadd www \
        && useradd www -g www \
        && yum remove -y gcc openssl-devel pcre-devel zlib-devel make sudo\
        && yum clean all \
        && rm -rf /tmp/* \
        && rm -rf /home/nginx-1.13.4 \
        && mkdir -p /var/tmp/nginx/client \
        && mkdir -p /usr/local/nginx/logs
ENTRYPOINT ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
