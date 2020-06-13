FROM alpine

RUN apk update && apk add php php7-fpm php7-mcrypt php7-soap tzdata php7-openssl php7-gmp php7-pdo_odbc php7-json php7-dom php7-pdo php7-zip php7-mysqli php7-bcmath php7-gd php7-odbc php7-pdo_mysql php7-gettext php7-xmlreader php7-xmlrpc php7-bz2 php7-iconv php7-curl php7-ctype php7-redis

# 设置时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN sed -i '/listen = 127.0.0.1:9000/c\\listen = 0.0.0.0:9000' /etc/php7/php-fpm.d/www.conf

WORKDIR /opt
# to run php-fpm foreground by force and allow-to-run-as-root
CMD ["/usr/sbin/php-fpm7","-F", "-R"]