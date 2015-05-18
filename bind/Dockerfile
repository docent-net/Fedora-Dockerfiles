# Based on the Fedora image
FROM fedora

MAINTAINER http://fedoraproject.org/wiki/Cloud

# install main packages:
RUN yum -y update && yum clean all
RUN yum -y install bind-utils bind && yum clean all

# gen rndc key:
RUN rndc-confgen -a -c /etc/rndc.key
RUN chown named:named /etc/rndc.key

# copy cfg files:
ADD ./cfg_files/init.d/named /etc/init.d/named
ADD ./cfg_files/named.conf /etc/named/named.conf
RUN mkdir /root/scripts -p
ADD ./cfg_files/root/scripts/init.sh /root/scripts/init.sh
RUN chmod +x /root/scripts/init.sh

# set up the BIND env:
RUN chmod +x /etc/init.d/named
RUN mkdir /var/dockerlock/subsys -p
#?? RUN mkdir /var/log/named

# init env
RUN /root/scripts/init.sh

EXPOSE 53

# start services:
CMD /usr/sbin/named -u named -f
#CMD /etc/init.d/named start
