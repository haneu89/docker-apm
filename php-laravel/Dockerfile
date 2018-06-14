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

RUN apt-get install -y vim
COPY ./default2.conf /etc/nginx/sites-available/default
EXPOSE 80

CMD /etc/init.d/php7.0-fpm start && nginx -g "daemon off;"