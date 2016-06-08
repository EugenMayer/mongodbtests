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
RUN apt-get -y install libpcre3-dev libcurl4-openssl-dev libcurl4-openssl-dev pkg-config
RUN apt-get -y install autoconf g++ make php-pear php5-dev php5-dbg valgrind
# extra packages to imitate problematic stack
RUN apt-get -y install libsasl2-dev libmemcached-dev
# memcached-dev
RUN pecl install mongodb && echo "extension=mongodb.so" >> /etc/php5/cli/php.ini

CMD [ "bash", "-c", "valgrind --leak-check=full /usr/bin/php -S localhost:8085" ]
