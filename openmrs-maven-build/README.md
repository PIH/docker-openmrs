openmrs-maven-build
=======================

### Development

To build this image locally:

```docker build --rm -t openmrs-maven-build .```

To use this image locally to build a particular project:

1. cd into that project
2. docker run -it --rm -v $(pwd):/data -w /data openmrs-maven-build mvn clean install
3. to re-use downloaded maven artifacts across executions, you can first create a directory on the host for these, and then mount this volume into /root/.m2 in the docker container

### CI

This image is built by github actions automatically upon each commit, and published to partnersinhealth/openmrs-maven-build in DockerHub.