FROM php:fpm-alpine
RUN docker-php-ext-install pdo_mysql

COPY ./symfony /var/www/project
WORKDIR /var/www/project

RUN    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN    php -r "if (hash_file('sha384', 'composer-setup.php') === 'c5b9b6d368201a9db6f74e2611495f369991b72d9c8cbd3ffbc63edff210eb73d46ffbfce88669ad33695ef77dc76976') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN    php composer-setup.php --filename=composer
RUN    php -r "unlink('composer-setup.php');"
RUN   ./composer install --no-dev

CMD php-fpm;
EXPOSE 9001

