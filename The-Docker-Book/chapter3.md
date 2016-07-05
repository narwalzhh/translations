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
