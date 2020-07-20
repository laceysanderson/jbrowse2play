FROM centos/httpd-24-centos7

MAINTAINER Lacey-Anne Sanderson <laceyannesanderson@gmail.com>

USER root

WORKDIR /var/www/html/

RUN curl -sL https://rpm.nodesource.com/setup_10.x | bash - \
  && yum install nodejs -y \
  && node --version && npm --version

RUN npm install -g @gmod/jbrowse-cli \
  && jbrowse --version

RUN jbrowse create jbrowse2

WORKDIR /var/www/html/jbrowse2

EXPOSE 80 5432
