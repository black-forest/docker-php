FROM php:7.1.25-fpm-alpine

RUN apk add \
        git \
        openssh \
        openssh-client \
        sudo

RUN apk add \
        $PHPIZE_DEPS \
        aspell-dev \
        aspell-libs \
        bzip2-dev \
        c-client \
        freetds-dev \
        freetype-dev \
        geoip-dev \
        gettext-dev \
        gmp-dev \
        icu-dev \
        icu-libs \
        imagemagick-dev \
        imap-dev \
        libcrypto1.0 \
        libevent-dev \
        libgcc \
        libintl \
        libjpeg-turbo-dev \
        libldap \
        libltdl \
        libmcrypt-dev \
        libmemcached-dev \
        libpng-dev \
        librdkafka-dev \
        libssl1.0 \
        libstdc++ \
        libxml2-dev \
        libxslt-dev \
        openldap-dev \
        pcre-dev \
        postgresql-dev \
        rabbitmq-c-dev \
        tidyhtml-dev \
        tidyhtml-libs \
        yaml-dev \
        zlib

#RUN docker-php-source extract \
#    && cd /usr/src/php \
#    && sed -i 's/buffio.h/tidybuffio.h/' ext/tidy/*.c

RUN docker-php-ext-install \
        bcmath \
        bz2 \
        calendar \
        dba \
        exif \
        gd \
        gettext \
        gmp \
        imap \
        intl \
        ldap \
        mysqli \
        opcache \
        pcntl \
        pdo_dblib \
        pdo_mysql \
        pdo_pgsql \
        pgsql \
        pspell \
        shmop \
        soap \
        sockets \
        sysvmsg \
        sysvsem \
        sysvshm \
        tidy \
        wddx \
        xmlrpc \
        xsl \
        zip

RUN pecl install \
        amqp \
        apcu \
        event \
        grpc \
        imagick \
        mcrypt-1.0.0 \
        memcached \
        mongodb \
        oauth \
        rdkafka \
        redis\
        uuid \
        xdebug \
        yaml

RUN docker-php-ext-enable \
        amqp \
        apcu \
        event \
        grpc \
        imagick \
        mcrypt \
        memcached \
        mongodb \
        oauth \
        rdkafka \
        redis \
        uuid \
        xdebug \
        yaml

#RUN apk add \
#        pkgconf-dev

#RUN pecl install \
#        geoip \
#        uploadprogress

#RUN docker-php-ext-enable \
#        geoip \
#        uploadprogress

RUN  mv /usr/local/etc/php/conf.d/docker-php-ext-event.ini /usr/local/etc/php/conf.d/z-docker-php-ext-event.ini

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === '93b54496392c062774670ac18b134c3b3a95e5a5e5c8f1a9f115f203b75bf9a129d5daa8ba6a13e2cc8a1da0806388a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

RUN rm -rf \
        /usr/include/php \
        /usr/lib/php/build \
        /tmp/* \
        /root/.composer \
        /var/cache/apk/* \
    && docker-php-source delete

ARG DEFAULT_USER=php

RUN adduser $DEFAULT_USER -s /bin/bash -h /home/$DEFAULT_USER -D \
    && echo $DEFAULT_USER" ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/$DEFAULT_USER \
    && chmod 0440 /etc/sudoers.d/$DEFAULT_USER

USER $DEFAULT_USER

WORKDIR /home/$DEFAULT_USER
