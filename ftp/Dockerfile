FROM debian:stretch-slim

ENV COMPOSER_ALLOW_SUPERUSER=1
ENV COMPOSER_NO_INTERACTION=1
ENV COMPOSER_HOME /root/.composer

# Timezone 설정
ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 기본 설치
RUN apt-get update && apt-get install -y nginx php php-fpm php-mcrypt \ 
      php-zip php-mysql php-pgsql php-mbstring php-intl php-soap php-gd \
      php-dev php-curl php-xml php-pgsql curl apt-utils\
      ca-certificates apt-transport-https build-essential --no-install-recommends \
      && rm -rf /var/lib/apt/lists/*

COPY ./default.conf /etc/nginx/sites-available/default

EXPOSE 80

CMD /etc/init.d/php7.0-fpm start && nginx -g "daemon off;"