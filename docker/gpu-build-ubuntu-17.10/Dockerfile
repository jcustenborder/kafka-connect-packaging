FROM ubuntu:17.10

MAINTAINER jcustenborder@gmail.com

ARG USER_HOME_DIR="/home/jenkins"

RUN useradd --uid 1000 -m jenkins

ENV CUDA_ROOT="/opt/cuda"

RUN apt-get update && apt-get upgrade -y
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y ocl-icd-opencl-dev libmicrohttpd-dev libssl-dev \
    cmake build-essential ruby2.3 ruby2.3-dev wget dirmngr hwloc
RUN apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1704/x86_64/7fa2af80.pub
RUN bash -c 'echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1704/x86_64 /" > /etc/apt/sources.list.d/cuda.list'
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y cuda
RUN gem install fpm bundler rake
USER jenkins
