# Dockerfile

**用来构建自己的image**

**1. 新建Dockerfile文件**
```shell
touch Dockerfile
```

**2. 编写Dockerfile文件**
>FROM base image  
RUN 执行命令  
ADD 添加文件  
COPY 拷贝文件  
CMD 执行命令  
EXPOSE 暴露端口  
WORKDIR 指定路径  
MAINTAINER 维护者  
ENV 设定环境变量  
ENTRYPOINT 容器入口  
USER 指定用户  
VOLUME mount point  

```shell
FROM alpine:latest
MAINTAINER zhangjl 
CMD echo "hello docker"
```

**3. 构建image**
```shell
docker build -t hello_world ./
```

**4. 运行**
```shell
docker run hello_docker
```