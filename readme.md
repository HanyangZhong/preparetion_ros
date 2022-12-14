# 安装ubuntu20 focal
`https://zhuanlan.zhihu.com/p/135953477`    
`https://www.jianshu.com/p/54d9a3a695cc`    

## 安装后国外任然可连接源到中科大或阿里源下载ros




## 分布式通信   
树梅派固定ip    
`https://blog.csdn.net/qq_44214671/article/details/114165432`   
    
## 配置hosts文件   
`sudo gedit /etc/hosts`   

## 电脑从机文件设定内容    
主机树梅派的ip地址以及电脑名称    
```127.0.0.1	localhost
127.0.1.1	zhy
192.168.0.110	raspberrypi

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
## 树梅派主机操作同理   
## 设置树梅派source文件
`sudo gedit .bashrc`    
```
export ROS_MASTER_URI=http://主机IP:11311
export ROS_HOSTNAME=主机IP
```   
`source .bashrc`    

## 设置电脑source文件
`sudo gedit .bashrc`    
```
export ROS_MASTER_URI=http://主机IP:11311
export ROS_HOSTNAME=从机IP
```   
`source .bashrc`    

## 寻找已安装ros包
`rospack find XXX`  

## 环境变量问题
如果有项目先前已经在 .bashrc 文件内导入了环境变量，会导致整个环境中运行的包变成那个项目的包优先被调用，从而可能导致其他项目的依赖出问题        
建议在创建工作空间前，先将其他项目在 .bashrc 引入的环境变量注释，并编译 source .bashrc     
在此操作下再创建工作空间加入功能包编译，不会出现问题      


