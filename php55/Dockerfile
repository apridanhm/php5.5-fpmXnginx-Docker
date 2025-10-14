FROM php:5.5.38-fpm

# Tulis ulang sources.list dan tandai trusted (bypass GPG expiry)
RUN printf 'deb [trusted=yes] http://archive.debian.org/debian jessie main contrib non-free\n' > /etc/apt/sources.list \
 && echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99no-check-valid \
 && apt-get -o Acquire::AllowInsecureRepositories=true update

# Paket dev yang dibutuhkan buat ekstensi lawas
RUN apt-get install -y --no-install-recommends \
      libjpeg62-turbo-dev libpng-dev libfreetype6-dev \
      zlib1g-dev libicu-dev libxml2-dev libmcrypt-dev \
      autoconf g++ make \
 && rm -rf /var/lib/apt/lists/*

# Build ekstensi PHP 5.5
RUN docker-php-ext-configure gd --with-freetype-dir=/usr --with-jpeg-dir=/usr \
 && docker-php-ext-install -j"$(nproc)" gd mysql mysqli pdo_mysql mbstring mcrypt opcache

EXPOSE 9000

