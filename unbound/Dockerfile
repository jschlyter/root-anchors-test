FROM docker.io/fedora:latest

RUN dnf -y update && dnf -y install unbound bind-utils

ADD entrypoint.sh /

#ENTRYPOINT /usr/sbin/unbound -d
ENTRYPOINT sh /entrypoint.sh
