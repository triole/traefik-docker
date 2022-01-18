FROM alpine:latest

COPY ./bin/* /usr/bin/

LABEL traefik.enable=true
LABEL traefik.http.routers.tfk.tls=false
LABEL traefik.http.routers.tfk.entrypoints=web
LABEL traefik.http.routers.tfk.rule="Host(`tfk.localhost`)"
LABEL traefik.http.routers.tfk.service=api@internal
LABEL traefik.http.routers.tfk.middlewares=escience_ips_only@file

HEALTHCHECK --interval=5s --timeout=5s --retries=3 \
    CMD pgrep traefik

CMD ["/usr/bin/traefik", "--configfile", "/vol/conf/conf.toml"]
