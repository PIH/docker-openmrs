p7zip
=======================

A plain Alpine image with [p7zip](https://pkgs.alpinelinux.org/package/v3.21/main/x86_64/p7zip) (`7z`) preinstalled, for
creating and extracting `.7z` and `.zip` archives -- including password-protected ones -- without needing network access
at runtime to install it. Apart from `7z`, it's identical to `alpine:3.21` (`sh`, `tar`, `gzip`, `find`, `chown`, etc.),
so it can stand in for that image in any script that also needs `7z`.

Used by [openmrs-contrib-distro-tools](https://github.com/PIH/openmrs-contrib-distro-tools) for its backup, restore and
archive utilities.

### Development

To build this image locally:

```docker build --rm -t partnersinhealth/p7zip .```

### Usage

#### Create a password-protected archive of a directory

* Assuming the directory to archive is at `$SOURCE_DIR`
* Assuming the archive should be written into `$OUTPUT_DIR`
* Assuming the archive password is in `$ARCHIVE_PASSWORD` (passed by name only, so its value never appears in `ps`)

```shell
docker run --rm -e ARCHIVE_PASSWORD -v $SOURCE_DIR:/source:ro -v $OUTPUT_DIR:/out partnersinhealth/p7zip \
    sh -c '7z a -p"$ARCHIVE_PASSWORD" -t7z /out/backup.7z /source'
```

#### Extract an archive

* Assuming the archive is at `$ARCHIVE_DIR/backup.7z`
* Assuming it should be extracted into `$OUTPUT_DIR`

```shell
docker run --rm -e ARCHIVE_PASSWORD -v $ARCHIVE_DIR:/archive:ro -v $OUTPUT_DIR:/out partnersinhealth/p7zip \
    sh -c '7z x -p"$ARCHIVE_PASSWORD" -o/out -y /archive/backup.7z'
```

### CI

This image is built by github actions automatically upon each commit, and published to partnersinhealth/p7zip in DockerHub.
