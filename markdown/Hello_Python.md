# Hello_Python  
## 第一个python示例
>`spam_amount = 0`  
>`print(spam_amount)`  
>
>`#ordering spam egg spam bacom and spam`  
>`spam_amount = spam_amount + 4`
>
>`if spam_amount > 0:`  
>&emsp;&emsp;&emsp;&emsp;`print("But I don't want any spam!)`  
>
>`viking_song = "Spam " * spam_amount`  
>`print(viking_somg)`   

## 定义变量  
>`spam_amount = 0`  
#我们创建了一个名为`spam_amount`的变量，通过`=`等号赋予值为0，这就是赋值操作.  
**NOTE:**  
1.在python中，变量在赋值前不需要声明。  
2无需告诉python变量的数据类型。一个变量可以被重新赋值为其他类型数据。比如原来是字符串的变量，可以赋值为布尔值。  

## 方法调用  
>`print(spam_amount)`  
#`print`是python中用来打印信息的功能函数，我们输入函数名和括号来调用函数，括号内是函数的输入，即参数。   

## 注释  
>`#ordering spam egg spam bacom and spam`  
#通过井号标记该行是注释内容  

## 赋值   
>`spam_amount = spam_amount + 4`  
#这里对变量`spam_amount`重新赋值，并做了简单的加法运算，python首先会计算等号右边的表达式(**spam_amount + 4**),然后将结果赋值给等号左边的变量。  

## 代码块  
>`if spam_amount > 0:`  
>&emsp;&emsp;&emsp;&emsp;`print("But I don't want any spam!)`    
#python中冒号代表代码块的起始，通过缩进(**四个空格**)表示代码块的所属。这里`if`条件语句判断变量`spam_amount`大于0时执行`print`函数。  

## 乘法重复
>`viking_song = "Spam " * spam_amount`  
>`print(viking_somg)`  
#在pyton中，`*`乘号在不同类型变量的作用是不同的，这里对字符串`Spam `进行乘法操作，本质是对字符串的重复扩展，变量`vikong_song`的结果为`Spam Spam Spam Spam `  


## 算术运算  
|    运算操作    |     名字     |        描述        |  
|---------------|-------------|-------------------|  
| a + b        |   加法        |	a加b的和        |  
| a - b        |   减法        |    a减b的差       |  
| a * b        |   乘法        |     a乘b的积 		|  
| a / b 		|  真除法      |     a除b的商			|  
| a // b       |   整除        |     a除b的商，去除小数部分|  
| a % b        |   模数        |     a除以b的余			|  
| a ** b       |   指数        |     a的b次方			|  
| -a           |   负数        |     a的负数            |

>`print(5 / 2)`  
>`print(6 / 2)`  
**2.5**  
**3.0**
>
>`print(5 // 2)`  
>`print(6 // 2)`  
**2**  
**3**  

## 运算顺序  
**PEMDAS**    
**P**arentheses  **括号**  
**E**xponents **指数运算**  
**M**ultiplication/**D**ivision **乘除运算**   
**A**ddition/**S**ubtraction **加减运算**     
                
## 与数内建函数  
### type
>`spam_amount = 0`  
>`type(spam_amount)`  
>**int**  
>`type(19.95)`  
>**float**  
#通过`type`函数获得指定数据或者变量的类型  

### min max  
>`print(max(1,2,3))`  
**3**  
>`print(min(1,2,3))`  
**1**  
#通过`min`函数获得最小值，通过`max`函数获得最大值  

### abs
>`print(abs(32))`  
>`print(abs(-32))`  
**32**  
**32**  
#通过`abs`函数获得绝对值  

### float  
>`print(float(10))`  
**10.0**  
#通过`float`函数将输入参数转换为float类型

### int  
>`print(int(3.33))`  
>`print(int('807') + 1)`  
**3**  
**808**  
通过`int`函数将输入参数转换为int类型








