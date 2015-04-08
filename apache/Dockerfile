FROM debian:jessie
MAINTAINER Stephane Boulard <lossendae@gmail.com>

RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install apache2 libapache2-mod-php5 vim && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Activate a2enmod
RUN a2enmod rewrite
RUN a2enmod php5

# RUN rm -rf /etc/apache2/sites-enabled/000-default.conf

# RUN /bin/ln -sf ../sites-available/default-ssl /etc/apache2/sites-enabled/001-default-ssl
# RUN /bin/ln -sf ../mods-available/ssl.conf /etc/apache2/mods-enabled/
# RUN /bin/ln -sf ../mods-available/ssl.load /etc/apache2/mods-enabled/

# Set Apache environment variables (can be changed on docker run with -e)
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_SERVERADMIN admin@localhost
ENV APACHE_SERVERNAME localhost
ENV APACHE_SERVERALIAS docker.localhost
ENV APACHE_DOCUMENTROOT /var/www

EXPOSE 80
EXPOSE 443

ADD ./vhost.conf /etc/apache2/sites-available/
RUN ln -s /etc/apache2/sites-available/vhost.conf /etc/apache2/sites-enabled/

VOLUME ["/var/www"]

ADD start.sh /start.sh
RUN chmod 0755 /start.sh
CMD ["bash", "start.sh"]