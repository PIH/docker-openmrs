openmrs-maven-build
=======================

**DEPRECATED:** this image is no longer rebuilt or published. Its base image (`maven:3-jdk-8-slim`, Debian 11) is past end of
life and can no longer install security updates, so it fails to build. The last published image (`latest`/`main`,
2025-02-05) remains available on Docker Hub, but will not receive any further updates, including security fixes. The
Dockerfile is kept here for reference only.

### Development

To build this image locally:

```docker build --rm -t openmrs-maven-build .```

To use this image locally to build a particular project:

1. cd into that project
2. docker run -it --rm -v $(pwd):/data -w /data openmrs-maven-build mvn clean install
3. to re-use downloaded maven artifacts across executions, you can first create a directory on the host for these, and then mount this volume into /root/.m2 in the docker container

### CI

This image was previously built by github actions automatically upon each commit, and published to partnersinhealth/openmrs-maven-build in DockerHub.