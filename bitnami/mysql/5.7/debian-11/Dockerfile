FROM docker.io/bitnami/minideb:bullseye

ARG TARGETARCH

LABEL org.opencontainers.image.authors="https://bitnami.com/contact" \
      org.opencontainers.image.description="Application packaged by Bitnami" \
      org.opencontainers.image.ref.name="5.7.39-debian-11-r26" \
      org.opencontainers.image.source="https://github.com/bitnami/containers/tree/main/bitnami/mysql" \
      org.opencontainers.image.title="mysql" \
      org.opencontainers.image.vendor="VMware, Inc." \
      org.opencontainers.image.version="5.7.39"

ENV HOME="/" \
    OS_ARCH="${TARGETARCH:-amd64}" \
    OS_FLAVOUR="debian-11" \
    OS_NAME="linux"

COPY prebuildfs /
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
# Install required system packages and dependencies
RUN install_packages ca-certificates curl libaio1 libc6 libcom-err2 libcrypt1 libgcc-s1 libgssapi-krb5-2 libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libsasl2-2 libssl1.1 libstdc++6 libtinfo6 libtirpc3 procps psmisc
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    for COMPONENT in \
      "ini-file-1.4.3-153-linux-${OS_ARCH}-debian-11" \
      "mysql-5.7.39-2-linux-${OS_ARCH}-debian-11" \
      "gosu-1.14.0-154-linux-${OS_ARCH}-debian-11" ; \
    do \
      if [ ! -f "${COMPONENT}.tar.gz" ]; then \
        curl -SsLf https://downloads.bitnami.com/files/stacksmith/${COMPONENT}.tar.gz -O ; \
        curl -SsLf https://downloads.bitnami.com/files/stacksmith/${COMPONENT}.tar.gz.sha256 -O ; \
      fi && \
      sha256sum -c "${COMPONENT}.tar.gz.sha256" && \
      tar -zxf "${COMPONENT}.tar.gz" -C /opt/bitnami --strip-components=2 --no-same-owner --wildcards '*/files' && \
      rm -rf "${COMPONENT}.tar.gz{,sha256}" ; \
    done
RUN apt-get autoremove --purge -y curl && \
    apt-get update && apt-get upgrade -y && \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives
RUN chmod g+rwX /opt/bitnami
RUN mkdir /docker-entrypoint-initdb.d

COPY rootfs /
RUN /opt/bitnami/scripts/mysql/postunpack.sh
ENV APP_VERSION="5.7.39" \
    BITNAMI_APP_NAME="mysql" \
    PATH="/opt/bitnami/common/bin:/opt/bitnami/mysql/bin:/opt/bitnami/mysql/sbin:$PATH"

EXPOSE 3306

USER 1001
ENTRYPOINT [ "/opt/bitnami/scripts/mysql/entrypoint.sh" ]
CMD [ "/opt/bitnami/scripts/mysql/run.sh" ]
