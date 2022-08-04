FROM maven:3-jdk-8

MAINTAINER Michael Seaton <mseaton@pih.org>

ARG DEBIAN_FRONTEND=noninteractive

# We install firefox, as it is used by some modules (eg. coreapps) in Karma tests
RUN apt-get update
RUN apt-get install -y git lsb-release wget software-properties-common
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A6DCF7707EBC211F
RUN apt-add-repository "deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu focal main"
RUN apt-get update
RUN apt-get install -y firefox

CMD ["mvn"]