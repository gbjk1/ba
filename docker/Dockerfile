FROM alpine:latest

RUN apk update && apk upgrade && apk add nodejs npm

RUN addgroup -g 1000 mygroup && adduser -u 1000 -D -G mygroup myuser

COPY --chown=1000:1000 ./server.js /app/

USER myuser

CMD ["node", "/app/server.js"]
