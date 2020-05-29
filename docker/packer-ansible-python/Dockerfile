FROM python:3.7

MAINTAINER jcustenborder@gmail.com

ARG PACKER_VERSION='1.5.6'
ARG PACKER_URL='https://releases.hashicorp.com/packer/1.5.6/packer_1.5.6_linux_amd64.zip'

RUN useradd --uid 1000 -m jenkins
RUN pip install ansible
RUN apt-get update && apt-get install -y rsync unzip
RUN curl -Ls -o /tmp/packer.zip $PACKER_URL \
    && unzip -d /usr/bin/ /tmp/packer.zip \
    && rm /tmp/packer.zip \
    && chmod +x /usr/bin/packer
USER jenkins