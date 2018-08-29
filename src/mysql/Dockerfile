FROM mysql:8

# Metadata information
LABEL author="Ricardo Rivera"
LABEL website="https://www.softwaredefinedengineer.com"
LABEL version="0.1"
LABEL description="MySQL Server."

# Our default user that will run applications on the container
RUN groupadd -g 999 appuser && \
    useradd -r -u 999 -g appuser appuser

# Configure Mysql and adjust permissions.
RUN chown -R appuser:appuser /var/lib/mysql && \
    chown -R appuser:appuser /var/log/mysql

# Switch to non-priviledged user to run our application
USER appuser

# Export volumes as appuser
VOLUME /var/lib/mysql/
VOLUME /var/log/mysql/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mysqld"]