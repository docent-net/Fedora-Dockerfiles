# Based on the Fedora image
FROM fedora

MAINTAINER http://fedoraproject.org/wiki/Cloud

# install main packages:
RUN dnf -y update && dnf clean all
RUN dnf -y install haproxy && dnf clean all

# copy cfg files:
ADD ./cfg_files/haproxy.cfg /etc/haproxy/haproxy.cfg
#RUN mkdir /root/scripts -p
#ADD ./cfg_files/root/scripts/init.sh /root/scripts/init.sh
#RUN chmod +x /root/scripts/init.sh

# init env
#RUN /root/scripts/init.sh

#EXPOSE 53

# start haproxy:
CMD /usr/sbin/haproxy -db -f /etc/haproxy/haproxy.cfg
