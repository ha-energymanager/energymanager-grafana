ARG BUILD_FROM
FROM ${BUILD_FROM}

RUN apk add --no-cache grafana bash jq curl dos2unix

# Ensure grafana user & dirs
RUN adduser -D -H -u 472 -s /sbin/nologin grafana || true \
 && mkdir -p /data/grafana /data/logs /data/plugins \
 && chown -R grafana:grafana /data

COPY rootfs /

# Normalize line endings + make scripts executable
RUN dos2unix /etc/cont-init.d/* /etc/services.d/grafana/* /usr/local/bin/prepare-provisioning || true \
 && chmod +x /etc/cont-init.d/* /etc/services.d/grafana/run /etc/services.d/grafana/finish /usr/local/bin/prepare-provisioning
