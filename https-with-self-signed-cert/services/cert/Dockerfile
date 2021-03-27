# openssl で自己証明証明書を作成するためのイメージを定義する
FROM alpine:3

WORKDIR /app

RUN apk update && \
  apk add --no-cache openssl && \
  rm /var/cache/apk/*

COPY ./bin/generate-cert.sh /usr/local/bin/

CMD ["/usr/local/bin/generate-cert.sh"]
