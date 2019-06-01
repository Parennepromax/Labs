FROM debian
MAINTAINER Sergey Ermolaev <sergej.ermolaev2010@yandex.ru>
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && \
    apt-get -y upgrade && \
    apt -y install nginx && \
    apt-get clean && \
    rm -rf /var/www/* && \ 
    mkdir -p /var/www/yandex.com/img && \
    chmod -R 754 /var/www/yandex.com/ && \
    useradd admin && \
    usermod -aG admin admin && \
    chown -R admin:admin /var/www/yandex.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/yandex.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user admin/g' /etc/nginx/nginx.conf
ADD index.html /var/www/yandex.com/
ADD img.jpg /var/www/yandex.com/img/
CMD ["nginx", "-g", "daemon off;"]
