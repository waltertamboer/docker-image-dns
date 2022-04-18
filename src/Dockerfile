FROM alpine:latest

ENV DOCKER_GEN_VERSION 0.8.4
ENV DOCKER_HOST unix:///var/run/docker.sock
ENV GATEWAY=172.17.42.1 \
    RESOLV_PATH=

RUN apk --no-cache add \
    dnsmasq \
    openssl \
 && wget -qO- https://github.com/nginx-proxy/docker-gen/releases/download/$DOCKER_GEN_VERSION/docker-gen-alpine-linux-amd64-$DOCKER_GEN_VERSION.tar.gz | tar xvz -C /usr/local/bin

COPY src/etc/. /etc
COPY src/usr/. /usr

EXPOSE 53/udp

VOLUME /var/run

ENTRYPOINT ["entrypoint"]

