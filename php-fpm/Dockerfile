FROM luchaoyi1992/php

MAINTAINER Chaoyi Lu <iyoahcul@gmail.com>


#####################################
# xDebug:
#####################################

ARG INSTALL_XDEBUG=true
RUN if [ ${INSTALL_XDEBUG} = true ]; then \
    # Install the xdebug extension
    pecl install xdebug && \
    docker-php-ext-enable xdebug \
;fi

# Copy xdebug configration for remote debugging
COPY ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

#####################################
# Opcache:
#####################################

RUN docker-php-ext-install opcache && docker-php-ext-enable opcache 


ADD ./xijinfa.ini /usr/local/etc/php/conf.d
ADD ./xijinfa.pool.conf /usr/local/etc/php-fpm.d/

RUN rm -r /var/lib/apt/lists/*

RUN usermod -u 1000 www-data

WORKDIR /var/www

CMD ["php-fpm"]

EXPOSE 9000
