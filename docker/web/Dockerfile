FROM wordpress:php5.6-apache

# PHP設定ファイルのコピー
COPY settings/php.ini /usr/local/etc/php/php.ini

# PHPエラーログファイルの作成
RUN touch /var/log/php_error.log && \
    chown www-data:www-data /var/log/php_error.log

# Apache設定ファイルのコピー
COPY settings/000-default.conf /etc/apache2/sites-available/000-default.conf
COPY settings/default-ssl.conf /etc/apache2/sites-available/default-ssl.conf

# 証明書のコピーとSSLのモジュールの起動
COPY ssl/keys/mycert_crt.pem /opt/mycert_crt.pem
COPY ssl/keys/mycert_key.pem /opt/mycert_key.pem

RUN a2enmod ssl && \
    a2ensite default-ssl

# msmtpモジュールのインストール
RUN apt-get update && \
    apt-get install -y msmtp

COPY settings/msmtprc /etc/msmtprc

RUN chown www-data:www-data /etc/msmtprc && \
    chmod 0600 /etc/msmtprc
