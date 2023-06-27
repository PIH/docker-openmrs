FROM ubuntu:18.04

MAINTAINER Michael Seaton <mseaton@pih.org>

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get install -y git lsb-release wget software-properties-common

RUN wget https://repo.percona.com/apt/percona-release_0.1-4.xenial_all.deb
RUN dpkg -i percona-release_0.1-4.xenial_all.deb
RUN apt-get update
RUN apt-get install -y percona-xtrabackup

CMD /bin/bash
