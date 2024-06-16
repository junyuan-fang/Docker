# 使用官方 Golang 镜像作为构建环境
FROM golang:1.16

WORKDIR /usr/src/app

EXPOSE 8080

COPY . .

ENV PORT=8080
ENV REQUEST_ORIGIN="http://localhost:5000"

RUN go build

CMD ./server