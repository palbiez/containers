FROM docker.io/bitnami/minideb:bullseye

ARG TARGETARCH

LABEL org.opencontainers.image.authors="https://bitnami.com/contact" \
      org.opencontainers.image.description="Application packaged by Bitnami" \
      org.opencontainers.image.ref.name="2021.6.3-debian-11-r18" \
      org.opencontainers.image.source="https://github.com/bitnami/containers/tree/main/bitnami/scikit-learn-intel" \
      org.opencontainers.image.title="scikit-learn-intel" \
      org.opencontainers.image.vendor="VMware, Inc." \
      org.opencontainers.image.version="2021.6.3"

ENV HOME="/" \
    OS_ARCH="${TARGETARCH:-amd64}" \
    OS_FLAVOUR="debian-11" \
    OS_NAME="linux"

COPY prebuildfs /
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
# Install required system packages and dependencies
RUN install_packages ca-certificates curl libbz2-1.0 libc6 libcom-err2 libcrypt1 libffi7 libgcc-s1 libgssapi-krb5-2 libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 liblzma5 libncursesw6 libnsl2 libreadline8 libsqlite3-0 libssl1.1 libstdc++6 libtinfo6 libtirpc3 procps zlib1g
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f python-3.10.7-1-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/python-3.10.7-1-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/python-3.10.7-1-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c python-3.10.7-1-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf python-3.10.7-1-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf python-3.10.7-1-linux-${OS_ARCH}-debian-11.tar.gz python-3.10.7-1-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f scikit-learn-intel-2021.6.3-2-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/scikit-learn-intel-2021.6.3-2-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/scikit-learn-intel-2021.6.3-2-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c scikit-learn-intel-2021.6.3-2-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf scikit-learn-intel-2021.6.3-2-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf scikit-learn-intel-2021.6.3-2-linux-${OS_ARCH}-debian-11.tar.gz scikit-learn-intel-2021.6.3-2-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    if [ ! -f gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz ]; then \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz -O ; \
      curl -SsLf https://downloads.bitnami.com/files/stacksmith/gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256 -O ; \
    fi && \
    sha256sum -c gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256 && \
    tar -zxf gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
    rm -rf gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz gosu-1.14.0-154-linux-${OS_ARCH}-debian-11.tar.gz.sha256
RUN apt-get autoremove --purge -y curl && \
    apt-get update && apt-get upgrade -y && \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives
RUN chmod g+rwX /opt/bitnami
RUN mkdir /.local && chmod g+rwX /.local

COPY rootfs /
RUN /opt/bitnami/scripts/scikit-learn-intel/postunpack.sh
ENV APP_VERSION="2021.6.3" \
    BITNAMI_APP_NAME="scikit-learn-intel" \
    PATH="/opt/bitnami/python/bin:/opt/bitnami/common/bin:$PATH"

WORKDIR /app
USER 1001
ENTRYPOINT [ "/opt/bitnami/scripts/scikit-learn-intel/entrypoint.sh" ]
CMD [ "python" ]
