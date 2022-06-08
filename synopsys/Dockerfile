#Getting base image from CentOS 7
FROM centos:7

MAINTAINER Eugenio Guerra O. <eugenioguerrao@gmail.com>

LABEL Remarks="This is a Dockerfile for synopsys license service SCL v2021.12"

#Systemd
ENV container docker
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]

#Update Software Repository
RUN yum -y update

#Install lsb
RUN yum -y install lsb

#Copy necessary files
COPY linux64/ /opt/linux64/
COPY linux64/systemd/scl7.service /etc/systemd/system/

#Enable scl7 service
RUN systemctl enable /etc/systemd/system/scl7.service
RUN chmod +x /etc/systemd/system/scl7.service

EXPOSE 27020

#Run lmgrd
#CMD ["/opt/linux64/bin/lmgrd", "-c /opt/linux64/license/SynopsysKey.lic", "-l /opt/linux64/logs/debug.log"] 

CMD ["systemctl start scl7"]
