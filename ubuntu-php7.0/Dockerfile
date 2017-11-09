FROM ubuntu:16.04

MAINTAINER jinhyung <mail@jinhyung.kim>

# 기본 설치
RUN apt-get update && apt-get install -y \
  apache2 \
  php \
  libapache2-mod-php \
  php-mcrypt \
  php-zip \
  php-mysql \
  php-mbstring \
  php-gd \
  php-dev \
  php-curl \
  php-xml \
  curl \
  wget \
  build-essential \
  --no-install-recommends

RUN a2enmod rewrite
RUN sed -i ':a;N;$!ba;s/AllowOverride None/AllowOverride All/3' /etc/apache2/apache2.conf

EXPOSE 80

CMD apachectl -DFOREGROUND