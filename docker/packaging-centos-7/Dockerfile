FROM centos:7

RUN yum upgrade -y
RUN yum install -y rpm-build ruby ruby-devel rubygems
RUN yum groupinstall -y "Development Tools"
RUN gem install fpm