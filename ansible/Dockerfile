FROM centos:centos7
MAINTAINER Aaron Weitekamp <aweiteka@redhat.com>

RUN yum -y install http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && yum clean all

RUN yum install -y ansible && yum clean all

WORKDIR /root/ansible-playbooks

CMD /bin/bash

LABEL RUN docker run -it --rm --net=host -v ~/.ssh/id_rsa:/root/.ssh/id_rsa -v /etc/ansible/hosts:/etc/ansible/hosts -v `pwd`:/root/ansible-playbooks --name NAME -e NAME=NAME -e IMAGE=IMAGE IMAGE
