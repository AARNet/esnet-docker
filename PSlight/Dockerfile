# perfSONAR Light

FROM centos:centos6
MAINTAINER Brian Tierney <bltierney@es.net>

RUN yum clean all && \
    rpm -hUv https://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm && \ 
    rpm -hUv http://software.internet2.edu/rpms/el6/x86_64/main/RPMS/Internet2-repo-0.5-3.noarch.rpm && \ 
    yum -y update &&  \
    yum -y install traceroute net-tools ntp python-setuptools supervisor perfSONAR_PS-Bundles-Level1 

ADD supervisord.conf /etc/supervisord.conf
ADD ls_registration_daemon.conf /opt/perfsonar_ps/ls_registration_daemon/etc/ls_registration_daemon.conf

# BWCTL - 4823, 5001-5900, 6001-6200
# OWAMP - 861, 8760-9960
EXPOSE 4823 5001-5900 6001-6200 861 8760-9960

# add pid directory
VOLUME /var/run

CMD /usr/bin/supervisord -c /etc/supervisord.conf
