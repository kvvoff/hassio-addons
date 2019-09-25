ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

RUN echo "http://nl.alpinelinux.org/alpine/edge/main/" >> /etc/apk/repositories
RUN echo "http://nl.alpinelinux.org/alpine/edge/testing/" >> /etc/apk/repositories
RUN apk add nut jq --update-cache

RUN mkdir /var/run/nut
RUN chown root:nut /var/run/nut
RUN chmod 770 /var/run/nut

# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]

# Labels
LABEL \
    io.hass.name="Network UPS Tools" \
    io.hass.description="Manage battery backup (UPS) devices" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Dale Higgs <dale3h@addons.community>" \
    org.label-schema.description="Manage battery backup (UPS) devices" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Network UPS Tools" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://community.home-assistant.io/" \
    org.label-schema.usage="https://github.com/hassio-addons/addon-nut/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/hassio-addons/addon-nut" \
    org.label-schema.vendor="Community Hass.io Addons"
