# base image
FROM centos:7

# system update
RUN yum -y update && yum clean all
RUN yum reinstall -y glibc-common && yum clean all

RUN localedef -c -i ja_JP -f UTF-8 ja_JP.UTF-8

RUN sed -i -e '/override_install_langs/s/$/,ja_JP.utf8/g' /etc/yum.conf

ENV LANG ja_JP.UTF-8

RUN rm -f /etc/localtime && ln -s /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN yum install -y openssh-server
RUN ssh-keygen -t rsa -N "" -f /etc/ssh/ssh_host_rsa_key

RUN yum clean all

RUN sed -ri 's/^#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN echo 'root:root' | chpasswd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]