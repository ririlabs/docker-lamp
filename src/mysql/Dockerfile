FROM mysql:8

# Metadata information
LABEL author="Ricardo Rivera"
LABEL author_website="https://www.softwaredefinedengineer.com"
LABEL description="Dockerized MySQL server"

VOLUME /var/log/mysql/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mysqld"]