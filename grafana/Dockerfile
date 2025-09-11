ARG BUILD_FROM
FROM ${BUILD_FROM}

RUN apk add --no-cache grafana bash jq bashio

RUN adduser -D -H -u 472 -s /sbin/nologin grafana || true

RUN mkdir -p /data/grafana /data/logs /data/plugins \
 && chown -R grafana:grafana /data

COPY rootfs /

RUN chmod +x \
    /etc/cont-init.d/* \
    /etc/services.d/grafana/run \
    /etc/services.d/grafana/finish \
    /usr/local/bin/prepare-provisioning

EXPOSE 3000
