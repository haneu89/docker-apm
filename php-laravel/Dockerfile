FROM debian:stretch-slim

# Timezone 설정
ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 기본 설치
RUN apt-get update && apt-get install -y nginx php php-fpm php-mcrypt \ 
      php-zip php-mysql php-pgsql php-mbstring php-intl php-soap php-gd \
      php-dev php-curl php-xml curl wget \
      ca-certificates apt-transport-https build-essential --no-install-recommends

# Composer 설치
RUN curl -sS https://getcomposer.org/installer | \
    php -- --install-dir=/usr/bin/ --filename=composer

COPY ./default2.conf /etc/nginx/sites-available/default
EXPOSE 80

CMD /etc/init.d/php7.0-fpm start && nginx -g "daemon off;"