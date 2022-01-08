# docker-compose-node-service

用 docker-compose 部署单机多服务负载均衡

> 确保部署之前，服务器已安装好 docker 和 docker-compose

#### 部署

进入项目目录

```sh
$ cd ./express
```

构建镜像

```sh
$ docker-compose build --force-rm
```

启动服务

```sh
$ docker-compose up --scale node=5
```

访问

```sh
http://你的服务器IP地址:7000
```

一切都正常的话，访问页面，每次刷新页面返回的内容可以看到多个服务 ip，说明负载均衡生效。目前的扩展是单机环境下的 scale，无论将 service 扩展到多少，只能限制在单机环境下。但是一台服务器的资源是有限的，那么如何扩展多台服务器？那么就是需要使用 swarm 技术了
