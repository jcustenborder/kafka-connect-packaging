FROM ubuntu:17.04

MAINTAINER jcustenborder@gmail.com

ARG USER_HOME_DIR="/home/jenkins"

RUN useradd --uid 1000 -m jenkins

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y ocl-icd-opencl-dev libmicrohttpd-dev libssl-dev cmake build-essential ruby2.3
RUN gem install fpm bundler rake

USER jenkins
