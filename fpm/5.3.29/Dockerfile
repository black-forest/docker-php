FROM php:5.3.29-cli-alpine

# Install the shell
RUN apk add bash \
            zsh

# Install bcmath
RUN docker-php-ext-install bcmath

# Install bz2
RUN apk add bzip2-dev \
    && docker-php-ext-install bz2

# Install calendar
RUN docker-php-ext-install calendar

# Install dba
RUN docker-php-ext-install dba

# Install exif
RUN docker-php-ext-install exif

# Install gd
RUN apk add freetype-dev \
            libjpeg-turbo-dev \
            libpng-dev \
    && docker-php-ext-install gd

# Install gettext
RUN apk add gettext-dev \
            libintl \
    && docker-php-ext-install gettext

# Install gmp
RUN apk add gmp-dev \
    && docker-php-ext-install gmp

# Install intl
RUN apk add icu-dev \
            icu-libs \
            libgcc \
            libstdc++ \
    && docker-php-ext-install intl

# Install ldap
RUN apk add libldap \
            openldap-dev \
    && docker-php-ext-install ldap

# Install mysqli
RUN docker-php-ext-install mysqli

# Install pcntl
RUN docker-php-ext-install pcntl

# Install pdo_dblib
RUN apk add freetds-dev \
    && docker-php-ext-install pdo_dblib

# Install pdo_mysql
RUN docker-php-ext-install pdo_mysql

# Install pdo_pgsql
RUN apk add postgresql-dev \
    && docker-php-ext-install pdo_pgsql

# Install pgsql
RUN docker-php-ext-install pgsql

# Install pspell
RUN apk add aspell-libs \
            aspell-dev \
    && docker-php-ext-install pspell

# Install shmop
RUN docker-php-ext-install shmop

# Install soap
RUN apk add libxml2-dev \
            zlib \
    && docker-php-ext-install soap

# Install sockets
RUN docker-php-ext-install sockets

# Install sysvmsg
RUN docker-php-ext-install sysvmsg

# Install sysvsem
RUN docker-php-ext-install sysvsem

# Install sysvshm
RUN docker-php-ext-install sysvshm

# Install tidy
RUN apk add tidyhtml-dev \
            tidyhtml-libs \
    && docker-php-ext-install tidy

# Install wddx
RUN docker-php-ext-install wddx

# Install xmlrpc
RUN apk add libxml2-dev \
            zlib \
    && docker-php-ext-install xmlrpc

# Install xsl
RUN apk add libxml2-dev \
            libxslt-dev \
            zlib \
    && docker-php-ext-install xsl

# Install zip
RUN apk add zlib \
    && docker-php-ext-install zip

# Install imagick
RUN apk add imagemagick-dev \
            $PHPIZE_DEPS \
    && pecl install imagick \
    && docker-php-ext-enable imagick

# Install xdebug
RUN apk add $PHPIZE_DEPS \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug
