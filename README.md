# ubuntu

## netstat命令使用

      netstat -anptc
            a:显示所有连线中的Socket
            n:直接使用IP地址，而不通过域名服务器
            p:显示正在使用Socket的程序识别码和程序名称
            t:显示TCP传输协议的连线状况
            c:持续显示

      netstat -anpt |grep -i "7070" |wc -l

## ubuntu18安装mysql修改root默认密码
      https://blog.csdn.net/qq_38737992/article/details/81090373
      
## 修改默认jdk
      查看：sudo update-alternatives --list java
      修改：sudo update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_221/bin/java 300
      
      

## ubuntu将程序加入服务
      1.进入目录： cd /etc/init.d/
      2.新建文件： sudo vi kafka
      3.编辑内容
      
            ======内容开始===========================================================================================
            
            #!/bin/bash
            #chkconfig:2345 20 90
            #description:zookeeper
            #processname:zookeeper
            case $1 in
                      start)
                          #启动命令    
                          /opt/kafka_2.12-1.0.0/bin/kafka-server-start.sh -daemon /opt/kafka_2.12-1.0.0/config/server.properties
                          ;;
                      stop)
                          #停止命令    
                          /opt/kafka_2.12-1.0.0/bin/kafka-server-stop.sh
                          ;;
                      restart)
                          #重启命令    
                          /opt/kafka_2.12-1.0.0/bin/kafka-server-stop.sh
                          /opt/kafka_2.12-1.0.0/bin/kafka-server-start.sh -daemon /opt/kafka_2.12-1.0.0/config/server.properties
                          ;;
                      *)
                          echo "require start|stop|restart"
                          ;;
            esac
            
            ========内容结束=========================================================================================
            
        4.刷新服务systemctl daemon-reload
        5.启动服务：sudo service kafka start
        
        
## ubuntu20安装软件
      
      docker安装 >>>>>>>>>>>>>>>>>>>>>>>>>>>>
            1、安装docker
                  sudo apt install docker.io
            2、创建docker用户组
                  sudo groupadd docker
            3、加入docker用户组
                  sudo usermod -aG docker $USER
            4、更新docker用户组
                  newgrp docker
            5、修改镜像下载源      
                  进入/etc/docker
                  查看有没有 daemon.json。这是docker默认的配置文件。
                  如果没有新建，如果有，则修改。
                  
                   {
                     "registry-mirrors": ["https://zfzbet67.mirror.aliyuncs.com"]
                   }
             6、Docker 常用命令
                  1.启动docker
                  sudo service docker start
                  2.停止docker
                  sudo service docker stop
                  3.重启docker
                  sudo service docker restart      
                   
         wine安装>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
            1、sudo dpkg --add-architecture i386
            2、wget -nc https://dl.winehq.org/wine-builds/winehq.key
            3、sudo apt-key add winehq.key
            4、sudo dedit /etc/apt/sources.list 【添加源】
                  deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
            5、sudo apt update
            6、sudo apt install --install-recommends winehq-stable
            7、wine -version


## git初始化密码

      在你的用户目录下,用户目录:
          windows: C:/Users/username
          mac os x: /Users/username
          linux: /home/username



      这里默认你已经安装好了git，首先我们需要在命令行窗口中运行命令：
            1、git config --global credential.helper store
            2、vim .git-credentials
            3、
                  1>手动记录密码：添加内容（这里以github为例）https://{username}:{password}@github.com
                  2>自动记录密码：直接运行命名git pull，这时会让你输入用户名的密码，在你输入了正确的用户名和密码后，下次再运行git pull或者git push的时候就会发现再也不用输入用户名和密码了。



