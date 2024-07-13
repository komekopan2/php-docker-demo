# イメージを取得
FROM php:8.1.18-fpm
# 独自のphp.iniファイル(PHPの設定ファイル)を 
# コンテナ内の/usr/local/etc/php/ディレクトリにコピー
COPY php.ini /usr/local/etc/php/

  # composer environment
ENV  COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

# composer
COPY --from=composer:2.6.5 /usr/bin/composer /usr/bin/composer

# パッケージやPHPの拡張モジュールをインストールするコマンド　を実行
RUN apt-get update && apt-get install -y \
	git \
	curl \
	zip \
	unzip \
    && docker-php-ext-install pdo_mysql

# 作業ディレクトリを/var/wwwに設定
WORKDIR /var/www

