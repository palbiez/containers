FROM docker.io/bitnami/minideb:bullseye

ARG TARGETARCH

LABEL org.opencontainers.image.authors="https://bitnami.com/contact" \
      org.opencontainers.image.description="Application packaged by Bitnami" \
      org.opencontainers.image.ref.name="1.12.1-debian-11-r4" \
      org.opencontainers.image.source="https://github.com/bitnami/containers/tree/main/bitnami/cosign" \
      org.opencontainers.image.title="cosign" \
      org.opencontainers.image.vendor="VMware, Inc." \
      org.opencontainers.image.version="1.12.1"

ENV HOME="/" \
    OS_ARCH="${TARGETARCH:-amd64}" \
    OS_FLAVOUR="debian-11" \
    OS_NAME="linux"

COPY prebuildfs /
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
# Install required system packages and dependencies
RUN install_packages ca-certificates curl procps
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f cosign-1.12.1-0-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/cosign-1.12.1-0-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/cosign-1.12.1-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c cosign-1.12.1-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf cosign-1.12.1-0-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf cosign-1.12.1-0-linux-${OS_ARCH}-debian-11.tar.gz cosign-1.12.1-0-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN apt-get autoremove --purge -y curl && \
    apt-get update && apt-get upgrade -y && \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives
RUN chmod g+rwX /opt/bitnami
RUN mkdir -p "/cosign-keys" && chmod -R 777 "/cosign-keys"
RUN mkdir /.sigstore && chmod g+rwX /.sigstore

ENV APP_VERSION="1.12.1" \
    BITNAMI_APP_NAME="cosign" \
    PATH="/opt/bitnami/cosign/bin:$PATH"

WORKDIR /cosign-keys
USER 1001
ENTRYPOINT [ "cosign" ]
CMD [ "--help" ]
