# Multi-arch build support via Home Assistant build system
ARG BUILD_FROM
FROM ${BUILD_FROM}

# Default to Alpine base if BUILD_FROM not provided by HA builder
# (HA will inject a suitable base for the target arch.)

# Install Grafana and helpers
RUN apk add --no-cache grafana bash jq

# Copy root filesystem
COPY rootfs /

# Permissions
RUN chmod +x \
/etc/cont-init.d/* \
/etc/services.d/grafana/run \
/usr/local/bin/prepare-provisioning

EXPOSE 3000
