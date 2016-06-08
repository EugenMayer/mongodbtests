from debian:jessie

RUN apt-get update
RUN apt-get -y install php5
RUN apt-get -y install libpcre3-dev libcurl4-openssl-dev libcurl4-openssl-dev pkg-config
RUN apt-get -y install autoconf g++ make php-pear php5-dev php5-dbg valgrind
# thats the cause of the segfaults!
RUN apt-get -y install libsasl2-dev libsasl2-modules-gssapi-mit

RUN pecl install mongodb && echo "extension=mongodb.so" >> /etc/php5/cli/php.ini

CMD [ "bash", "-c", "valgrind --leak-check=full /usr/bin/php -S localhost:8085" ]
