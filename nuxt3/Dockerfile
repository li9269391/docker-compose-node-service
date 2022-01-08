FROM node:14.18.0-alpine

# LABEL maintainer="hd"
# LABEL description="Nuxt3 Demo"

# RUN apk --update add tzdata \
#   && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
#   && echo "Asia/Shanghai" > /etc/timezone \
#   && apk del tzdata

# RUN echo "Asia/Shanghai" > /etc/timezone

# ARG NODE_ENV

# 注：nuxtjs3 需要的环境 HOST 变量，否则只能通过 localhost 访问。另外 eggjs\express\nuxt2 则没有这个问题，一般运维部署建议0.0.0.0
# 这里选择在 docker-compose 中配置 environment HOST
# ENV HOST 0.0.0.0


# ENV NODE_ENV ${NODE_ENV}

# 在容器中创建一个目录
RUN mkdir -p /data/wwww/app-server

# 定位到容器的工作目录
WORKDIR /data/wwww/app-server

COPY package.json /data/wwww/app-server/package.json

# 安装依赖
RUN yarn install

# 构建生产包
RUN yarn build

COPY . /data/wwww/app-server/

EXPOSE 3000

ENTRYPOINT ["yarn" ,"start"]
