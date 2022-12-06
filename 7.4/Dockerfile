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
    && apt install -y php7.4 php7.4-cli \
       php7.4-pgsql php7.4-sqlite3 php7.4-gd \
       php7.4-curl \
       php7.4-imap php7.4-mysql php7.4-mbstring \
       php7.4-xml php7.4-zip php7.4-bcmath php7.4-soap \
       php7.4-intl php7.4-readline \
       php7.4-ldap \
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
