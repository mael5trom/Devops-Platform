# Purpose: Execute Drupal related tasks for Continuous Integration Services
# Dockerfile instructions: https://docs.docker.com/engine/reference/builder/

FROM ubuntu
MAINTAINER chico.russell@gmail.com  @ https://github.com/mael5trom

LABEL "com.webteks.ci"="Web Teks"
LABEL version="1.0"
LABEL description="This container is a base implementation of tools for \
executing Drupal tasks requested from Jenkins.  It will contain all \
required installations to that only commands are necessary."

RUN apt-get update 
RUN apt-get install -y --no-install-recommends \
		openssh-server \
		default-jdk \
	&& rm -rf /var/lib/apt/lists/*
RUN mkdir /var/run/sshd
RUN useradd -u 1000 jenkins | chpasswd
RUN /usr/sbin/sshd




