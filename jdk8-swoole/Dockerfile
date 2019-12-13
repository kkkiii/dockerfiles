FROM fabletang/jre8-ubuntu
MAINTAINER hom liu <2624886248@qq.com>
# add php 7.2 cli surport

RUN apt-get update
RUN apt-get install -y apt-utils
RUN apt-get install -y aptitude

RUN aptitude install vim -y && \
    aptitude install openssl -y && \
    aptitude install libssl-dev -y && \
    aptitude install wget -y && \
    aptitude install libc6 -y && \
    aptitude install libargon2-0 -y && \
    aptitude install libsodium23 -y && \
    aptitude install libssl1.1 -y && \
    aptitude install libcurl4 -y && \
    aptitude install libzip4 -y && \
    aptitude install libsodium23 -y

RUN apt-get install -y --no-install-recommends gnupg \
    && echo "deb http://ppa.launchpad.net/ondrej/php/ubuntu bionic main" > /etc/apt/sources.list.d/ondrej-php.list \
    && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4F4EA0AAE5267A6C \
    && apt-get update \
    && apt-get -y --no-install-recommends install curl ca-certificates unzip \
    && apt-get install -y php7.2-common php7.2-cli php7.2-curl php-apcu php-apcu-bc \
        php7.2-json php7.2-mbstring php7.2-opcache php7.2-readline php7.2-xml php7.2-zip
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer global require hirak/prestissimo \
    && composer clear-cache \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/* ~/.composer



RUN cd /tmp && wget https://pecl.php.net/get/swoole-4.2.9.tgz && \
    tar zxvf swoole-4.2.9.tgz && \
    cd swoole-4.2.9  && \
    phpize  && \
    ./configure  --enable-openssl && \
    make && make install

RUN touch /usr/local/etc/php/conf.d/swoole.ini && \
    echo 'extension=swoole.so' > /usr/local/etc/php/conf.d/swoole.ini

RUN mkdir -p /app/data

WORKDIR /app

COPY ./app /app

EXPOSE 8101
CMD ["/usr/local/bin/php", "/app/index.php"]

RUN java -version