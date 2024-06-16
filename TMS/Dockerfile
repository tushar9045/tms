FROM ubuntu
COPY ./tms /var/www/html/tms
RUN apt-get update && \
    apt-get install -y nginx mysql-client php-fpm wget php-mysql  curl && \
    apt-get clean && \
    rm /etc/nginx/sites-enabled/default && \
    rm -rf /var/www/html/tms/TMS/Dockerfile


COPY nginx.conf /etc/nginx/sites-enabled/

EXPOSE 80 443

#CMD ["nginx", "-g", "daemon off;"]
CMD service php8.3-fpm start && nginx -g "daemon off;"
