FROM alpine:latest

ARG TIMEZONE

COPY ./bin/* /usr/bin/

LABEL traefik.enable=true
LABEL traefik.http.routers.tfk.tls=false
LABEL traefik.http.routers.tfk.entrypoints=web
LABEL traefik.http.routers.tfk.rule="Host(`tfk.localhost`) || Host(`tfk.alma002.lin.gw`)"
LABEL traefik.http.routers.tfk.service=api@internal
# LABEL traefik.http.routers.tfk.middlewares=escience_ips_only@file

RUN apk --update add tzdata \
 && cp "/usr/share/zoneinfo/${TIMEZONE}" "/etc/localtime" \
 && echo "${TIMEZONE}" > "/etc/timezone" \
 && apk del tzdata \
 && rm -rf /var/cache/apk/*

HEALTHCHECK --interval=5s --timeout=5s --retries=3 \
    CMD pgrep traefik

CMD ["/usr/bin/traefik", "--configfile", "/vol/conf/conf.toml"]
