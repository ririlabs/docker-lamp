FROM ubuntu:18.04

# Metadata information
LABEL author="Ricardo Rivera"
LABEL website="https://www.softwaredefinedengineer.com"
LABEL version="0.1"
LABEL description="Apache server with PHP."

# Our default user that will run applications on the container
RUN groupadd -g 999 appuser && \
    useradd -r -u 999 -g appuser appuser

# Update system and install necessary packages
RUN apt-get update && \
    apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install apache2 php php-mysql libapache2-mod-php

# Set default ENV vars
ENV APACHE_LISTEN_HTTP=8080
ENV APACHE_LISTEN_HTTPS=8443

# Configure Apache. Disable default site, update permissions, and use custom listen ports.
RUN a2dissite 000-default.conf && \
    chown -R appuser:appuser /var/log/apache2 && \
    chown appuser:appuser /var/run/apache2 && \
    sed -i 's/\<Listen 80\>/Listen ${APACHE_LISTEN_HTTP}/' /etc/apache2/ports.conf && \
    sed -i 's/\<Listen 443\>/Listen ${APACHE_LISTEN_HTTPS}/' /etc/apache2/ports.conf

# Export volumes as root
VOLUME /var/www/
VOLUME /etc/apache2/

# Switch to non-priviledged user to run our application
USER appuser

# Export volumes as appuser
VOLUME /var/log/apache2

CMD ["/usr/sbin/apache2ctl", "-DFOREGROUND"]