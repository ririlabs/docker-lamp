FROM mysql:5.7

# Metadata information
LABEL author="Ricardo Rivera"
LABEL author_website="https://www.ririlabs.com"
LABEL description="Dockerized MySQL server"

# Update system and install necessary packages
RUN apt-get update && \
    apt-get -y upgrade

# Switch to non-priviledged user to run our application
USER mysql

# Export volumes as appuser
VOLUME /var/lib/mysql/
VOLUME /var/log/mysql/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mysqld"]