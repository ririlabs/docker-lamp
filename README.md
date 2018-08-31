# Docker LAMP Server
This is a basic Linux/Apache/MySQL/PHP server using Docker Compose. The server stack consists of the following:
* Ubuntu 18.04 
* Apache 2.4
* MySQL 5.7
* PHP 7.2

## Configuration
All configuration for the lamp stack should be done under the <code>config</code> folder. 

### Apache Configuration
By default, the server uses HTTPS. You will need to modify this if you do not plan on serving HTTPS traffic. See the `optional` section for more information.

#### Environment Variables
The `config/apache/vhost.conf` file has several environment variables that require proper values for the server to run correctly.

##### APACHE_SERVER_NAME
This is the server name for your web server. Usually in the form of `yourdomain.com`.

##### APACHE_SERVER_ALIAS
This is the list of aliases for your web server. An example would be `www.yourdomain.com`.

##### APACHE_SSL_VERIFY_CLIENT
Used for client certificate authentication (useful for reverse proxies). Sets the Certificate verification level for the Client Authentication.

##### APACHE_SSL_VERIFY_DEPTH
Used for client certificate authentication (useful for reverse proxies). Sets how deeply mod_ssl should verify before deciding that the clients don't have a valid certificate.

#### Secrets
The `config/apache/secrets` folder contains files where you can copy your certificates into. These are required if you wish to use HTTPS, which is turned on by default.

##### ca.cert
Used only with the `SSLVerifyClient` option. The public SSL cert for your Certificate Authority.

##### vhost.cert
Used only for `HTTPS` traffic. The public SSL cert for your domain.

##### vhost.key
Used only for `HTTPS` traffic. The private SSL key for your domain.

#### Optional
You may choose to modify the `src/apache/vhost.conf` which would allow you to turn off HTTPS, add more virtual hosts, and change other parameters in the Apache configuration. Note that modifying this file will require a rebuild of the Apache image for it to take effect.

### MySQL Configuration

#### Environment Variables
The `config/mysql/mysql.env` file has several environment variables that in most cases can be left at their default values.

##### MYSQL_ROOT_PASSWORD_FILE
Path to the root password secret file.

##### MYSQL_DATABASE_FILE
Path to the database name secret file.

##### MYSQL_USER_FILE
Path to the database username secret file.

##### MYSQL_PASSWORD_FILE
Path to the database user password secret file.

##### MYSQL_ALLOW_EMPTY_PASSWORD
Set to `yes` to allow an empty password for the root account. Recommend leaving blank.

##### MYSQL_RANDOM_ROOT_PASSWORD
Set to `yes` to generate a random password for the root account. Recommend leaving blank.

##### MYSQL_ONETIME_PASSWORD
Set to `yes` to generate a one-time password for the root account. Recommend leaving blank.

#### Secrets
The `config/mysql/secrets` folder contains files where you can specify sensitive account information for mysql such as root password, database name, database user, and database password.

##### mysql-root
The root mysql password. Set during initial run. This is required unless MYSQL_ALLOW_EMPTY_PASSWORD, MYSQL_RANDOM_ROOT_PASSWORD, or MYSQL_ONETIME_PASSWORD is set.

##### mysql-db-name
The database name to use for the database. Set during initial run.

##### mysql-db-user
The database user to use for the database. Set during initial run.

##### mysql-db-pass
The database password to use for the database. Set during initial run.

## Installing as a service on Ubuntu
1. Clone the repository into `/opt/dockerapps/docker-lamp`.
2. Properly configure the options under the `config` folder.
3. Copy `systemd/docker-lamp.service` unit file into `/lib/systemd/system/docker-lamp.service`.
4. Optionally, you may modify the docker-lamp.service systemd unit file to match your preferences or work with other Linux distributions.
5. Use `systemctl start docker-lamp` to start the lamp server.
