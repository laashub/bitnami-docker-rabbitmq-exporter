FROM bitnami/minideb:buster
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ca-certificates curl procps sudo unzip wget
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/rabbitmq-exporter-0.29.0-0-linux-amd64-debian-10.tar.gz && \
    echo "c419bc5dd62a7007526015d0b5aa9b27497ad00e9f15eb4e3364a1e1a57bb18d  /tmp/bitnami/pkg/cache/rabbitmq-exporter-0.29.0-0-linux-amd64-debian-10.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/rabbitmq-exporter-0.29.0-0-linux-amd64-debian-10.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/rabbitmq-exporter-0.29.0-0-linux-amd64-debian-10.tar.gz
RUN apt-get update && apt-get upgrade -y && \
    rm -r /var/lib/apt/lists /var/cache/apt/archives

ENV BITNAMI_APP_NAME="rabbitmq-exporter" \
    BITNAMI_IMAGE_VERSION="0.29.0-debian-10-r39" \
    PATH="/opt/bitnami/rabbitmq-exporter/bin:$PATH"

EXPOSE 9090

WORKDIR /opt/bitnami/rabbitmq-exporter
USER 1001
ENTRYPOINT [ "rabbitmq_exporter" ]
