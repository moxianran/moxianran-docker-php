From php:7.1-fpm
LABEL maintainer="453104950@qq.com"
MAINTAINER moxianran "453104950@qq.com"

# 设置时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update
RUN apt-get install -y git
RUN apt-get install -y libfreetype6-dev
RUN apt-get install -y libjpeg62-turbo-dev
RUN apt-get install -y libpng-dev

RUN docker-php-ext-install zip \
&& docker-php-ext-install pdo_mysql \
&& docker-php-ext-install opcache \
&& docker-php-ext-install mysqli \
&& rm -r /var/lib/apt/lists/*

# 复制扩展包
COPY ./pkg/redis.tgz /home/redis.tgz
COPY ./pkg/mongodb.tgz /home/mongodb.tgz
COPY ./pkg/swoole.tgz /home/swoole.tgz
COPY ./pkg/librdkafka.tar.gz /home/librdkafka.tar.gz
COPY ./pkg/rdkafka.tgz /home/rdkafka.tgz

# 安装扩展
RUN cd /home \
&& tar -zxvf librdkafka.tar.gz \
&& rm -r librdkafka.tar.gz \
&& mv librdkafka-* librdkafka \
&& cd librdkafka \
&& ./configure  && make && make install

RUN pecl install /home/rdkafka.tgz && echo "extension=rdkafka.so" > /usr/local/etc/php/conf.d/rdkafka.ini
RUN pecl install /home/redis.tgz && echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini
RUN pecl install /home/mongodb.tgz && echo "extension=mongodb.so" > /usr/local/etc/php/conf.d/mongodb.ini
RUN pecl install /home/swoole.tgz && echo "extension=swoole.so" > /usr/local/etc/php/conf.d/swoole.ini

# 安装Composer
ENV COMPOSER_HOME /root/composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
ENV PATH $COMPOSER_HOME/vendor/bin:$PATH

RUN rm -f /home/redis.tgz \
&& rm -f /home/mongodb.tgz \
&& rm -f /home/swoole.tgz

# 工作目录
WORKDIR /data/data

# 权限
RUN usermod -u 1000 www-data