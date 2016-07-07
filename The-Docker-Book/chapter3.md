1. #### 查看docker程序是否存在，功能是否正常：docker info

2. #### Docker容器的创建到启动：docker run

  ```
  # -i 保证容器中STDIN是开启的
  # -t 为要创建的容器分配一个伪tty终端
  # -i -t 创建一个能与之交互的容器
  # ubuntu 使用的是ubuntu镜像
  # /bin/bash 告诉docker在新容器中执行什么命令  

  sudo docker run -i -t ubuntu /bin/bash
  ```
  ```
  # 获取容器主机名
  hostname
  # 查看容器的网络配置
  ip a
  # 查看容器中运行的进程
  ps -aux
  # 退出容器
  exit
  ```

3. #### 查看当前系统中容器的列表：docker ps

  ```
  # 查看正在运行的容器
  docker ps
  # 查看所有的容器
  docker ps -a
  # 查看最后一次运行的容器
  docker ps -l
  ```

4. #### 指定容器的名称： --name

  ```
  # 名称的规则
  [a-zA-Z0-9_.-]

  sudo docker run --name my_container_name -i -t ubuntu /bin/bash
  ```

5. #### 重新启动已经停止的容器： docker start

  ```
  # 查看所有的容器
  sudo docker ps -a
  # 启动指定名称的容器
  sudo docker start container_name_to_start
  # 查看是否启动
  sudo docker ps
  ```

6. #### 附着在容器上： docker attach

  ```
  # 启动某个容器
  # 依附到次容器上
  # 可以使用容器名称指定也可以使用容器ID指定
  docker attach container_name
  ```

7. #### 创建守护进程： -d

  ```
  # 创建守护进程，返回容器ID
  sudo docker run --name daemon_dave -d ubuntu /bin/sh -c
    "while true; do echo hello world; sleep 1; done"
  ```

8. #### 获取容器日志信息： docker logs

  ```
  sudo docker logs daemon_container_name
  # 动态获取日志信息 -f
  sudo docker logs -f contianer_name
  # 获取最后几条日志信息
  sudo docker logs --tail 10 contianer_name
  # 跟踪最新日志
  sudo docker logs --tail 0 -f contianer_name
  # 为日志信息加上时间戳 -t
  sudo docker logs --tail 0 -ft contianer_name
  ```

9. #### 查看容器内进程 docker top

  ```
  sudo docker top contianer_name
  ```

10. #### 容器内部运行进程： docker exec

  ```
  # -d 要运行一个后台进程
  # touch /etc/new_config_file 创建一个新的文件
  sudo docker exec -d container_name touch /etc/new_config_file
  # -t -i 创建交互式任务
  sudo docker exec -t -i container_name /bin/bash
  ```

11. #### 停止守护进程： docker stop

  ```
  sudo docker stop container_name
  # 快速停止某个容器 docker kill
  # 显示最后 x 个容器
  sudo docker ps -n x
  ```

12. #### 自动重启容器： --restart

  ```
  # always 无论退出代码是什么，都会自动重启该容器
  sudo docker run --restart=always --name container_name
  -d ubuntu /bin/bash -c
  "while true; do echo hello world; sleep 1; done"
  # on-failure 指定有当退出代码非 0 时，才会自动重启
  # on-failure:5 指定重启次数参数
  ```

13. #### 深入容器： docker inspect

  ```
  sudo docker inspect container_name
  # 使用 -f 或 --format 标志查看指定结果
  sudo docker inspect --format='{{.Name}} {{.State.Running}}'
  container_name
  ```

14. #### 删除容器： docker rm

  ```
  # 也可用ID指定容器
  sudo docker rm container_name
  # 删除所有容器
  # -q 返回容器ID
  sudo docker rm 'docker ps -a -q'
  ```
