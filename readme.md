# 安装ubuntu20 focal
`https://zhuanlan.zhihu.com/p/135953477`    
`https://www.jianshu.com/p/54d9a3a695cc`    
`https://blog.csdn.net/hwh295/article/details/113409389`        

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


## move_base参数设置以及amcl包参数设置问题
amcl:       
/odom以及/map链接的主要是由amcl包实现的      
如果请求/odomy以及/map链接出现异常，可能是amcl包设置超时时间有关
<param name="transform_tolerance" value="1.0" />        
这个时间可以设长一些      
        
move_base:      
costmap_common_params最好将global和local分开      
global的膨胀半径可以设的比local的稍微大一些，这样容易绕开障碍物      
global的cost_scaling_factor可以设的比local大一些，容易绕开障碍物     
        
local的膨胀半径可以设的比global的稍微小一些，这样容易绕开障碍物      
local膨胀半径一般设为小车的半径      
local的cost_scaling_factor可以设的比global大一些，容易绕开障碍物   
        
base_local_planner_params参数设定需按照实际情况        
最大线速度和最大角速度都需要实测        
前进模拟参数sim_time非常重要      
如果机器人在本地规划上表现不太好容易打转，多半是本地路径规划太短导致      
可以适当延长sim_time时间        

其他参数调节      
`https://www.cnblogs.com/lizhensheng/p/11117583.html`
