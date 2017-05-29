FROM debian:jessie

MAINTAINER Maksym Churkin <m.churkyn@globalgames.net>

RUN apt-get update && apt-get install -y \
    nginx

RUN echo "UTC" > /etc/timezone && dpkg-reconfigure -f noninteractive tzdata 

ADD nginx.conf /etc/nginx/
ADD drakeroll.com.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/drakeroll.com.conf /etc/nginx/sites-enabled/drakeroll.com.conf
RUN rm /etc/nginx/sites-enabled/default

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
