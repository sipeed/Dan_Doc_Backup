搭建裸机开发环境
=================================================

.. contents:: 本文目录

下载sdk
-------------------------------------------------

k210的sdk在linux和windows下都可以进行开发

如果是在linux系统下，可以进行以下步骤下载k210的sdk

1. 使用命令从网络上下载k210的裸机开发sdk 
``wget https://s3.cn-north-1.amazonaws.com.cn/dl.kendryte.com/documents/kendryte-standalone-sdk-0.3.0.zip`` 

2. 解压sdk
``unzip kendryte-standalone-sdk-0.3.0.zip`` 

3. 进入目录，目录内容如下所示
``cd kendryte-standalone-sdk-0.3.0 && ls`` 

:: 

	 CHANGELOG.md  cmake  CMakeLists.txt  lds  lib  LICENSE  README.md  src

（window下待补充...）

编写程序
-------------------------------------------------

如果是在linux系统下，可以通过以下操作进行代码编写

1. 以hello_world为例，在 *kendryte-standalone-sdk-0.3.0* 目录下使用命令创建目录 
``cd src && mkdir hello_world`` 

2. 使用命令进入 *hello_world* 目录，在该目录放入你自己的main.c文件及其他.c或.h文件并进行编辑
``cd hello_world`` 

3. 创建并编辑main函数并输入代码，以hellow_world为例，输入在main.c中输入以下代码并保存
``vim main.c`` 

.. code-block:: code

		/****************测试代码************************/
		#include <stdio.h>
		#include "sleep.h"
		#include "encoding.h"
		int main()
		{
		    uint64_t core_id = current_coreid();
		    if (core_id == 0)
		    {
		        printf("Core 0 Hello, world!\n");
		    }
		    else
		    {
		        msleep(100);
		        printf("Core 1 Hello, world!\n");
		    }
		    while (1)
		        ;
		    return 0;
		}

（window下待补充...）



编译程序
-------------------------------------------------

如果是在linux系统下，可以通过以下操作进行编译步骤

1. 下载k210编译工具链kendryte-toolchain.tar.gz
``wget https://s3.cn-north-1.amazonaws.com.cn/dl.kendryte.com/documents/kendryte-toolchain.tar.gz`` 

2. 解压工具链
``tar xvf kendryte-toolchain.tar.gz``

此时还需要再配置环境变量
``export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:your_toolchain_path/bin/``

.. note:: 其中your_toolchain_path为编译工具链的存放路径

3. 进入kendryte-standalone-sdk-0.2.1目录，在该目录下使用命令
``mkdir build && cd build``

4. 在build目录下使用
``cmake .. -DPROJ=<ProjectName> -DTOOLCHAIN=YourToolchainPath/bin && make``

.. note:: 其中ProjectName为工程名，YourToolchainPath为编译工具链的路径
	
5. 以hello_word为例，使用以下编译命令，完成之后再build目录下将生成以hello_world.bin文件，这就是我们要烧录的二进制文件
``cmake .. -DPROJ=hello_world -DTOOLCHAIN=/opt/riscv-toolchain/bin && make``

烧录程序
-------------------------------------------------

如果在linux下，我们需要先下载 `烧录脚本  <https://fdvad021asfd8q.oss-cn-hangzhou.aliyuncs.com/Sipeed_M1_hardware/isp_auto.py>`_ 

使用命令下载脚本
``wget http://pgeza64pd.bkt.clouddn.com/isp_auto.py``

使用以下命令可以直接烧录二进制
``python3 your_isp_auto_path -d /dev/ttyUSB0  your_bin_path -b 200000``

.. note:: 其中your_isp_auto_path为isp_auto.py的存放路径，your_bin_path为二进制文件的路径

以笔者的hello_world为例，则命令如下
``python3 /home/isptools/isp_auto.py  -d /dev/ttyUSB0  /opt/k210_sdk/build/hello_world.bin -b 200000``

如果是在window下，则可以一键烧录二进制文件，我们先下载 `烧录软件  <https://s3.cn-north-1.amazonaws.com.cn/dl.kendryte.com/documents/K-Flash-V0.3.0.zip>`_ 

点击蓝色字烧录软件即可下载

打开烧录软件，点击图中红圈选中二进制文件所在路径

.. figure:: https://fdvad021asfd8q.oss-cn-hangzhou.aliyuncs.com/Sipeed_M1_hardware/kflash_path.jpg
   :width: 250px
   :align: center
  
再选择通信串口

.. figure:: https://fdvad021asfd8q.oss-cn-hangzhou.aliyuncs.com/Sipeed_M1_hardware/kflash_dev.jpg
   :width: 250px
   :align: center

波特率选择2000000

.. figure:: https://fdvad021asfd8q.oss-cn-hangzhou.aliyuncs.com/Sipeed_M1_hardware/kflash_rate.jpg
   :width: 250px
   :align: center

点击flash即可烧录，烧录过程大概几十秒

运行demo
-------------------------------------------------

烧录完毕之后，上电即可运行demo

为了查看demo的输出信息，我们需要使用串口调试助手，选中荔枝丹对应的串口

因为上电瞬间就会输出信息，此时荔枝丹串口还没接入上位机，所以我们需要在接入上位机后按下板子上的RST键重启荔枝丹

此时即可看到如下调试信息

.. code-block:: debug

		Core 0 Hello, world!
		Core 1 Hello, world!

恭喜你，已经完成了荔枝丹的裸机demo开发，请继续你的AI探索之旅吧！！

.. note:: 可以参考sdk中README.md文件

.. admonition:: 交流与答疑

    对于本章内容，如有疑问，欢迎到 `荔枝丹 | 建议与讨论区 <http://bbs.lichee.pro/t/sipeed-m1>`_ 提问或分享经验。







