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

# library required by Puppeeter, which is used to run some Karma tests using ChromeHeadless
RUN apt-get install -y fonts-liberation gconf-service libappindicator1 libasound2 libatk1.0-0 \
    libcairo2 libcups2 libfontconfig1 libgbm-dev libgdk-pixbuf2.0-0 libgtk-3-0 libicu-dev libjpeg-dev  \
    libnspr4 libnss3 libpango-1.0-0 libpangocairo-1.0-0 libpng-dev libx11-6 libx11-xcb1 libxcb1  \
    libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6  xdg-utils

# Selenium tests in some modules require there to be a valid file configured for OPENSSL_CONF
RUN touch /root/openssl.conf
ENV OPENSSL_CONF=/root/openssl.conf

CMD ["mvn"]
