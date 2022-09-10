FROM ubuntu:20.04

ENV USER root
ENV HOME /root
ENV SHELL bash

ENV DEBIAN_FRONTEND noninteractive
ENV TZ America/New_York
ENV TERM xterm-color


ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

USER root:root

# system updates
RUN  apt-get -y upgrade && apt-get -y update && apt-get install -y locales apt-utils software-properties-common && locale-gen en_US.UTF-8 && dpkg-reconfigure locales && echo "system updates complete"

# additional system package installs
RUN apt-get install -qq -y --no-install-recommends shellcheck openssh-server && echo "additional system package installs complete"

# base system package installs
RUN apt-get install -qq -y --no-install-recommends apt-transport-https ca-certificates  systemd systemd-cron sudo   git gzip  unzip zip wget curl  python3.7 python3-pip  python-dev python3-dev python3-mysql.connector default-libmysqlclient-dev build-essential && echo "base system package installs complete"

RUN apt install -y mysql-server libmysqlclient-dev

RUN pip3 install Django mysqlclient

CMD [ "tail", "-f", "/dev/null"]

# setup