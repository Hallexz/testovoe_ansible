
FROM php:7.4-fpm

# Установка необходимых расширений PHP
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo_mysql

# Установка Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Копирование исходного кода приложения
COPY ./www /var/www/html

# Установка прав на файлы
RUN chown -R www-data:www-data /var/www/html

# Установка рабочей директории
WORKDIR /var/www/html

# Запуск PHP-FPM
CMD ["php-fpm"]
