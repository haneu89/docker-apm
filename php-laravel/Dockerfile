FROM debian:stretch-slim

ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

MAINTAINER jinhyung <mail@jinhyung.kim>

# 기본 설치
RUN apt-get update && apt-get install -y \
  nginx \
  php \
  php-fpm \
  php-mcrypt \
  php-zip \
  php-mysql \
  php-pgsql \
  php-mbstring \
  php-intl \
  php-soap \
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