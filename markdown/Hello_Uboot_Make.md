# uboot编译命令  
## make imx6ull_14x14_evk_emmc_defconfig  
![make xxx defconfig flow](../pic/make_xxx_defconfig_flow.jpg "make xxx defconfig flow")  
`make xxx_defconfig`最终在根目录下生成.config文件，该文件为后续编译提供配置项目。
## make   
![make flow](../pic/make.jpeg "make flow")  
`u-boot`是ELF格式文件，`make`命令的本质是通过编译链接生成`u-boot`文件。

# uboot移植  
## 添加新的板子  
>`cp /configs/mx6ull_14x14_evk_emmc_defconfig /configs/mx6ull_joey_emmc_defconfig //新建defconfig文件并修改`  
>`cp /include/configs/mx6ullevk.h /include/configs/mx6ull_joey_emmc.h //新建板子头文件并修改`  
>`cp /board/freescale/mx6ullevk/ /board/freescale/mx6ull_joey_emmc/ -r //新建板子源文件并修改Makefile Kconfig等`   
>`vi /arch/arm/cpu/armv7/mx6/Kconfig //添加新板子配置信息`

# uboot启动  



