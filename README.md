docker-openmrs
=======================

Docker images used for OpenMRS development, testing, and deployment

### Images

Each is built and published to Docker Hub by GitHub Actions on every commit to its directory. See each directory's README
for details.

* [openmrs-maven-build](openmrs-maven-build) (`partnersinhealth/openmrs-maven-build`) - Maven and JDK 8, with the browsers
  and libraries needed to build and run tests for OpenMRS modules in CI
* [percona-0.1-4](percona-0.1-4) (`partnersinhealth/percona-0.1-4`) - Percona XtraBackup, for backing up from and
  restoring into MySQL 5.6 instances
* [p7zip](p7zip) (`partnersinhealth/p7zip`) - Alpine with `7z` preinstalled, for creating and extracting `.7z` and `.zip`
  archives (including password-protected ones) without network access at runtime
