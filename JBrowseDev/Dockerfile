FROM centos/httpd-24-centos7

MAINTAINER Lacey-Anne Sanderson <laceyannesanderson@gmail.com>

USER root

WORKDIR /var/www

RUN curl -sL https://rpm.nodesource.com/setup_14.x | bash - \
  && yum install nodejs -y \
  && yum install git -y \
  && npm install -g yarn \
  && node --version && npm --version && yarn --version

RUN npm install -g @jbrowse/cli \
  && jbrowse --version

RUN git clone https://github.com/GMOD/jbrowse-components.git \
  && cd jbrowse-components && yarn

WORKDIR /var/www/jbrowse-components

EXPOSE 80 5432 3000
