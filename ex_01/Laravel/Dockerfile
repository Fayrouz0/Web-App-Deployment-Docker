FROM php:8.3.8

RUN apt-get update -y && apt-get install -y openssl zip unzip git
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /app
COPY . .
RUN composer install
RUN php artisan key:generate
RUN touch /app/database/database.sqlite
RUN php artisan migrate

EXPOSE 8000

CMD ["php", "artisan", "serve", "--host=0.0.0.0"]
