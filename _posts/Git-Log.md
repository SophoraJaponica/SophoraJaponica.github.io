1.（空仓库）创建完空仓库就将本地项目关联到远程
    1.1.如果本地项目已经通过git管理：
        直接通过git remote add origin (仓库地址) 关联
        => git push -u origin master 推送代码上去，就完事了。
    1.2.本地项目未通过git管理：
        git init(将项目通过git初始化)
        => git add .(添加所有修改到暂存区)
        => git commit -m "first commit remark"(提交commit)
        => git remote add origin (仓库地址)
        => git push -u origin master(推送到远程github)


2.（非空仓库）创建完非空仓库就将本地项目关联到远程
    2.1.远程非空仓库的关联，就要涉及到2个不同项目的关联了；得先将远程的代码合并下来，才能提交；
    我们先假设项目已经通过git管理了。缺少关联push远程仓库的步骤讲：
        2.1.1.关联远程仓库：git remote add origin (仓库地址)
        2.1.2.git pull origin master --allow-unrelated-histories（意思是2个不同项目的没关联提交允许拉取合并）
        2.1.3.git push origin master（push成功，完工...）
    注意：
    针对非空仓库的关联：可能有同学会问为什么不直接git pull origin master呢？是可以的，但是2个不同项目的不同提交记录并没有关联，
    最后git push origin master是不会成功的。提醒如下图：
    非空仓库的关联，pull是可以成功的，但是push是不行
    push不成功 - 这时候先通过git pull origin master --allow-unrelated-histories拉取下，再push
    出现(non-fast-forward)的根本原因是repository已经存在项目且不是你本人提交（但是git只认地址），你commit的项目和远程repository不一样。