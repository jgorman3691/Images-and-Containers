#syntax=Dockerfile
FROM foundation AS server
RUN apt install apache2 -y \
    libapache2_mod_php -y \
    && systemctl restart apache2
WORKDIR /var/www/html
COPY /var/www/html /var/www/html \
     && /etc/apache2/apache2.conf /etc/apache2/apache2.conf \
     && /etc/apache2/mods-enabled/ /etc/apache2/mods-enabled/ \
     && /etc/apache2/sites-enabled/ /etc/apache2/sites-enabled/
EXPOSE 80
CMD ["apachectl", "-D", "FOREGROUND"]
