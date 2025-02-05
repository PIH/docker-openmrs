FROM maven:3-jdk-8-slim

LABEL authors="Michael Seaton <mseaton@pih.org>, Andy Cotton <acotton@pih.org>"

ARG DEBIAN_FRONTEND=noninteractive

# We install firefox, as it is used by some modules (eg. coreapps) in Karma tests
# library required by Puppeeter, which is used to run some Karma tests using ChromeHeadless
# Selenium tests in some modules require there to be a valid file configured for OPENSSL_CONF
RUN apt-get update \
&& apt-get install -y firefox-esr docker gnupg \
    fonts-liberation gconf-service libappindicator1 libasound2 libatk1.0-0 \
    libcairo2 libcups2 libfontconfig1 libgbm-dev libgdk-pixbuf2.0-0 libgtk-3-0 libicu-dev libjpeg-dev  \
    libnspr4 libnss3 libpango-1.0-0 libpangocairo-1.0-0 libpng-dev libx11-6 libx11-xcb1 libxcb1  \
    libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 xdg-utils \
&& apt-get clean \
&& touch /root/openssl.conf


# Set Config home and work directories to allow running as non-root user, and for OPENSSL_CONF
ENV OPENSSL_CONF=/root/openssl.conf
ENV MAVEN_CONFIG=/var/maven/.m2
ENV HOME /var/maven
ENV MAVEN_HOME /var/maven
ENV MAVEN_OPTS -Duser.home=/var/maven
WORKDIR /data

ENTRYPOINT ["mvn"]