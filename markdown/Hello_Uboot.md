# 常用命令
## help帮助信息
>=>`help`  //查看所有支持的命令  
>=>`help cmd` //查看**cmd**命令提示信息  
>=>`?` //作用等同于**help**  

## bdinfo查看板子信息  

## print查看环境变量  

## version查看版本信息  

## setenv设置环境变量  
>=>`setenv bootdelay 5` //修改**bootdelay = 5**  
>=>`setenv bootargs 'console=ttymxc0,115200 root=/dev/mmcblk1p2 rootwait rw'` //包含空格的变量值需要用单引号括起来   
>=>`setenv myEnv joey` //新建环境变量**myEnv = joey**  
>=>`setenv myEnv` //删除环境变量**myEnv**  

## saveenv保存环境变量  

## md显示内存 md[.b,.w,.l] address count 
>=>`md.b 80000000 40` //打印0x80000000开始的0x40个**byte**的内存值  
>=>`md.w 80000000 20` //打印0x80000000开始的0x20个**world**的内存值  
>=>`md.l 80000000 10` //打印0x80000000开始的0x10个**long**的内存值  

## nm修改指定内存 nm[.b,.w,.l] address   
>=>`nm.l 80000000` //修改0x80000000地址内存值为**0x1234567**      
>80000000: 0500e031 ? `12345678`  
>80000000: 12345678 ? `q`  
>=>

## mm连续修改内存 mm[.b,.w,.l] address  
>=>`mm.l 80000000`  //修改0x80000000开始的内存值  
>80000000：12345678 ？`05050505`  
>80000004: 15d723ac ? `05050505`  
>80000008: 2b008806 ? `05050505`  
>8000000c: ae78903f ? `q`  
>=>

## mw指定内存写入指定数据 mw[.b,.w,.l] address value count  
>=>`mw.b 80000000 0a 10` //从0x80000000开始写入**0x10**个**0x0a**    

## cp复制内存 cp[.b,.w,.l] source target count   
>=>`cp.b 80000000 80000100 10` //从0x80000000拷贝**0x10**个**byte**到0x80000100  

## cmp比较内存 cmp[.b,.w,.l] addr1 addr2 count  
>=>`cmp.b 80000000 80000100 10` /比较0x80000000和0x80000100的**0x10**个**byte**  






