FROM bitnami/minideb:stretch
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ca-certificates curl procps unzip wget
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/rabbitmq-exporter-0.29.0-1-linux-amd64-debian-9.tar.gz && \
    echo "0c601d41a4de4518970ec96bba105c23d0d633fa3c87a99ea91e607f18bd50c5  /tmp/bitnami/pkg/cache/rabbitmq-exporter-0.29.0-1-linux-amd64-debian-9.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/rabbitmq-exporter-0.29.0-1-linux-amd64-debian-9.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/rabbitmq-exporter-0.29.0-1-linux-amd64-debian-9.tar.gz

ENV BITNAMI_APP_NAME="rabbitmq-exporter" \
    BITNAMI_IMAGE_VERSION="0.29.0-debian-9-r112" \
    PATH="/opt/bitnami/rabbitmq-exporter/bin:$PATH"

EXPOSE 9090

WORKDIR /opt/bitnami/rabbitmq-exporter
USER 1001
ENTRYPOINT [ "rabbitmq_exporter" ]
