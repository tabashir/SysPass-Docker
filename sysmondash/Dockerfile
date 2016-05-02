FROM nuxsmin/apache-php
MAINTAINER nuxsmin nuxsmin@cygnux.org
LABEL from=github version=stable-master

# Usage:
# docker run -d --name=sysmondash nuxsmin/sysmondash
# webroot: /var/www/html/
# Apache2 config: /etc/apache2/

RUN apt-get update \
	&& DEBIAN_FRONTEND=noninteractive apt-get -y install \
	php5-curl \
	php5-json \
	wget \
	unzip \
	&& apt-get clean \
	&& rm -r /var/lib/apt/lists/*

WORKDIR /var/www/html

LABEL version=1.0.2016050201

RUN wget https://github.com/nuxsmin/sysMonDash/archive/master.zip \
	&& unzip master.zip \
	&& mv sysMonDash-master sysMonDash \
	&& chown www-data -R sysMonDash/ \
	&& mkdir /etc/sysMonDash \
	&& chown www-data /etc/sysMonDash/ \
	&& chmod 750 /etc/sysMonDash/

COPY 000-default.conf /etc/apache2/sites-available/
