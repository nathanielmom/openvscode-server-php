FROM linuxserver/openvscode-server:latest

LABEL maintainer="Nathaniel Mom"

USER root

ARG DEBIAN_FRONTEND=noninteractive
ARG NODE_VERSION=18

RUN apt update \
    && apt dist-upgrade -y \
    && apt-get install -y ca-certificates apt-transport-https software-properties-common zip unzip \
    && add-apt-repository ppa:ondrej/php \
    && apt update \
    && apt install -y php8.2 php8.2-cli \
       php8.2-pgsql php8.2-sqlite3 php8.2-gd \
       php8.2-curl \
       php8.2-imap php8.2-mysql php8.2-mbstring \
       php8.2-xml php8.2-zip php8.2-bcmath php8.2-soap \
       php8.2-intl php8.2-readline \
       php8.2-ldap \
    && php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
    && curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g npm \
    && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" > /etc/apt/sources.list.d/yarn.list \
    && apt-get update \
    && apt-get install -y yarn \
    && apt -y autoremove \
    && apt clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
