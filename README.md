## 【入门篇】

- 电容通交流隔直流，电感通直流隔交流
- 肖特基二极管，比较低的导通压降

## 【强化篇】

### 【P16】【强化篇】15-元件符号绘制

文件 > 新建 > 元件

- 半径改为 <u>0.01inch</u>

![image-20240708213208373](https://s2.loli.net/2024/07/08/uN5nx3eymTPQU4g.png)

### 【P17】【强化篇】16-元件封装绘制

文件 > 新建 > 封装

- 查阅数据手册《C9418\_运算放大器\_LM358D\_规格书\_ST(意法半导体)运算放大器规格书》，“6.2 SO8 package information”，即 SOP 封装

![image-20240708205019248](https://s2.loli.net/2024/07/08/ISlBN9rJHRkLWqg.png)

:one: 焊盘

- 图层：`LM358DT` 是表贴封装，需要修改焊盘的图层属性改为 <u>顶层</u>。这样就会变成顶层的表贴焊盘
- 形状：改为 <u>长圆形</u>
- 宽：从”Figure 28. SO8 package mechanical drawing”看出b是引脚的宽度，“Table 5. SO8 package mechanical data“中b对应的Min.和Max.分别为0.28和0.48，因为需要把引脚整个包住，焊盘宽度可以取得大一些如 <u>0.6mm</u>

![image-20240708210345646](https://s2.loli.net/2024/07/08/YpcknshBxLEujZP.png)

- 高：查看L1典型值为1.04，可以取大一点为 <u>1.9mm</u>

![image-20240708205534109](https://s2.loli.net/2024/07/08/c6RXCF3JgInf8hU.png)

焊盘的尺寸标注完成

![image-20240708210249252](https://s2.loli.net/2024/07/08/lAztZdKSamRqUNC.png)

元器件有8个引脚，首先复制出一侧的4个引脚，三种方法：

1. 复制粘贴法：中心X距离根据e的典型值 <u>1.27mm</u> 进行依次计算，第二个中心X距离为 <u>1.27mm</u>，第三个中心X距离为 <u>1.27*2mm</u>，第四个中心X距离为 <u>1.27*3mm</u>
2. 智能尺寸法：标注方法与 SolidWorks 几乎一致
3. 线性阵列法：放置 > 焊盘 > 条形多焊盘，点击原点，向右拉动，Tab 一次填数量 <u>4</u>，再 Tab 一次填距离 <u>1.27</u>，Enter 确定

![image-20240708210912733](https://s2.loli.net/2024/07/08/5wbRTAnSZVCQGM4.png)

全选复制粘贴另一侧焊盘，两侧焊盘距离应该是两侧焊盘中心点之间的距离，相当于 E1 + 焊盘的高 = 3.9 + 1.9 = 5.8

![image-20240708212250423](https://s2.loli.net/2024/07/08/Ytn4dwE9Ba2kJgO.png)

修改另一侧其中一个焊盘的位置“中心Y”为 <u>5.8mm</u>，框选另一侧的4个焊盘为顶部对齐

![image-20240708212955806](https://s2.loli.net/2024/07/08/YVcCwL8tERB7OZ4.png)

修改引脚的编号

- 第一个引脚放置在原点，剩下引脚应该逆时针排列

![image-20240708213816756](https://s2.loli.net/2024/07/08/raKVIRv6x4z7yqC.png)

:two: 丝印

- 右边栏：图层 > 顶层丝印层

第一种方法：

- 放置 > 线条 > 矩形

- 放置 > 线条 > 圆形，表明芯片正方向朝左

![image-20240708215338672](https://s2.loli.net/2024/07/08/D7qeroiwRcjaA4y.png)

第二种方法：

- 放置 > 线条 > 中心圆弧
- 放置 > 线条 > 折线
- 放置 > 线条 > 圆形

![image-20240708220459653](https://s2.loli.net/2024/07/08/EIa3e7SQwRbu5DN.png)

绑定元件和封装

- 底部导航栏：库 > 器件 > 个人 > 右键器件 LM358DT > 关联封装，个人 > 点击封装 > 确定

![image-20240708220947622](https://s2.loli.net/2024/07/08/ovlnhB34jL8DP6a.png)

![image-20240708221016203](https://s2.loli.net/2024/07/08/zTHnuD984JaNhUe.png)

测试封装

- 所有工程 > test1工程 
- 工程设计 > 打开原理图
- 底部导航栏 > 库 > 个人 > `LM358DT` > 放置
- 顶部导航栏 > 更新/转换原理图到PCB > 应用修改

![image-20240708221552070](https://s2.loli.net/2024/07/08/8dhTUrRONFEmM3b.png)

- 3D视图

![image-20240708221635633](https://s2.loli.net/2024/07/08/KoJ9gzLX75Tsiar.png)

### 【P18】【强化篇】17-51单片机核心板元件选型

- `STC89C52RC`
  - XTAL（晶振，crystal oscillator）
  - 谐振电容、滤波电容

![image-20240708222900729](https://s2.loli.net/2024/07/08/jFxW1QMeVDmgXE3.png)

- 电源电路：Type-C接口分为：6PIN（仅供电）、16PIN（USB2.0）、24PIN（USB3.0）。仅需供电选 6PIN
- 5V转3.3V：LDO 芯片 `AMS1117`，经典的线性稳压器

![image-20240708223531108](https://s2.loli.net/2024/07/08/NH8ryVj4qJomh3e.png)

- 外围功能电路：
  - 按键检测电路：单片机引脚检测按键，实现一些操作
    - 选择微动贴片按键
  - LED指示灯：指示系统状态
    - 0805贴片LED指示灯
  - 排针引出：方便调试和外接模块

### 【P19】【强化篇】18-51核心板电源&最小系统原理图设计

#### :one: 电源电路部分

- `TYPE-C-6P-DIP2X2`
  - VBUS——电源正极
  - CC1、CC2——负责快充
    - CC（Configuration Channel，配置通道）
    - 不需要，5.1k（？？？）电阻接地
  - EH——固定的针脚

![image-20240709222437676](https://s2.loli.net/2024/07/09/dRBinxGgpN6f4v5.png)

- `SS3235S-L1`——开关，2侧6个触点
  - 只需要1侧3个触点，另一侧不需要用直接接地
  - 开关输出需要接LDO（Low Dropout Regulator，低压差线性稳压器），给个+5V（？？？）

![image-20240709222510831](https://s2.loli.net/2024/07/09/ExPG6u3wHmp4Zj7.png)

- `AMS1117-3.3_C6186`——LDO（Low Dropout Regulator，低压差线性稳压器）

![image-20240709222527206](https://s2.loli.net/2024/07/09/7TudoqYsgSRP4zf.png)

- `LED_0805-G(LED_0805)`

![image-20240709222739884](https://s2.loli.net/2024/07/09/cLam5P41ZYW9jnz.png)

- 滤波电容：参考 `AMS1117` 数据手册，得知输入输出电容都是 <u>10μF</u>
  - 选用 1 个 <u>10μF</u> 陶瓷电容和 1 个 <u>0.1μF(100nF)</u> 陶瓷电容并联使用（？？？，并联滤波效果更好，可以缩短缓冲时间）
  - 选用 `CAP_0805(C0805)`

![image-20240709223248562](https://s2.loli.net/2024/07/09/lqYkpzi4Qtjv9oy.png)

![image-20240709224811103](https://s2.loli.net/2024/07/09/N546OikhvrbgfVJ.png)

#### :two: 单片机的最小系统电路

- 选型：`STC89C52RC-40I-LQFP44`
- 一般芯片附近会加一颗 <u>0.1μF(100nF)</u> 的去耦电容（？？？，滤除高频噪声，使电压稳定干净，保证元件的正常工作）
- 快速添加网络标签：选中右键 > 扇出网络标签/非连接标识

![image-20240709233332953](https://s2.loli.net/2024/07/09/AZYbPFUW53xVJqo.png)

**晶振电路**

- XTAL1、XTAL2引脚接 <u>12MHZ</u> 的外部晶振
- 选型：`ABLS-12.000MHZ-B4H-T`
  - 需要 2 个谐振电容，容值参考数据手册《C8707_单片机(MCU-MPU-SOC)_STC89C52RC-40I-LQFP44_规格书_STC(宏晶)单片机(MCU_MPU_SOC)规格书》，为 <u>47pF</u>

![image-20240709232738343](https://s2.loli.net/2024/07/09/MKdCBTZE2J1kmAu.png)

![image-20240711232042927](https://s2.loli.net/2024/07/11/6tAjfvUFHg9NOqC.png)

**单片机复位电路**

- <u>10K</u> 电阻和 <u>10μF</u> 电容

![image-20240709233657783](https://s2.loli.net/2024/07/09/XtQRgDJbyhclrvw.png)

分析复位电路：

- 复位电路上电时，电容需要充电，会产生比较大的电流，电流经过 R4 会使 RST 进入高电平
- 随着电容充电完成，电流会逐渐减小，RST 会被下拉至 GND

由于 RST 是高电平复位，所以单片机上电时，电路就会自动进行复位

如果希望手动复位，可以在电容上并联一个按键，按下按键会被自动上拉至高电平，可以使单片机复位

- 按键选型：`轻触按键3*4*H`

![image-20240709235223622](https://s2.loli.net/2024/07/09/DqXjZd7faVIn3Jh.png)

**排针引出**

- 选型1：`HDR-M_2.54_1x16P(HDR-TH_16P-P2.54-V-M)`
- 选型2：`HDR-M_2.54_1x7P(HDR-TH_7P-P2.54-V-M)`

![image-20240711214107633](https://s2.loli.net/2024/07/11/gUoFEczfHWVJPah.png)

#### :three: 按键电路

- 按键消抖：并上1个电容

![image-20240711214942944](https://s2.loli.net/2024/07/11/OhYmnj9GI5auswl.png)

#### :four: LED 驱动电路

- IO口不能放在LED阳极，而要放在LED阴极
- 对于51单片机的IO口来说，电流输入能力远大于电流输出能力，即灌电流大于拉电流
- 当IO口输出低电平时，LED点亮；当IO口输出高电平时，LED熄灭

![image-20240711215946466](https://s2.loli.net/2024/07/11/1Fgm2OSpr6Ml5Ix.png)

#### :five: P0 口上拉电阻

- 根据《C8707\_单片机(MCU-MPU-SOC)\_STC89C52RC-40I-LQFP44\_规格书\_STC(宏晶)单片机(MCU_MPU_SOC)规格书》——“第4章 STC89C51RC/RD+系列单片机的I/O口结构”描述

![image-20240711220839710](https://s2.loli.net/2024/07/11/D45XZwWfIHEqiKj.png)

![image-20240711220857654](https://s2.loli.net/2024/07/11/UuiBCXsaTZxehgK.png)

![image-20240711221627502](https://s2.loli.net/2024/07/11/pYTzL1XNjmbdrew.png)

#### :six: 电源引出引脚

- 外接传感器有核心板供电，需要引脚将电源引出

![image-20240711222956716](https://s2.loli.net/2024/07/11/3IfFkNwaEijZcHp.png)

#### :seven: 串口引出引脚

- 方便外部通信和下载程序
- 串口引脚：RXD/P3.0、TXD/P3.1

![image-20240711222507795](https://s2.loli.net/2024/07/11/jMOIc4GvtebYVuf.png)

![image-20240711222942592](https://s2.loli.net/2024/07/11/TSMbIAKugfYUPq4.png)

### 【P20】【强化篇】19-51核心板外围功能电路原理图设计&DRC

**电路原理图成品**

![SCH_51单片机核心板原理图_1-P1_2024-07-11](https://s2.loli.net/2024/07/11/6pUvBYHfgMW1CcJ.png)

**DRC 检测结果**

![image-20240711232828646](https://s2.loli.net/2024/07/11/T4qAIVOWM7tsn2h.png)



## 快捷键

- Q：单位
- Space：旋转 - 左向旋转
- X：翻转 - 左右翻转
- W（Wire）：绘制导线、单路布线
- R（Rectangle）: 矩形

