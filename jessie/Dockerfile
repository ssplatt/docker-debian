FROM debian:jessie
MAINTAINER “Brett Taylor” <sweet.brett@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
ENV container docker

RUN apt-get update ; \ 
  apt-get upgrade -y ; \
  apt-get install -y systemd systemd-sysv dbus udev lsb-release curl \
      git cron at logrotate rsyslog unattended-upgrades ssmtp lsof procps \
			initscripts libsystemd0 libudev1 sysvinit-utils util-linux; \
  apt-get clean ; \
  (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i = systemd-tmpfiles-setup.service ] || rm -f $i; done) ; \
  rm -f /lib/systemd/system/multi-user.target.wants/* ; \
  rm -f /etc/systemd/system/*.wants/* ; \
  rm -f /lib/systemd/system/local-fs.target.wants/* ; \
  rm -f /lib/systemd/system/sockets.target.wants/*udev* ; \
  rm -f /lib/systemd/system/sockets.target.wants/*initctl*

VOLUME [ “/sys/fs/cgroup” ]

CMD [“/sbin/init”]
