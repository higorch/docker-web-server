FROM higorch/php8.2-fpm-for-wordpress

WORKDIR /var/www/html/app-example-with-php

COPY . .

RUN groupadd -g 1000 appgroup && useradd -u 1000 -ms /bin/bash -g appgroup appuser

RUN usermod -u 1000 appuser && groupmod -g 1000 appgroup && chown -R appuser:appgroup /var/www/html

COPY .docker/php/php.ini /usr/local/etc/php

EXPOSE 9000

USER appuser

CMD ["php-fpm"]