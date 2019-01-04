FROM debian:stretch-slim

ENV COMPOSER_ALLOW_SUPERUSER=1
ENV COMPOSER_NO_INTERACTION=1
ENV COMPOSER_HOME /root/.composer

# Timezone 설정
ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 기본 설치
RUN apt-get update \
      && apt-get install -y --no-install-recommends curl wget gnupg cron apt-utils ca-certificates apt-transport-https build-essential \
      && wget -q https://packages.sury.org/php/apt.gpg -O- | apt-key add - \
      && echo "deb https://packages.sury.org/php/ stretch main" | tee /etc/apt/sources.list.d/php.list \
      && apt-get update \
      && apt-get install -y --no-install-recommends nginx php7.2 php7.2-fpm \ 
      php7.2-zip php7.2-mysql php7.2-pgsql php7.2-mbstring php7.2-intl php7.2-soap php7.2-gd \
      php7.2-dev php7.2-curl php7.2-xml php7.2-pgsql \
      && rm -rf /var/lib/apt/lists/*

# Composer 설치
RUN curl -sS https://getcomposer.org/installer | \
    php -- --install-dir=/usr/bin/ --filename=composer
# prestissimo

COPY ./default2.conf /etc/nginx/sites-available/default

RUN composer global require hirak/prestissimo

EXPOSE 80

CMD cron && /etc/init.d/php7.0-fpm start && nginx -g "daemon off;"