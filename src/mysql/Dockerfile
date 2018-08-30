FROM mysql:8

# Metadata information
LABEL author="Ricardo Rivera"
LABEL author_website="https://www.softwaredefinedengineer.com"
LABEL description="Dockerized MySQL server"

USER mysql

VOLUME /var/lib/mysql/
VOLUME /var/log/mysql/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mysqld"]