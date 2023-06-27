percona-0.1-4
=======================

This Percona image is intended to be a replacement for manual installation of Percona-0.1.4 for backing up from and restoring into MySQL 5.6 instances.  This is based on an Ubuntu 18.04 base image, which has the required libraries needed to support this package.

### Development

To build this image locally:

```docker build --rm -t partnersinhealth/percona-0.1-4 .```

### Usage

#### Create a backup from a MySQL instance running in Docker

* Assuming you have a MySQL 5.6 Docker container named `$CONTAINER`
* Assuming this container has host volumes configured for the `/var/lib/mysql` and `/run/mysqld` directories
* Assuming you have the MySQL root password in `$MYSQL_ROOT_PASSWORD`
* Assuming you have a directory into which you want to store your backup at `$BACKUP_DIR`
* Assuming you have a space-delimited list of database names you want to included in `$DATABASES`

```shell
docker run --name percona --rm --volumes-from $CONTAINER -v $BACKUP_DIR:/opt/backup partnersinhealth/percona-0.1-4 innobackupex --user=root --password=$MYSQL_ROOT_PASSWORD --no-timestamp --databases="$DATABASES" /opt/backup
```

#### Prepare an existing backup to make it consistent and suitable for restoration

* Assuming you have a directory into which the backup was done at `$BACKUP_DIR`

```shell
docker run --name percona --rm -v $BACKUP_DIR:/opt/backup partnersinhealth/percona:0.1-4 innobackupex --apply-log  /opt/backup
```

### Restore a previously prepared backup

* Assuming you have a directory into which the backup was prepared at `$BACKUP_DIR`
* Assuming you have a directory into which you want the restore into (the new MySQL data directory) at `$RESTORE_DIR`

```shell
docker run --name percona --rm -v $BACKUP_DIR:/opt/backup -v $RESTORE_DIR:/var/lib/mysql partnersinhealth/percona:0.1-4 innobackupex --copy-back --datadir=/var/lib/mysql /opt/backup
```

### CI

This image is built by github actions automatically upon each commit, and published to partnersinhealth/percona-0.1-4 in DockerHub.