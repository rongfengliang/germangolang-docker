FROM golang:alpine as build
ENV VERSION=v1.7
WORKDIR /app
RUN apk update && apk add wget unzip build-base git bzr mercurial gcc 
COPY . /app
RUN go build

FROM alpine:latest
LABEL EMAIL="1141519465@qq.com"
LABEL AUTHOR="dalongrong"
WORKDIR /app
COPY --from=build /app/worker-gearman /usr/local/bin/worker-gearman
ENTRYPOINT ["worker-gearman"]