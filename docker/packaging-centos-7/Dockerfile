FROM centos:7

MAINTAINER jcustenborder@gmail.com

ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_CONFIG "$USER_HOME_DIR/.m2"

RUN useradd --uid 1000 -m jenkins
RUN yum upgrade -y
RUN yum install -y rpm-build ruby ruby-devel rubygems java-1.8.0-openjdk-headless
RUN yum groupinstall -y "Development Tools"
RUN gem install fpm
RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && curl -fsSL http://apache.osuosl.org/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz \
    | tar -xzC /usr/share/maven --strip-components=1 \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

USER jenkins