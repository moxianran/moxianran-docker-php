From nginx:1.15.6
LABEL maintainer="453104950@qq.com"

# 设置时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

#修改源
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
COPY ./sources.list /etc/apt/sources.list