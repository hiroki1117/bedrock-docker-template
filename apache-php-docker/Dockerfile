FROM php:7.4.33-apache

RUN apt-get -y update \
  && apt-get -y upgrade \
  && apt-get install -y wget

# mysql_connectionエラー対策
RUN docker-php-ext-install mysqli \
  && service apache2 restart

# ドキュメントルートを変更する
ENV APACHE_DOCUMENT_ROOT='/var/www/web/'
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf

# コンテナログイン時のパスを最後に指定
WORKDIR  /var/www/web
