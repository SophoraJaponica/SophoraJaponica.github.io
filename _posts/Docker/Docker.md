---
layout:     post
title:      问题记录
subtitle:   V0.1
date:       2022-04-10
author:     Sam
header-img: img/post-bg-cook.jpg
catalog: true
tags:
- Docker
---

2022/4/3
记录容器启动失败
![avatar](../../img/docker/img1.png)
response from daemon: OCI runtime create failed: container with id exists:XXX:unknown

问题原因：
 (...)
解决方法
    1、执行
        `find / -name "containerID"`
    2、清除运行文件：
        `sudo rm -rf /var/run/docker/runtime-runc/moby/containerID/`
    3、重新启动
        docker start containerID