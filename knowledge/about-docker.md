### Docker相关

 1. 创建Dockerfile
 2. 使用 Dockerfile 文件，通过 docker build 命令来构建一个镜像。

     >docker build -t runoob/centos:6.7 .
     >-t:指定要创建的目标镜像名
     . ：Dockerfile 文件所在目录，可以指定Dockerfile 的绝对路径
     
 3. `docker run -p 6001:50001 -t -i hyq/kgqa:1.2`
 > 50001端口为dockerfile中指定http服务器的端口,使用-p命令,将其映射至本机的6001端口,并修改flask_web.py中的默认端口号,使之与6001对应.运行时,另制定flask_web.py端口号,如7001,即可成功运行.

 4. 使用命令:`docker exec $IMAGE_ID ls` 可以查看该docker中的目录.
 5. 使用命令:`docker exec $IMAGE_ID cat engine.log` 可查看docker服务器中的log.
 6.  `docker image rm -f IMAGEID`删除docker image

 7. 关掉运行中的docker:
 >1.docker ps #查看运行中的docker
 >2.docker stop $IMAGE_ID
 

 8. 使用`docker run --env-file=env.conf -p 50001:50001 kgqa`可以将配置文件env.conf中的参数传进dockerfile

 9. docker教程:https://yeasy.gitbooks.io/docker_practice/content/image/dockerfile/cmd.html
 10. `docker ps -a`查看所有的container
 11. `docker rm container_id`删除container
 12. `docker image rm id`删除image
 13. `COPY`失败有可能是因为在.dockerignore文件中忽略了该文件