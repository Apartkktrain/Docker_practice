FROM ubuntu:20.04
LABEL version="1.0"
LABEL description="ubuntu 20.04+apache"

ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2

RUN apt-get update && \
    apt-get install -y apache2

EXPOSE 80
CMD ["apachectl", "-D", "FOREGROUND"]

RUN apt-get install -y php libapache2-mod-php

RUN apt-get install -y php-fpm php-common php-mbstring php-xmlrpc php-gd php-xml php-mysql php-cli php-zip php-curl php-imagick
RUN a2enmod rewrite
RUN service apache2 restart

RUN echo "<?php phpinfo(); ?>" >> /var/www/html/info.php