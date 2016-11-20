FROM alpine:3.4

ADD usr /usr
RUN install-package nginx

RUN install-package php5-fpm php5-pear php5-phar
#fix missing xml module
RUN sed -i 's/exec $PHP/exec $PHP -d extension=xml.so/g' /usr/bin/pecl


RUN install-package php5-mcrypt php5-openssl
RUN install-package php5-opcache php5-apcu php5-memcache
RUN install-package php5-curl php5-json
RUN install-package php5-gd php5-gettext php5-intl php5-iconv

#install composer
RUN install-package php5-ctype php5-dom git
RUN php -r "readfile('https://getcomposer.org/installer');" | php && mv composer.phar /usr/local/bin/composer

#install pecl extensions
RUN pecl-install redis-2.2.8

#install database drivers
RUN install-package php5-pdo_sqlite php5-pdo_mysql php5-mysqli
