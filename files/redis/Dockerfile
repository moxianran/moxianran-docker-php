FROM redis:5.0.5
LABEL maintainer="453104950@qq.com"

# 设置时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN mkdir -p /usr/local/var/db/redis/
RUN chmod 777 -R /usr/local/var/db/redis/

#修改源
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
COPY ./sources.list /etc/apt/sources.list
