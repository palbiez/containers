FROM docker.io/bitnami/minideb:bullseye

ARG TARGETARCH

LABEL org.opencontainers.image.authors="https://bitnami.com/contact" \
      org.opencontainers.image.description="Application packaged by Bitnami" \
      org.opencontainers.image.ref.name="2.6.0-debian-11-r17" \
      org.opencontainers.image.source="https://github.com/bitnami/containers/tree/main/bitnami/harbor-notary-server" \
      org.opencontainers.image.title="harbor-notary-server" \
      org.opencontainers.image.vendor="VMware, Inc." \
      org.opencontainers.image.version="2.6.0"

ENV HOME="/" \
    OS_ARCH="${TARGETARCH:-amd64}" \
    OS_FLAVOUR="debian-11" \
    OS_NAME="linux"

COPY prebuildfs /
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
# Install required system packages and dependencies
RUN install_packages ca-certificates curl libc6 procps
RUN mkdir -p /tmp/bitnami/pkg/cache/ && cd /tmp/bitnami/pkg/cache/ && \
    for COMPONENT in \
      "harbor-notary-server-2.6.0-1-linux-${OS_ARCH}-debian-11" \
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

COPY rootfs /
RUN /opt/bitnami/scripts/harbor-notary-server/postunpack.sh
ENV APP_VERSION="2.6.0" \
    BITNAMI_APP_NAME="harbor-notary-server" \
    PATH="/opt/bitnami/harbor-notary-server/bin:/opt/bitnami/common/bin:$PATH" \
    SERVICE_NAME="notary_server"

VOLUME [ "/etc/notary" ]

EXPOSE 4443

USER 1001
ENTRYPOINT [ "/opt/bitnami/scripts/harbor-notary-server/entrypoint.sh" ]
CMD [ "/opt/bitnami/scripts/harbor-notary-server/run.sh" ]
