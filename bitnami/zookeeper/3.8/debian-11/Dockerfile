FROM docker.io/bitnami/minideb:bullseye

ARG TARGETARCH

LABEL org.opencontainers.image.authors="https://bitnami.com/contact" \
      org.opencontainers.image.description="Application packaged by Bitnami" \
      org.opencontainers.image.ref.name="3.8.0-debian-11-r43" \
      org.opencontainers.image.source="https://github.com/bitnami/containers/tree/main/bitnami/zookeeper" \
      org.opencontainers.image.title="zookeeper" \
      org.opencontainers.image.vendor="VMware, Inc." \
      org.opencontainers.image.version="3.8.0"

ENV HOME="/" \
    OS_ARCH="${TARGETARCH:-amd64}" \
    OS_FLAVOUR="debian-11" \
    OS_NAME="linux" \
    PATH="/opt/bitnami/common/bin:/opt/bitnami/java/bin:/opt/bitnami/zookeeper/bin:$PATH"

COPY prebuildfs /
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
# Install required system packages and dependencies
RUN install_packages ca-certificates curl libc6 netcat procps xmlstarlet zlib1g
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f wait-for-port-1.0.3-154-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/wait-for-port-1.0.3-154-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/wait-for-port-1.0.3-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c wait-for-port-1.0.3-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf wait-for-port-1.0.3-154-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf wait-for-port-1.0.3-154-linux-${OS_ARCH}-debian-11.tar.gz wait-for-port-1.0.3-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f java-11.0.16-0-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/java-11.0.16-0-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/java-11.0.16-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c java-11.0.16-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf java-11.0.16-0-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf java-11.0.16-0-linux-${OS_ARCH}-debian-11.tar.gz java-11.0.16-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f zookeeper-3.8.0-156-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/zookeeper-3.8.0-156-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/zookeeper-3.8.0-156-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c zookeeper-3.8.0-156-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf zookeeper-3.8.0-156-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf zookeeper-3.8.0-156-linux-${OS_ARCH}-debian-11.tar.gz zookeeper-3.8.0-156-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN apt-get autoremove --purge -y curl && \
    apt-get update && apt-get upgrade -y && \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives
RUN chmod g+rwX /opt/bitnami
RUN ln -s /opt/bitnami/scripts/zookeeper/entrypoint.sh /entrypoint.sh
RUN ln -s /opt/bitnami/scripts/zookeeper/run.sh /run.sh

COPY rootfs /
RUN /opt/bitnami/scripts/zookeeper/postunpack.sh
ENV APP_VERSION="3.8.0" \
    BITNAMI_APP_NAME="zookeeper"

EXPOSE 2181 2888 3888 8080

USER 1001
ENTRYPOINT [ "/opt/bitnami/scripts/zookeeper/entrypoint.sh" ]
CMD [ "/opt/bitnami/scripts/zookeeper/run.sh" ]
