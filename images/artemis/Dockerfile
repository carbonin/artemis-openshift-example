FROM openjdk:8-jre-alpine

ARG REF

ENV ARTEMIS_HOME=/opt/artemis \
    ARTEMIS_INSTANCE=/var/lib/artemis

VOLUME ${ARTEMIS_INSTANCE}

EXPOSE 61613

RUN mkdir -p ${ARTEMIS_HOME}
COPY apache-artemis-${REF} "${ARTEMIS_HOME}/"
COPY start_artemis /usr/bin

ENTRYPOINT [ "start_artemis" ]
