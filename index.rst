荔枝丹 全流程指南
=================================================

荔枝丹，一款嵌入式AI开发平台。

人工智能浪潮正在席卷而来，在这种环境下，荔枝丹经过数月打磨，终于在10月，向各位热爱开源和人工智能的极客们见面了。
荔枝丹是国内一款优秀的开源AI开发套件，志在推广AI相关的开发和教育，集成Micropython，让开发不再困难。

.. figure:: http://pgeza64pd.bkt.clouddn.com/dan-board.jpg
  :width: 500px
  :align: center
  
  荔枝丹 - Lichee Dan
 
荔枝丹使用嘉楠堪智科技的AI芯片k210作为核心单元，带独立FPU的双核处理，64位的CPU位宽，8M的片上SRAM，400M的可调标称频率，支持乘法、除法和平方根运算的双精度FPU。高性能的核心处理特性展露无遗。

在AI处理方面k210可进行卷积、批归一化、激活、池化等运算。同时也可以进行语音方向扫描和语音数据输出的前置处理工作。

荔枝丹具有以下能力

- 数字视频接口 (DVP)
- 通用异步收发传输器 (UART)
- 直接内存存取控制器 (DMAC)
- 集成电路内置总线 (I²C)
- 串行外设接口 (SPI)
- 集成电路内置音频总线 (I²S)
- 联合测试工作组 (JTAG)
- 现场可编程 IO 阵列 (FPIOA/IOMUX)

令人惊艳的是，荔枝丹还具备

- 神经网络处理器 (KPU)
- 音频处理器 (APU)
- 快速傅里叶变换加速器 (FFT Accelerater)
- 高级加密加速器 (AES Accelerater) 
- 安全散列算法加速器 (SHA256 Accelerater)  
- 快速傅里叶变换加速器 (FFT Accelerater)

|  
.. figure:: http://pgeza64pd.bkt.clouddn.com/dan-core-borad.jpg
  :width: 500px
  :align: center
  
  荔枝丹核心板

荔枝丹的特性如下

- 具备机器视觉能力
- 具备机器听觉能力
- 更好的低功耗视觉处理速度与准确率
- 具备卷积人工神经网络硬件加速器 KPU，可高性能进行卷积人工神经网络运算
- 支持固件加密，难以使用普通方法破解
- 独特的可编程 IO 阵列，使产品设计更加灵活
- 3.3V/1.8V 双电压支持，无需电平转换，节约成本
|

荔枝丹的板载外设

- 72pin全引脚引出，可自由映射功能
- FPC24P座，可接DVP摄像头
- FPC24P座，可接8bit MCU LCD
- 板载功率放大IC，可配合喇叭使用
- 板载Tpye C接口
- 板载TF卡槽
- 板载麦克风
- 板载wifi
- 板载高速DAC
- 可带麦克风阵列扩展板进行语音识别，波束成型，声场成像

.. figure:: http://pgeza64pd.bkt.clouddn.com/dan-pin.png
  :width: 500px
  :align: center
  
  荔枝丹引脚图

您可能需要这些来进一步了解荔枝丹： `kendryte210_datasheet  <http://pgeza64pd.bkt.clouddn.com/kendryte_datasheet_20180919020633.pdf>`_ | `荔枝丹原理图 <http://pgeza64pd.bkt.clouddn.com/K210_dock.pdf>`_

荔枝丹仍在不断地成长，对于外观、电路设计、文档内容甚至于荔枝丹的发展方向，我们欢迎您到 `荔枝丹 | 建议与讨论区 <http://bbs.lichee.pro/t/dan>`_ 提出您宝贵的建议。
 
同时欢迎各位加入 `荔枝派交流群826307240 <https://jq.qq.com/?_wv=1027&k=5uWO21P>`_ | `荔枝派Telegram电报群 <https://t.me/sipeed>`_ 与众多开发者、爱好者即时交流。

.. figure:: http://odfef978i.bkt.clouddn.com/QQ_Group_2.jpg
   :width: 250px
   :align: center

.. toctree::
   :maxdepth: 2
   :caption: 上手体验篇
	 
	 事前准备 <before_experience/uartCH340_src>
   裸机体验 <experience/standalone_src>
   FreeRTOS <experience/freeRTOS_src>
   
   

.. toctree::
   :maxdepth: 2
   :caption: MicroPython

   x'x'x <MicroPython/xxx文件名>
