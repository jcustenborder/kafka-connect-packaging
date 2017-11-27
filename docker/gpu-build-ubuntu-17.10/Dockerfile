FROM ubuntu:17.10

MAINTAINER jcustenborder@gmail.com

ARG USER_HOME_DIR="/home/jenkins"

RUN useradd --uid 1000 -m jenkins

RUN apt-get update && apt-get upgrade -y
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y ocl-icd-opencl-dev libmicrohttpd-dev libssl-dev \
    cmake build-essential ruby2.3 ruby2.3-dev wget dirmngr libhwloc-dev libmicrohttpd-dev
RUN apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1704/x86_64/7fa2af80.pub
RUN bash -c 'echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1704/x86_64 /" > /etc/apt/sources.list.d/cuda.list'

# Install AMD APP SDK
ADD http://s3.amazonaws.com/omnia-ci/AMD-APP-SDKInstaller-v3.0.130.135-GA-linux64.tar.bz2 .
RUN pwd
RUN ls -ltr
RUN tar xjf AMD-APP-SDKInstaller-v3.0.130.135-GA-linux64.tar.bz2 && \
    ./AMD-APP-SDK-v3.0.130.135-GA-linux64.sh -- -s -a yes && \
    rm -f AMD-APP-SDK-v3.0.130.135-GA-linux64.sh AMD-APP-SDKInstaller-v3.0.130.135-GA-linux64.tar.bz2 && \
    rm -rf /opt/AMDAPPSDK-3.0/samples/

ENV AMDAPPSDKROOT=/opt/AMDAPPSDK-3.0
ENV OPENCL_HOME=/opt/AMDAPPSDK-3.0
ENV OPENCL_LIBPATH=/opt/AMDAPPSDK-3.0/lib/x86_64

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y cuda
RUN gem install fpm bundler rake
USER jenkins
