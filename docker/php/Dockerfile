# Usa una imagen base de PHP
FROM php:8.1-fpm

# Instala dependencias del sistema
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libzip-dev \
    unzip \
    git \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo pdo_pgsql

# Instala Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Establece el directorio de trabajo
WORKDIR /var/www

# Copia el archivo de dependencias y las instala
COPY ../gatewayJuridico/composer.json ../gatewayJuridico/composer.lock ./
RUN composer install --no-autoloader --no-scripts

# Copia el código fuente de la aplicación
COPY . .

# Genera el autoloader de Composer
RUN composer dump-autoload --optimize

# Exponemos el puerto 9000 para PHP-FPM
EXPOSE 8000

# Comando por defecto
CMD ["php-fpm"]
