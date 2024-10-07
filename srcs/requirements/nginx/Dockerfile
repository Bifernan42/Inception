FROM debian:bullseye
RUN apt update
RUN apt upgrade -y
RUN apt install nginx -y
RUN mkdir -p /etc/nginx/ssl
RUN apt-get install openssl -y
RUN openssl req -x509 -nodes -out /etc/nginx/ssl/inception.crt -keyout /etc/nginx/ssl/inception.key -subj "/C=FR/ST=IDF/L=Paris/O=42/OU=42/CN=bifernan.42.fr/UID=login"
RUN mkdir -p /var/run/nginx
COPY conf/nginx.conf /etc/nginx/nginx.conf

#set permissions for the web root directory
RUN chmod 755 /var/www/html
RUN chown -R www-data:www-data /var/www/html

#run nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
