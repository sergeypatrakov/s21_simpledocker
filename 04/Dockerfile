FROM nginx:latest

WORKDIR /app

COPY ./apt.sh /app/

RUN bash apt.sh

COPY ./server.c /app/
COPY ./start.sh /app/
COPY ./nginx/nginx.conf /etc/nginx/

EXPOSE 8080

CMD ["bash", "./start.sh"]