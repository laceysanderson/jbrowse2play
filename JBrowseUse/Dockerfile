FROM node:lts-alpine3.13

MAINTAINER Lacey-Anne Sanderson <laceyannesanderson@gmail.com>

USER root

WORKDIR /

RUN npm install -g @jbrowse/cli \
  && jbrowse --version

RUN jbrowse create jbrowse2

EXPOSE 5000

WORKDIR /jbrowse2

CMD npx serve .
