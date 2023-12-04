# 一、汇编Led  
## KeyPoint  
点亮一个LED通过控制IO引脚的GPIO复用功能。   
**0.** 时能GPIO外设时钟`CCM_CCGRx`   
**1.** 配置IO引脚的复用功能`IOMUXC_SW_MUX_CTL_PAD_xxx`       
**2.** 配置IO引脚的电器属性`IOMUXC_SW_PAD_CTL_PAD_xxx`  
**3.** 配置GPIO为输出`GPIOx_GDIR`  
**4.** 控制GPIO输出高低电平`GPIOx_DR`  

## DemoCode  
>.global _start  
>_start:  
>&emsp;**#`CCM_CCGR1` 使能GPIO1外设时钟**   
>&emsp;ldr r0, =0x020c406c       
>&emsp;ldr r1, =0x0c000000  
>&emsp;str r1, [r0]  
>&emsp;  
>&emsp;**#`IOMUXC_SW_MUX_CTL_PAD_GPIO1_IO00` GPIO1_IO00引脚复用为GPIO1_IO00功能**  
>&emsp;**#实际上该引脚名为GPIO1_IO00,默认复用功能就是GPIO**   
>&emsp;ldr r0, =0x020e005c   
>&emsp;ldr r1, =0x05
>&emsp;str r1, [r0]  
>&emsp;  
>&emsp;**#`IOMUXC_SW_PAD_CTL_PAD_GPIO1_IO00` 设置IO属性**  
>&emsp;ldr r0, =0x020e02e8  
>&emsp;ldr r1, =0x10b0  
>&emsp;str r1, [r0]  
>&emsp;  
>&emsp;**#`GPIO1_GDIR` 设置GPIO1_IO00输出模式**  
>&emsp;ldr r0, =0x0209c004  
>&emsp;ldr r1, =0x1  
>&emsp;str r1, [r0]  
>&emsp;  
>&emsp;**#`GPIO1_DR` 设置GPIO1_IO00输出高电平**  
>&emsp;ldr r0, =0x0209c000  
>&emsp;ldr r1, =0x1  
>&emsp;str r1, [r0]   
>&emsp;  
>&emsp;**#死循环,防止不可预计**  
>loop:  
>&emsp;b loop  
  


