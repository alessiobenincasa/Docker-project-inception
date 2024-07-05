# Use Debian Bullseye as the base image
FROM debian:bullseye

# Install necessary packages and update system
RUN apt-get update && apt-get install -y mariadb-server

# Expose the port MySQL listens to
EXPOSE 3306

# Copy configuration files and tools
COPY ./conf/50-server.cnf /etc/mysql/mariadb.conf.d/
COPY ./tools /var/www/

# Initialize the database and remove the setup script
# Note: Bullseye uses 'mariadb' as the service name instead of 'mysql'
RUN service mariadb start \
    && mysql < /var/www/initial_db.sql \
    && rm -f /var/www/initial_db.sql

# Set the command to run the MariaDB server
CMD ["mysqld"]

