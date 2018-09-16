# docker-nginx

### 构建镜像
docker build -t "qq1060656096/nginx:1.13.4" 1.13.4
### 启动容器
docker run -tid -p 8080:80 --name simple-nginx qq1060656096/nginx:1.13.4 /usr/local/nginx/sbin/nginx -g "daemon off;" 
### 进入容器
docker exec -ti simple-nginx /bin/bash
### 查看容器nginx状态
docker exec -ti simple-nginx /bin/bash -c "ps -ef | grep nginx"

**nginx目录**

```
/usr/local/nginx
/usr/local/nginx/conf
/usr/local/nginx/html
/usr/local/nginx/logs
/usr/local/nginx/sbin
```

### 使用

```sh
# 拉去镜像
docker pull qq1060656096/nginx:1.13.4

# 启动容器
docker run -tid -p 8080:80 --name simple-nginx qq1060656096/nginx:1.13.4

#进入容器
docker exec -ti simple-nginx /bin/bash

查看容器nginx状态
docker exec -i simple-nginx /bin/bash -c "ps -ef | grep nginx"

# 删除镜像
docker rm -f simple-nginx

#查看镜像
docker ps


```