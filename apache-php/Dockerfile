FROM debian:jessie
MAINTAINER nuxsmin nuxsmin@syspass.org

# Usage:
# docker run -d --name=apache-php -p 8080:80 -p 8443:443 nuxsmin/apache-php
# webroot: /var/www/html/
# Apache2 config: /etc/apache2/

RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

RUN apt-get update && \
	apt-get -y install \
	apache2 \
	libapache2-mod-php5 \
	php5 \
	php5-curl \
	php5-mysqlnd \
	&& apt-get clean \
	&& rm -r /var/lib/apt/lists/*

WORKDIR /var/www/html

COPY entrypoint.sh /usr/local/sbin/

RUN chmod 755 /usr/local/sbin/entrypoint.sh

EXPOSE 80 443

ENTRYPOINT ["/usr/local/sbin/entrypoint.sh"]


