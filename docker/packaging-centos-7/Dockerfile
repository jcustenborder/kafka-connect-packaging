FROM centos:7

MAINTAINER jcustenborder@gmail.com

ARG MAVEN_VERSION=3.5.4
ARG USER_HOME_DIR="/home/jenkins"

RUN groupadd -g 994 docker
RUN useradd --uid 1000 -m -G docker jenkins

ADD docker-ce-stable.repo /etc/yum.repos.d/docker-ce-stable.repo
RUN yum install -y epel-release
RUN yum clean all && yum upgrade -y
RUN yum install -y \
    rpm-build \
    ruby \
    ruby-devel \
    rubygems \
    java-1.8.0-openjdk-devel \
    createrepo \
    docker-compose \
    docker-ce \
    git \
    graphviz \
    dpkg-dev
RUN yum groupinstall -y "Development Tools"
RUN gem install fpm bundler rake
RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && curl -fsSL http://apache.osuosl.org/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz \
    | tar -xzC /usr/share/maven --strip-components=1 \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_CONFIG "$USER_HOME_DIR/.m2"
#ENV JAVA_HOME=/etc/alternatives/java_sdk_1.8.0
ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US.UTF-8

USER jenkins
