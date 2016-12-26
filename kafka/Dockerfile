FROM openjdk:8-jre-alpine

ENV KAFKA_MIRROR=https://ftp.fau.de/apache/
ENV KAFKA_VERSION=0.10.1.0 KAFKA_SCALA_VERSION=2.11
ENV KAFKA_RELEASE_ARCHIVE kafka_${KAFKA_SCALA_VERSION}-${KAFKA_VERSION}.tgz

LABEL name="kafka" version=${KAFKA_VERSION}

RUN apk update && apk add ca-certificates openssl bash
RUN mkdir /opt \
    && wget -O "/tmp/${KAFKA_RELEASE_ARCHIVE}" \
        "${KAFKA_MIRROR}/kafka/${KAFKA_VERSION}/${KAFKA_RELEASE_ARCHIVE}" \
    && tar xfz "/tmp/${KAFKA_RELEASE_ARCHIVE}" -C /opt \
    && rm "/tmp/${KAFKA_RELEASE_ARCHIVE}" \
    && mv /opt/kafka_${KAFKA_SCALA_VERSION}-${KAFKA_VERSION} /opt/kafka \
    && chmod +x /opt/kafka/bin/*

ENV PATH="/opt/kafka/bin:${PATH}"

ADD server.properties /opt/kafka/config/server.properties

EXPOSE 9092

VOLUME ["/tmp/kafka-logs"]

CMD ["kafka-server-start.sh", "/opt/kafka/config/server.properties"]
