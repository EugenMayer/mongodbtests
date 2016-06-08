from debian:jessie

RUN apt-get update
RUN apt-get -y install php5 valgrind libsasl2-dev libmemcached-dev 
RUN apt-get -y install php5-dev libcurl4-openssl-dev libcurl4-openssl-dev pkg-config
RUN pecl install mongodb && echo "extension=mongodb.so" >> /etc/php5/cli/php.ini

CMD [ "bash", "-c", "valgrind --leak-check=full /usr/bin/php -S localhost:8085" ]
