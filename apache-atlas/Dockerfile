FROM openjdk:8-jdk-alpine
MAINTAINER Ludovic Chane Won In <ludovic@chanewon.in>

# Install required packages for installation
RUN apk add --no-cache \
    bash \
    su-exec \
    python 

# Define versions of apache atlas
ARG DISTRO_NAME=apache-atlas-0.7.1-incubating

# Add local bin archive
COPY "$DISTRO_NAME-bin.tar.gz" /

# Unarchive
RUN set -x \
    && cd / \
    && tar -xzf "$DISTRO_NAME-bin.tar.gz"


WORKDIR /$DISTRO_NAME

EXPOSE 21000

ENV PATH=$PATH:/$DISTRO_NAME/bin 

COPY "hbase-site.xml" /$DISTRO_NAME/hbase/conf

ENTRYPOINT ["/apache-atlas-0.7.1-incubating/bin/atlas_start.py"]
