FROM debian:stable
MAINTAINER Yuki Matsukura "matsubokkuri@gmail.com"

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -y update
RUN apt-get install -y -q redis-server

EXPOSE      6379
ENTRYPOINT  ["/usr/bin/redis-server"]

