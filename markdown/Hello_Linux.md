# 常用命令  
## nmcli 连接wifi  
>`sudo apt-get install nmcli` #安装nmcli命令  
>`sudo nmcli dev` #查看网络设备    
>`sudo nmcli r wifi on` #开启wifi  
>`sudo nmcli dev wifi` #扫描wifi  
>`sudo nmcli dev wifi connect "wifi名" password "密码"` #连接wifi  

## tar 打包压缩  
>`tar -cf documents.tar /home/user/documents` #打包文件和目录  
>`tar -xf documents.tar` #解包归档文件  
>`tar -czf document.tar.gz /home/user/documents` #使用gzip打包压缩  
>`tar -xzf document.tar.gz` #使用gzip解压缩  
>`tar -cjf document.tar.bz /home/user/documents` #使用bzip2打包压缩  
>`tar -xjf document.tar.bz` #使用bzip2解压缩  
>`tar --list -f documents.tar` #列出归档文件内容  

