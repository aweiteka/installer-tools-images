FROM centos:centos7
MAINTAINER Aaron Weitekamp <aweiteka@redhat.com>

RUN yum -y install http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && yum clean all

RUN yum install -y python-devel python-pip gcc && yum clean all

RUN pip install python-heatclient

WORKDIR /root/heat-templates

CMD /bin/bash

LABEL RUN docker run -it --rm --net=host -v `pwd`:/root/heat-templates --name NAME -e NAME=NAME -e IMAGE=IMAGE IMAGE
