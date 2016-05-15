# Purpose: Execute Drupal related tasks for Continuous Integration Services
# Dockerfile instructions: https://docs.docker.com/engine/reference/builder/

FROM ubuntu:14.04
MAINTAINER chico.russell@gmail.com  @ https://github.com/mael5trom

LABEL "com.webteks.ci"="Web Teks"
LABEL version="1.0"
LABEL description="This container is a base implementation of tools for \
executing Drupal tasks requested from Jenkins.  It will contain all \
required packages."

RUN apt-get update 
RUN apt-get install -y --no-install-recommends \
		openssh-server \
		default-jdk \
		curl bzip2 \
		libgmp10 libpng12-0 libltdl7 libmcrypt4 libpq5 libicu52 libxslt1.1 \
		imagemagick libmagickwand-6.q16-2 libmagickcore-6.q16-2 \
  		mysql-client postgresql-client-common sqlite \
  		php5-cli php5-intl php5-curl php5-mysql php5-json \
  		xfonts-base xfonts-75dpi && \
  		apt-get -y clean && \
  		apt-get -y autoclean && \
	  	apt-get -y autoremove && \
  		rm -rf /var/lib/apt/* && rm -rf && rm -rf /var/lib/cache/* && rm -rf /var/lib/log/* && rm -rf /tmp/*
		&& rm -rf /var/lib/apt/lists/*
RUN \
  cd /tmp && curl -O 'http://download.gna.org/wkhtmltopdf/0.12/0.12.2/wkhtmltox-0.12.2_linux-jessie-amd64.deb' && \
  dpkg -i /tmp/wkhtmltox-0.12.2_linux-jessie-amd64.deb && \
  mkdir -p /srv/bin && ln -s /usr/local/bin/wkhtmltopdf /srv/bin/wkhtmltopdf && \
  cd /srv/bin && \
  curl -fsSL "https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2" | tar -xjv && \
  mv phantomjs-2.1.1-linux-x86_64/bin/phantomjs /srv/bin/phantomjs && \
  rm -rf phantomjs-2.1.1-linux-x86_64 && rm -f phantomjs-2.1.1-linux-x86_64.tar.bz2 && \
  chmod +x /srv/bin/phantomjs && \
  apt-get -y clean && \
  apt-get -y autoclean && \
  apt-get -y autoremove && \
  rm -rf /var/lib/apt/* && rm -rf && rm -rf /var/lib/cache/* && rm -rf /var/lib/log/* && rm -rf /tmp/*
	
RUN mkdir /var/run/sshd
RUN useradd -u 1000 jenkins | chpasswd
RUN /usr/sbin/sshd




