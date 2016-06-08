from debian:wheezy

RUN apt-get update
RUN apt-get install -y curl
# dotdeb
RUN curl https://www.dotdeb.org/dotdeb.gpg -o /tmp/dotdeb.gpg \
  && apt-key add /tmp/dotdeb.gpg && rm /tmp/dotdeb.gpg
ADD https://www.dotdeb.org/dotdeb.gpg /dotdeb.gpg
RUN apt-key add dotdeb.gpg && apt-get update

RUN echo "deb http://dotdeb.netmirror.org/ wheezy-php55 all\ndeb-src http://dotdeb.netmirror.org/ wheezy-php55 all" >> /etc/apt/sources.list.d/dotdebphp55.list
RUN apt-get update
RUN apt-get -y install php5
RUN apt-get -y install imagemagick libmagick++-dev
RUN apt-get -y install autoconf g++ make php-pear php5-dev php5-dbg valgrind
RUN pecl install imagick && echo "extension=imagick.so" >> /etc/php5/cli/php.ini

CMD [ "bash", "-c", "valgrind --leak-check=full /usr/bin/php -S localhost:8085" ]
