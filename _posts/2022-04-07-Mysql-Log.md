---
layout:     post
title:      Mysql配置问题
subtitle:   v0.1版
date:       2022-04-10
author:     Sam Li
header-img: img/post-bg-cook.jpg
catalog: true
tags:
- Mysql
---

1.重置Mysql密码
    # 进入容器
    docker exec -it mysql bash
    # 设置跳过权限表的加载
    # 警告：这就意味着任何用户都能登陆进来，并进行任何操做，至关不安全。
    echo "skip-grant-tables" >> /etc/mysql/conf.d/docker.cnf
    # 退出容器
    exit
    # 重启容器
    docker restart mysql
    # 再次进入容器
    docker exec -it mysql bash
    # 登陆 mysql（无需密码）
    mysql -uroot
    # 更新权限
    flush privileges;
    # 修改密码
    alter user 'root'@'localhost' identified by '778899';
    # 退出mysql
    exit
    # 替换掉刚才加的跳过权限表的加载参数
    sed -i "s/skip-grant-tables/ /" /etc/mysql/conf.d/docker.cnf
    # 退出容器
    exit
    # 重启容器
    docker restart mysql

2.Mysql创建账户
    #创建账号
    create user sentao@'%' identified by '密码';
    #授权
    grant all on *.* to sentao@'%';
    flush privileges;
补充：
    #修改密码
    alter user 'sentao'@'%' identified by '778899';
    //%或localhost或170.0.0.1
    flush privileges;
    #收回权限
    revoke all ON *.*  FROM sentao@'%';
    flush privileges;
    #查询所有用户
    SELECT User, Host FROM mysql.user;