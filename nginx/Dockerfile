# INSTALLING NGINX & PHP-FPM

FROM ubuntu:14.04
MAINTAINER Studio Fuzed
RUN apt-get update
RUN apt-get -y install nginx
RUN sed -i -e"s/keepalive_timeout\s*65/keepalive_timeout 2/" /etc/nginx/nginx.conf
RUN sed -i -e"s/keepalive_timeout 2/keepalive_timeout 2;\n\tclient_max_body_size 100m/" /etc/nginx/nginx.conf
RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN apt-get -y install php5-cli php5-common php5-mysql php5-gd php5-dev php5-fpm php5-cgi php5-memcache
RUN apt-get -y install supervisor
ADD supervisord.conf /etc/supervisord.conf

ADD nginx-site.conf /etc/nginx/sites-available/default
ADD www /usr/share/nginx/www
RUN chown -R www-data:www-data /usr/share/nginx/www


ADD start.sh /start.sh
RUN chmod 755 /start.sh

# port expose
#EXPOSE 3306
EXPOSE 80

CMD ["/bin/bash", "/start.sh"]
