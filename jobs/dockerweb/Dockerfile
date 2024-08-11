# Usa una versión más reciente de PHP con Apache
FROM php:8.1-apache
LABEL maintainer="Jaivic"

# Habilita el módulo de reescritura de Apache
RUN a2enmod rewrite

# Actualiza los repositorios e instala las dependencias necesarias
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libicu-dev \
    libxml2-dev \
    libpq-dev \
    vim \
    --no-install-recommends \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Copia el contenido del directorio actual al directorio de trabajo del contenedor
COPY . /var/www/html/
WORKDIR /var/www/html/


