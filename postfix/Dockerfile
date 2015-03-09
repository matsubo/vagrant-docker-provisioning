FROM debian:stable
MAINTAINER Yuki Matsukura "matsubokkuri@gmail.com"

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -y update

run apt-get install -q -y postfix
run apt-get install -q -y rsyslog

# update configuration
run sed -i -e '/mynetworks/c\mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 172.16.0.0/12 192.168.0.0/16 10.0.0.0/8' /etc/postfix/main.cf


expose 25

cmd ["sh", "-c", "service rsyslog start ; service postfix start ; tail -F /var/log/mail.log"]


