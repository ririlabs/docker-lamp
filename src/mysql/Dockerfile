FROM mysql:8

# Metadata information
LABEL author="Ricardo Rivera"
LABEL website="https://www.softwaredefinedengineer.com"
LABEL version="0.1"
LABEL description="MySQL Server."

VOLUME /var/log/mysql/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mysqld"]