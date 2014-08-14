# Installing MYSQL Percona

FROM ubuntu:14.04
RUN apt-key adv --keyserver keys.gnupg.net --recv-keys 1C4CBDCDCD2EFD2A
RUN sh -c 'echo "deb http://repo.percona.com/apt trusty main" >> /etc/apt/sources.list'
RUN sh -c 'echo "deb-src http://repo.percona.com/apt trusty main" >> /etc/apt/sources.list'
RUN apt-get update
RUN apt-get -y install percona-server-server-5.5 percona-server-client-5.5
RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

RUN apt-get -y install supervisor
ADD supervisord.conf /etc/supervisord.conf

ADD start.sh /start.sh
RUN chmod 755 /start.sh

EXPOSE 3306

VOLUME ["~/Desktop/Chamba/docker/nginx/www/"]

CMD ["/bin/bash", "/start.sh"]
