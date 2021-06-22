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



