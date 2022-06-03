#Getting base image from CentOS 7
FROM centos:7

MAINTAINER Eugenio Guerra O. <eugenioguerrao@gmail.com>

LABEL Remarks="This is a Dockerfile for synopsys license service SCL v2021.12"

#Update Software Repository
RUN yum -y update

#Install lsb
RUN yum -y install lsb

#Copy necessary files
COPY linux64/ /opt/linux64/

EXPOSE 27020

#Run lmgrd
CMD ["/opt/linux64/bin/lmgrd", "-c /opt/linux64/license/SynopsysKey.lic", "-l /opt/linux64/logs/debug.log"] 

