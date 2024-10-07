FROM debian:bullseye
RUN apt update -y
RUN apt upgrade -y
RUN apt-get install mariadb-server -y mariadb-client && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/run/mysqld \
&& chown -R mysql:mysql /var/run/mysqld \
&& chmod 777 /var/run/mysqld

EXPOSE 3306

COPY tools/script.sh usr/local/bin/
#COPY ./conf/wordpress.sql /usr/local/bin/

RUN chmod +x /usr/local/bin/script.sh
#RUN chmod +x /usr/local/bin/wordpress.sql

ENTRYPOINT ["/usr/local/bin/script.sh"]

COPY conf/50-server.cnf /etc/mariadb.conf.d/50-server.cnf
CMD ["mysqld", "--bind-adress=0.0.0.0"]
