# 概述

该程序主要是对编码器进行测试。通过串行端口，我们可以与程序进行交互，输入相应的命令，就可以获取到相应的数据。

# 硬件要求

- YC2010-28磁编码器4个
- 直流减速电动机4个(12V, 366rpm)
- Arduino Mega 2560
- 杜邦线若干

# 引脚连接

|   车轮  | 右前轮     | 左前轮     | 右后轮   | 左后轮  |   
| :-------------: | :-------------: | :-------------: | :-------------: |   
|   引脚 | 18,22     | 19,23    | 21,24  | 20,25  |    

下图为具体的连接方法（以左前轮为例）：

![encoder](https://github.com/Saturn-robot/Encoder_driver/blob/master/Test_Encoders/circuit_diagram/FIT0403_encoder.png)

1、2接电源的正负极;

3接GND管脚，4接5V管脚;

5接中断管脚，6接普通的数字管脚;

注意：5,6引脚需要特别说明：我们所使用的Arduino Mega2560有6个中断管脚，如下表所示：


| 型号 | #0中断 | #1中断 | #2中断 | #3中断 | #4中断 | #5中断 |    
| :------: | :-----: |    
| Mega 2560 | 2 | 3 | 21 |  20 | 19 | 18 |    

详细内容请参考：<https://www.arduino.cc/en/Reference/AttachInterrupt>

# 使用手册

## 获取编码器数据

使用`e`命令即可获取到四个编码器的数据:

    e

## 编码器清零

使用`r`命令即可使编码器数据清零。

具体可以查看程序中的`command.h`文件:

```
#define READ_ENCODERS  'e'
#define RESET_ENCODERS 'r'
```

# 注意事项

- 安装增量式磁编码器时，要注意磁鼓不要接触到霍尔元件；
- 安装编码盘时，要注意导线的方向。安装之前最好做一个大致的布局，否则焊好之后很难改变导线的朝向；
