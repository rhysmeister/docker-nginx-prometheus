FROM centos:7.9.2009

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

COPY files/nginx.repo /etc/yum.repos.d/nginx.repo
RUN yum install net-tools yum-utils nginx -y
COPY files/nginx.conf /etc/nginx/nginx.conf
RUN systemctl enable nginx

RUN mkdir -p /opt/grok_exporter/patterns
COPY files/grok_exporter /opt/grok_exporter/
RUN chmod +x /opt/grok_exporter/grok_exporter
COPY files/grok_exporter.conf /etc/grok_exporter/grok_exporter.conf
COPY files/patterns/* /etc/grok_exporter/patterns/
COPY files/grok_exporter.service /usr/lib/systemd/system/grok_exporter.service
RUN systemctl enable grok_exporter

EXPOSE 80/tcp

STOPSIGNAL SIGQUIT

CMD ["/usr/sbin/init"]