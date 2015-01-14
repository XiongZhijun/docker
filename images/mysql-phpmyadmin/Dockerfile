FROM bobxiong/ubuntu:latest
MAINTAINER Bob Xiong <hust.xzj@gmail.com>

RUN sudo apt-get install -y mysql-server nginx

RUN sudo apt-get install -y php5 php5-mysql php5-gd php5-fpm php5-cgi php-apc php5-curl \
    php5-intl php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming \
    php5-ps php5-pspell php5-recode php5-sqlite php5-tidy php5-xmlrpc php5-xsl \

RUN rm /etc/nginx/sites-available/default
ADD ./default /etc/nginx/sites-available/default

# mysql config
RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

RUN mysqld & \
	sleep 5; \
	printf y\\n\\n\\n1\\n | apt-get install -y phpmyadmin; \
	sleep 15; \
	mysqladmin -u root shutdown

# RUN sed -i "s#// \$cfg\['Servers'\]\[\$i\]\['AllowNoPassword'\] = TRUE;#\$cfg\['Servers'\]\[\$i\]\['AllowNoPassword'\] = TRUE;#g" /etc/phpmyadmin/config.inc.php 

RUN service mysql start &&\
    mysql -e "grant all privileges on *.* to 'root'@'%' identified by 'root';"&&\
    mysql -e "grant all privileges on *.* to 'root'@'localhost' identified by 'root';"

EXPOSE 80
EXPOSE 3306

CMD nginx & \
    mysqld_safe;
#CMD mysqld_safe & \
#	service apache2 start;