FROM php:7.4-fpm

RUN apt-get update && \
    apt-get -y install wget \
        gnupg2 && \
    apt-key update && \
    apt-get update && \
    apt-get -y install \
            g++ \
            git \
            curl \
            imagemagick \
            libcurl3-dev \
            libicu-dev \
            libfreetype6-dev \
            libjpeg-dev \
            libjpeg62-turbo-dev \
            libonig-dev \
            libmagickwand-dev \
            libpq-dev \
            libpng-dev \
            libxml2-dev \
            libzip-dev \
            zlib1g-dev \
            default-mysql-client \
            openssh-client \
            nano \
            unzip \
            libjpeg-dev \
            libfreetype6-dev \
            libcurl4-openssl-dev \
            libssl-dev \
        --no-install-recommends && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


RUN docker-php-ext-install zip \
    intl \
    pdo_pgsql

RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install gd
# Environment settings
#ENV COMPOSER_ALLOW_SUPERUSER=1 \
#    PHP_USER_ID=33 \
#    PHP_ENABLE_XDEBUG=0 \
#    PATH=/app:/app/vendor/bin:/root/.composer/vendor/bin:$PATH

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- \
        --filename=composer.phar \
        --install-dir=/usr/local/bin


#COPY --chown=1000:1000 ./app /app

#RUN chown -R 1000:1000 /app/bin /app/config /app/public /app/src /app/templates/ /app/tests /app/.env /app/.env.test

# Application environment
WORKDIR /app