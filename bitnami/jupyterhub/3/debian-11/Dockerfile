FROM docker.io/bitnami/minideb:bullseye

ARG TARGETARCH

LABEL org.opencontainers.image.authors="https://bitnami.com/contact" \
      org.opencontainers.image.description="Application packaged by Bitnami" \
      org.opencontainers.image.ref.name="3.0.0-debian-11-r2" \
      org.opencontainers.image.source="https://github.com/bitnami/containers/tree/main/bitnami/jupyterhub" \
      org.opencontainers.image.title="jupyterhub" \
      org.opencontainers.image.vendor="VMware, Inc." \
      org.opencontainers.image.version="3.0.0"

ENV HOME="/" \
    OS_ARCH="${TARGETARCH:-amd64}" \
    OS_FLAVOUR="debian-11" \
    OS_NAME="linux"

COPY prebuildfs /
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
# Install required system packages and dependencies
RUN install_packages ca-certificates curl libbrotli1 libcom-err2 libcrypt1 libcurl4 libgcc-s1 libgcrypt20 libgmp10 libgnutls30 libgpg-error0 libgssapi-krb5-2 libhogweed6 libidn2-0 libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libldap-2.4-2 libnettle8 libnghttp2-14 libp11-kit0 libpsl5 librtmp1 libsasl2-2 libssh2-1 libstdc++6 libtasn1-6 libunistring2 procps zlib1g
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f miniconda-4.12.0-157-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/miniconda-4.12.0-157-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/miniconda-4.12.0-157-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c miniconda-4.12.0-157-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf miniconda-4.12.0-157-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf miniconda-4.12.0-157-linux-${OS_ARCH}-debian-11.tar.gz miniconda-4.12.0-157-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f jupyterhub-3.0.0-3-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/jupyterhub-3.0.0-3-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/jupyterhub-3.0.0-3-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c jupyterhub-3.0.0-3-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf jupyterhub-3.0.0-3-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf jupyterhub-3.0.0-3-linux-${OS_ARCH}-debian-11.tar.gz jupyterhub-3.0.0-3-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN apt-get autoremove --purge -y curl && \
    apt-get update && apt-get upgrade -y && \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives
RUN chmod g+rwX /opt/bitnami

ENV APP_VERSION="3.0.0" \
    BITNAMI_APP_NAME="jupyterhub" \
    PATH="/opt/bitnami/miniconda/bin:/opt/bitnami/miniconda/bin/:$PATH"

USER 1001
ENTRYPOINT [ "jupyterhub" ]
