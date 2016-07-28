FROM centos:7
MAINTAINER Leonardo Luduena <elnomade@gmail.com>
ENV REFRESHED_AT 2016-07-28

RUN yum -y install openssh-server wget tar nc nano dos2unix python-setuptools sudo && \
    yum clean all

RUN groupadd -r -g 700 devops && useradd -u 777 -s /bin/bash -m -d /opt/elnomade -g 700 elnomade
