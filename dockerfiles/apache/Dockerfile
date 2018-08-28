FROM ubuntu:18.04

MAINTAINER Ricardo Rivera

RUN apt update && apt -y upgrade && apt -y install apache2 php php-mysql libapache2-mod-php

RUN a2enmod php
RUN a2enmod rewrite

# ADD ./conf/apache-config.conf /etc/apache2/sites-enabled/000-default.conf