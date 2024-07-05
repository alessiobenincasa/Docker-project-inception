# Start with the Debian Bullseye base image
FROM debian:bullseye

# Install necessary packages
RUN apt-get update && apt-get -y install php7.4 php7.4-mysqli php7.4-fpm wget sendmail \
    && rm -rf /var/lib/apt/lists/*

# Expose the port PHP-FPM is running on
EXPOSE 9000

# Copy configuration files and scripts into the container
COPY ./conf/www.conf /etc/php/7.4/fpm/pool.d/
COPY ./tools /var/www/

# Ensure the startup script is executable
RUN chmod +x /var/www/wordpress_start.sh

# Set the container to run the startup script by default
ENTRYPOINT ["/var/www/wordpress_start.sh"]

# Set the command to run PHP-FPM without daemonizing
CMD ["/usr/sbin/php-fpm7.4", "--nodaemonize"]

