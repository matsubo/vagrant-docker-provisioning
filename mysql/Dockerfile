FROM debian:stable
MAINTAINER Yuki Matsukura "matsubokkuri@gmail.com"

ENV DEBIAN_FRONTEND noninteractive

# REPOS
RUN apt-get -y update
RUN apt-get install procps -yy

RUN apt-get install -y -q  mysql-server

ADD run /usr/local/bin/run
RUN chmod +x /usr/local/bin/run

VOLUME ["/var/lib/mysql"]
VOLUME ["/run/mysqld"]

EXPOSE 3306
CMD ["/usr/local/bin/run"]

