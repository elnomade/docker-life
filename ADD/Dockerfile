FROM elnomade/centos7base
MAINTAINER Leonardo Luduena <elnomade@gmail.com>
ENV REFRESHED_AT 2016-07-28


#Some examples including ADD

#Copying file to a directory
ADD lorem-ipsum.txt /opt/
RUN ls -lhart /opt/ && \
    echo "In this context, docker copied the file as user root"

USER elnomade
WORKDIR /opt/elnomade
ADD lorem-ipsum.txt .
RUN ls -lhart && \
    echo -e "In this new context, even when WORKDIR works\nUSER only honors RUN \nthen docker copied the file as user root"

#Dumping the content of directory tree to /opt/dump/
USER root
RUN mkdir /opt/dump
ADD tree /opt/dump/
RUN ls -lhart /opt/dump/ && \
    du -h /opt/dump/ && \
    echo -e "Docker dumped the content of tree directory, to /opt/dump/\nhonoring directories and files organization"

#Copying the directory tree to /opt/
ADD tree /opt/tree
RUN ls -lhart /opt/ && \
    du -h /opt/ && \
    echo -e "Docker copied the content of tree directory, \nto a new directory named /opt/tree/\nhonoring directories and files organization"

#Inflating oak.tar.gz to /tmp
#In order to create oak.tar.gz:
#$cp -R tree oak
#$sudo chown -R 777:700 oak
#$sudo chmod 777 oak/big-branch/bird-nest.txt
#$tar cvfz oak.tar.gz oak
ADD oak.tar.gz /tmp
RUN ls -lhart /tmp/ && \
    du -h /tmp/ && \
    ls -lh /tmp/oak/big-branch/bird-nest.txt && \    
    echo -e "Docker inflated the content of oak.tar.gz, \nto a new directory named /tmp/oak/\nhonoring directories and files organization \nAND keeping the user:group ownership \nAND file permissions"


#Getting compressed file from url
ADD https://github.com/elnomade/docker-life/archive/master.zip /opt
ADD https://github.com/csete/gpredict/archive/v1.3.tar.gz /opt
RUN ls -lhart /opt/ && \
	echo -e "ADD supports getting files from remote locations \nbut it doesn't include file decompression"
