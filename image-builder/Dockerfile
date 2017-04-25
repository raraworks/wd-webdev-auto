FROM ubuntu:latest
LABEL maintainer "andis.cirulis@whitedigital.eu"

#some general stuff
RUN apt-get update \
&& apt-get install -y vim \
&& apt-get install -y nginx

#lets use seperate command for now to speed up builds
RUN apt-get install -y php-fpm \
    && apt-get install -y php-mysql php-mbstring php-gd php-bcmath php-zip php-xml php-curl php-intl php-memcached


# #Expose http, https
EXPOSE 80 443

# # forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
 	&& ln -sf /dev/stderr /var/log/nginx/error.log

WORKDIR /root
ADD startup.sh ./
RUN chmod a+x startup.sh

ADD php.ini /etc/php/7.0/fpm/php.ini

CMD ["/bin/bash"]
#ENTRYPOINT  ["bash"]