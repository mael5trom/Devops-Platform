# Purpose: Execute Drupal related tasks for Continuous Integration Services
# Dockerfile instructions: https://docs.docker.com/engine/reference/builder/

FROM ubuntu
MAINTAINER chico.russell@gmail.com  @ https://github.com/mael5trom
RUN apt-get update 
RUN apt-get install -y --no-install-recommends \
		openssh-server \
		openjdk-6-jdk \
	&& rm -rf /var/lib/apt/lists/*
RUN mkdir /var/run/sshd
RUN useradd -u 1000 jenkins | chpasswd
RUN /usr/sbin/sshd




