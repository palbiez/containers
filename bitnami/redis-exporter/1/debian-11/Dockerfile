FROM docker.io/bitnami/minideb:bullseye

ARG TARGETARCH

LABEL org.opencontainers.image.authors="https://bitnami.com/contact" \
      org.opencontainers.image.description="Application packaged by Bitnami" \
      org.opencontainers.image.ref.name="1.44.0-debian-11-r12" \
      org.opencontainers.image.source="https://github.com/bitnami/containers/tree/main/bitnami/redis-exporter" \
      org.opencontainers.image.title="redis-exporter" \
      org.opencontainers.image.vendor="VMware, Inc." \
      org.opencontainers.image.version="1.44.0"

ENV HOME="/" \
    OS_ARCH="${TARGETARCH:-amd64}" \
    OS_FLAVOUR="debian-11" \
    OS_NAME="linux"

COPY prebuildfs /
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
# Install required system packages and dependencies
RUN install_packages ca-certificates curl procps
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f redis-exporter-1.44.0-0-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/redis-exporter-1.44.0-0-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/redis-exporter-1.44.0-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c redis-exporter-1.44.0-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf redis-exporter-1.44.0-0-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf redis-exporter-1.44.0-0-linux-${OS_ARCH}-debian-11.tar.gz redis-exporter-1.44.0-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN apt-get update && apt-get upgrade -y && \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives
RUN chmod g+rwX /opt/bitnami

ENV APP_VERSION="1.44.0" \
    BITNAMI_APP_NAME="redis-exporter" \
    PATH="/opt/bitnami/redis-exporter/bin:$PATH"

EXPOSE 9121

WORKDIR /opt/bitnami/redis-exporter
USER 1001
ENTRYPOINT [ "redis_exporter" ]
