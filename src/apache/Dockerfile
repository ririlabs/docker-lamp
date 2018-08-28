FROM ubuntu:18.04

LABEL author="Ricardo Rivera"
LABEL website="https://www.softwaredefinedengineer.com"
LABEL version="0.1"
LABEL description="Apache server with PHP."

RUN apt-get update && \
    apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install apache2 php php-mysql libapache2-mod-php

RUN a2enmod rewrite