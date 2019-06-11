FROM redis:5.0
LABEL maintainer="453104950@qq.com"

# 设置时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

Run mkdir -p /usr/local/var/db/redis/