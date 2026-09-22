FROM alpine:3.21

LABEL authors="Michael Seaton <mseaton@pih.org>"

# p7zip baked in, so creating/extracting .7z and .zip archives never needs network access at runtime.
# Otherwise a plain alpine image (sh, tar, gzip, find, chown), so it's a drop-in replacement for
# alpine:3.21 in scripts that also need 7z.
RUN apk add --no-cache p7zip

CMD ["/bin/sh"]
