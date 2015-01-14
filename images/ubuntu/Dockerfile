FROM ubuntu:14.04
MAINTAINER Bob Xiong <hust.xzj@gmail.com>

RUN dpkg-divert --local --rename --add /sbin/initctl
RUN ln -sf /bin/true /sbin/initctl

# Let the conatiner know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

RUN rm /etc/apt/sources.list
ADD ./sources.list /etc/apt/sources.list

RUN apt-get update
RUN apt-get upgrade
