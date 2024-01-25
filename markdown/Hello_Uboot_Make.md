# uboot编译命令  
## make imx6ull_14x14_evk_emmc_defconfig  
![make xxx defconfig flow](../pic/make_xxx_defconfig_flow.jpg "make xxx defconfig flow")  
`make xxx_defconfig`最终在根目录下生成.config文件，该文件为后续编译提供配置项目。
## make   
![make flow](../pic/make.jpeg "make flow")  
`u-boot`是ELF格式文件，`make`命令的本质是通过编译链接生成`u-boot`文件。

