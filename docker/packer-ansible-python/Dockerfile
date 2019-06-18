FROM python:3.7

MAINTAINER jcustenborder@gmail.com

ARG PACKER_URL='https://releases.hashicorp.com/packer/1.4.1/packer_1.4.1_linux_amd64.zip'
ARG VSPHERE_CLONE_URL='https://github.com/jetbrains-infra/packer-builder-vsphere/releases/download/v2.3/packer-builder-vsphere-clone.linux'
ARG VSPHERE_ISO_URL='https://github.com/jetbrains-infra/packer-builder-vsphere/releases/download/v2.3/packer-builder-vsphere-iso.linux'

RUN useradd --uid 1000 -m jenkins
RUN pip install ansible
RUN apt-get update && apt-get install -y rsync unzip
RUN curl -Ls -o /tmp/packer.zip $PACKER_URL \
    && unzip -d /usr/bin/ /tmp/packer.zip \
    && rm /tmp/packer.zip \
    && chmod +x /usr/bin/packer
RUN curl -Ls -o /usr/bin/packer-builder-vsphere-clone.linux $VSPHERE_CLONE_URL \
    && chmod +x /usr/bin/packer-builder-vsphere-clone.linux \
    && curl -Ls -o /usr/bin/packer-builder-vsphere-iso.linux $VSPHERE_ISO_URL \
    && chmod +x /usr/bin/packer-builder-vsphere-iso.linux
USER jenkins