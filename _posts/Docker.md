1.docker进入容器需要3个命令
    第1个docker run -itd运行一个容器；
    第2个docker ps查看容器id；
    第3个使用docker exec -it容器id /bin/bash进入容器。”


2.记录容器启动失败
![avatar](/img/Docker/img1.png)
response from daemon: OCI runtime create failed: container with id exists:XXX:unknown
问题原因：
解决方法
    1、执行
        `find / -name "XXX"`
    2、清除运行文件：
        `sudo rm -rf /var/run/docker/runtime-runc/moby/XXX/`
    3、重新启动
        docker start 8adf

