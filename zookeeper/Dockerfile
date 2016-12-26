FROM openjdk:8-jre-alpine

ENV ZOOKEEPER_MIRROR=https://ftp.fau.de/apache/
ENV ZOOKEEPER_VERSION=3.4.9
ENV ZOOKEEPER_RELEASE_ARCHIVE zookeeper-${ZOOKEEPER_VERSION}.tar.gz

LABEL name="zookeeper" version=${ZOOKEEPER_VERSION}

RUN apk update && apk add ca-certificates openssl bash
RUN mkdir /opt \
    && wget -O "/tmp/${ZOOKEEPER_RELEASE_ARCHIVE}" \
        "${ZOOKEEPER_MIRROR}/zookeeper/zookeeper-${ZOOKEEPER_VERSION}/${ZOOKEEPER_RELEASE_ARCHIVE}" \
    && tar xfz "/tmp/${ZOOKEEPER_RELEASE_ARCHIVE}" -C /opt \
    && rm "/tmp/${ZOOKEEPER_RELEASE_ARCHIVE}" \
    && mv /opt/zookeeper-${ZOOKEEPER_VERSION} /opt/zookeeper \
    && cp /opt/zookeeper/conf/zoo_sample.cfg /opt/zookeeper/conf/zoo.cfg \
    && mkdir -p /tmp/zookeeper

EXPOSE 2181 2888 3888

VOLUME ["/tmp/zookeeper"]

ENTRYPOINT ["/opt/zookeeper/bin/zkServer.sh"]
CMD ["start-foreground"]
