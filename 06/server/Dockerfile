FROM nginx:latest

USER root

WORKDIR /app

COPY ./server.c /app/
COPY ./start.sh /app/
COPY ./nginx/nginx.conf /etc/nginx/

RUN apt-get update; \
    apt-get upgrade; \
    apt-get install -y gcc spawn-fcgi libfcgi-dev; \
    chown -R nginx:nginx /etc/nginx/nginx.conf; \
    chown -R nginx:nginx /var/cache/nginx; \
    chown -R nginx:nginx /app; \
    touch /var/run/nginx.pid; \
    chown -R nginx:nginx /var/run/nginx.pid; \
    rm -rf /var/lib/apt/lists/*; \
    chmod u-s /usr/bin/su; \
    chmod u-s /usr/bin/mount; \
    chmod u-s /usr/bin/gpasswd; \
    chmod g-s /usr/bin/chage; \
    chmod g-s /usr/sbin/unix_chkpwd; \
    chmod g-s /usr/bin/expiry; \
    chmod u-s /usr/bin/chfn; \
    chmod u-s /usr/bin/chsh; \
    chmod u-s /usr/bin/passwd; \
    chmod u-s /usr/bin/newgrp; \
    chmod u-s /usr/bin/umount; \
    chmod g-s /usr/bin/wall

USER nginx

ENTRYPOINT ["sh", "./start.sh"]

HEALTHCHECK --interval=30s --start-period=3s --timeout=5s CMD curl -f http://localhost:81 || exit 1