# volume

**提供独立于容器之外的持久化存储，容器之间的数据共享**

**第一种形式**
```shell
docker run -p 80:80 -d --name nginx -v /usr/share/html nginx

docker inspect nginx
```
/usr/share/html 是容器内部的目录
docker inspect nginx 检查容器信息，其中 Mounts 中有挂载相关信息
```json
...
"Mounts":[
    {
        "name": "bae2ees....",
        "Source": "/var/lib/docker/volumes/bae2ees..../_data",
        "Destination": "/usr/share/nginx/html",
        ...
    }
]
...
```
这种形式会生成一个默认的目录(Source)跟容器中的目录(Destination)进行挂载
如果是Mac，是不能直接访问到Source目录的，因为Mac有一层虚拟层，再虚拟层运行了一个alpha主机，在主机中运行docker，通过一下命令进去，用root登陆
```shell
screen ~/Library/Containers/com.docer.docker/Data/com.docker.driver.amd64-linux/tty
```

**第二种形式**
```shell
docker run -p 80:80 -d -v $PWD/html:/usr/share/nginx/html nginx
```
本地的目录挂在到容器中

**第三种形式**
```shell
docker run --volumes-from
```

```shell
docker create -v $PWD/data:/var/mydata --name data_container ubuntu

docker run -it --volumes-from data_container ubuntu

//在第二个容器中 mount 命令查看
...
osxfs on /var/mydata type tmpfs ...
...
```