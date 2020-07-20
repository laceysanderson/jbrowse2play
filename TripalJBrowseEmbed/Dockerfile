FROM statonlab/tripal3_seeded

MAINTAINER Lacey-Anne Sanderson <laceyannesanderson@gmail.com>

## This image is focused on embedding JBrowse2 in Tripal.

WORKDIR /var/www/html/sites/all

RUN curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash - \
  && sudo yum install nodejs -y \
  && node --version && npm --version

RUN npm install -g @gmod/jbrowse-cli \
  && jbrowse --version

RUN mkdir tools && jbrowse create tools/jbrowse2
