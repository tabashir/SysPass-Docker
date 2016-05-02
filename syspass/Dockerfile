FROM nuxsmin/apache-php
MAINTAINER nuxsmin nuxsmin@syspass.org
LABEL from=github version=stable-master

# Usage:
# docker run -d --name=syspass nuxsmin/syspass
# webroot: /var/www/html/
# Apache2 config: /etc/apache2/

RUN apt-get update \
	&& DEBIAN_FRONTEND=noninteractive apt-get -y install \
	php5-curl \
	php5-gd \
	php5-json \
	php5-ldap \
	php5-mcrypt \
	wget \
	unzip \
	&& apt-get clean \
	&& rm -r /var/lib/apt/lists/*

WORKDIR /var/www/html

LABEL version=1.2.0.11

RUN wget https://github.com/nuxsmin/sysPass/archive/master.zip \
	&& unzip master.zip \
	&& mv sysPass-master sysPass \
	&& chown www-data -R sysPass/ \
	&& chmod 750 sysPass/config \
	&& mkdir sysPass/backup \
	&& chmod 750 sysPass/backup

COPY 000-default.conf /etc/apache2/sites-available/
