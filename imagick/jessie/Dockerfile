from debian:jessie

RUN apt-get update
RUN apt-get -y install php5
RUN apt-get -y install imagemagick libmagick++-dev
RUN apt-get -y install autoconf g++ make php-pear php5-dev php5-dbg valgrind
RUN pecl install imagick && echo "extension=imagick.so" >> /etc/php5/cli/php.ini

CMD [ "bash", "-c", "valgrind --leak-check=full /usr/bin/php -S localhost:8085" ]
