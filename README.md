# ubuntu
## windows10子系统
      子系统导入导出
             https://blog.csdn.net/sinat_32596537/article/details/87524071
             https://www.cnblogs.com/ahmczsy/p/10544926.html
      
      WSL 服务自动启动的正确方法
            https://zhuanlan.zhihu.com/p/47733615


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
            
        4.启动服务：sudo service kafka start
