FROM php:7.4-cli
RUN apt-get -yqq update && apt-get -yqq install \
  build-essential \
  g++ \
  gifsicle \
  git \
  gnupg2 \
  graphviz \
  jpegoptim \
  libbz2-dev \
  libc-client2007e-dev \
  libfreetype6-dev \
  libgmp-dev \
  libicu-dev \
  libjpeg62-turbo-dev \
  libkrb5-dev \
  libmagickwand-dev \
  libmcrypt-dev \
  libonig-dev \
  libpq-dev \
  libpng-dev \
  libssl-dev \
  libxml2-dev \
  libzip-dev \
  nodejs \
  openssl \
  unzip \
  zip \
  zlib1g-dev \
  libwebp-dev

RUN pecl install \
  imagick \
  mcrypt-1.0.4 \
  redis

RUN docker-php-ext-enable \
  imagick \
  mcrypt \
  redis

RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp
RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl
RUN docker-php-ext-configure intl

RUN docker-php-ext-install \
  exif \
  gd \
  gmp \
  imap \
  intl \
  mbstring \
  pdo \
  pdo_mysql \
  pcntl \
  soap \
  zip

# Install composer
COPY --from=composer:2 /usr/bin/composer /usr/local/bin/composer
