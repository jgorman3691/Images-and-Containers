FROM Debian:latest AS foundation
USER root
ENV DEBIAN_FRONTEND=noninteractive
RUN apt update -y && apt upgrade -y \
    && apt install ssh -y
ONBUILD RUN apt update -y && apt upgrade -y

FROM foundation AS server
WORKDIR /var/www/html
RUN apt install apache2 -y \
    libapache2_mod_php -y \
    && systemctl restart apache2
COPY /var/www/html /var/www/html \
     && /etc/apache2/apache2.conf /etc/apache2/apache2.conf \
     && /etc/apache2/mods-enabled /etc/apache2/mods-enabled \
     && /etc/apache2/sites-enabled /etc/apache2/sites-enabled/
CMD ["apachectl", "-D", "FOREGROUND"]
