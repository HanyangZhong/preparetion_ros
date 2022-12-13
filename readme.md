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
