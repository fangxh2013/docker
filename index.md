# docker 笔记

### Docker — 从入门到实践

点击[github地址](https://github.com/yeasy/docker_practice)

[github在线阅读](https://github.com/yeasy/docker_practice/blob/master/SUMMARY.md)

[gitbook在线阅读](https://yeasy.gitbook.io/docker_practice/)

[docker部署离线阅读方法](https://github.com/yeasy/docker_practice/wiki/%E7%A6%BB%E7%BA%BF%E9%98%85%E8%AF%BB%E5%8A%9F%E8%83%BD%E8%AF%A6%E8%A7%A3)



#### Vuepress 格式

```shell
docker pull ccr.ccs.tencentyun.com/dockerpracticesig/docker_practice:vuepress

# 国内仓库
docker run -it --rm -p 4000:80 ccr.ccs.tencentyun.com/dockerpracticesig/docker_practice:vuepress

# docker hub
#docker run -it --rm -p 4000:80 dockerpracticesig/docker_practice:vuepress

```

#### 或者：GitBook 格式

```shell
docker pull ccr.ccs.tencentyun.com/dockerpracticesig/docker_practice

# 国内仓库
docker run -it --rm -p 4000:80 ccr.ccs.tencentyun.com/dockerpracticesig/docker_practice

# docker hub
#docker run -it --rm -p 4000:80 dockerpracticesig/docker_practice

```

#### 打开浏览器阅读

打开浏览器，在地址栏输入 `127.0.0.1:4000` 即可开始阅读。

### 常用操作

进入容器：

```shell
docker exec -it <container ID> /bin/bash
```

删除：

```shell
#To clear containers:
docker rm -f $(docker ps -a -q)
docker rm -fv $(docker ps -aq)

#To clear images:
docker rmi -f $(docker images -a -q)

#To clear volumes:
docker volume rm $(docker volume ls -q)

#To clear networks:
docker network rm $(docker network ls | tail -n+2 | awk '{if($2 !~ /bridge|none|host/){ print $1 }}')
```

run:

```shell
docker run --rm -itd -v /home/ubuntu/src/wwwroot/develop/dingTalk/:/var/www/html -p 8088:80 php-apache:latest

docker run --rm -itd -v /home/ubuntu/src/wwwroot/develop/ding-talk/:/var/www/html -p 8090:80 dingtalk-api:1.0
```

宿主机执行docker下的任务:

```shell
docker exec <container ID> /usr/local/bin/php /var/www/html/ding-talk/yii day/index  >> /root/cron.log
*/10 * * * * docker exec <container ID> /usr/local/bin/php /var/www/html/ding-talk/yii day/pull-data  >> /root/pull-data.log
*/10 * * * * docker exec <container ID> /usr/local/bin/php /var/www/html/ding-talk/yii day/update-process-instance  >> /root/update_process_instance.log

docker exec <container ID> /usr/local/bin/php /var/www/html/ding-talk/yii dingtalk/index

docker exec <container ID> /usr/local/bin/php /var/www/html/ding-talk/yii process-instance/index
```

- Common Docker commands
  - `docker images` - list available images
  - `docker ps` - list running containers
  - `docker ps -a` - list all containters
  - `docker attach {containerId}` - reconnect/attach to a running container
  - `docker run -i -t 370feea6a7aa /bin/bash` - start a new container from an image (id = [370feea6a7aa](https://bitbucket.org/fangxiaohui/feature-extraction2/commits/370feea6a7aa))
  - `docker restart 370feea6a7aa` - restart a container
  - `docker stop 370feea6a7aa` - stop a container
  - `docker ps -a -q --filter="name=<containerName>"` - stop all containers by image name
  - `docker rm $(docker stop $(docker ps -a -q --filter ancestor=f558637854ca --format="{{.ID}}"))` - remove all container of a image
  - `docker run -p 8080:8080 -td test02` - start a new container with port mapping
  - `docker exec -it d595320f96a1 /bin/bash` - start a new terminal
  - `docker run -dit --restart unless-stopped/on-failure/always dl-docker:cpu` - start a container with auto restart policy
  - `docker update --restart=no my-container` - remove a container's restart policy

run following command to build image in the root directory of this project：

```shell
docker build -t imagename:tag -f Dockerfile .  
```

