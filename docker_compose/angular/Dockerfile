FROM alpine

RUN apk upgrade
RUN apk add nodejs npm
RUN npm install -y -g @angular/cli

# 设置时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# ng new 指令需要在项目目录中才生效，因此需设定工作目录为挂在目录
WORKDIR /opt/

CMD ["/bin/sh"]

# 使用容器创建项目
# docker run --rm -v /opt/ng-reader/stories-panel:/opt/ nodejs:v1 /usr/bin/ng new stories-panel

# 运行应用
# docker run --rm -v /opt/ng-reader/stories-panel:/opt/ -p 4200:4200 --name ng-reader nodejs:v1 /usr/bin/ng serve --host 0.0.0.0