FROM ubuntu:14.04
MAINTAINER Bob Xiong <hust.xzj@gmail.com>

RUN dpkg-divert --local --rename --add /sbin/initctl
RUN ln -sf /bin/true /sbin/initctl

# Let the conatiner know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

RUN rm /etc/apt/sources.list
ADD ./sources.list /etc/apt/sources.list

RUN apt-get update
RUN apt-get -y install mysql-server

# mysql config
RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

RUN service mysql start &&\
    mysql -e "grant all privileges on *.* to 'root'@'%' identified by 'root';"&&\
    mysql -e "grant all privileges on *.* to 'root'@'localhost' identified by 'root';"

EXPOSE 3306

CMD ["/usr/bin/mysqld_safe"]
