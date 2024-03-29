# LongScope - an Automatic Measurement Solution

- [LongScope - an Automatic Measurement Solution](#longscope---an-automatic-measurement-solution)
  - [简介](#简介)
  - [当前支持的型号](#当前支持的型号)
  - [更新计划](#更新计划)
  - [环境配置（开发者）](#环境配置开发者)
  - [环境配置（非开发者）](#环境配置非开发者)


## 简介
LongScope用于示波器的自动化或远程测量。程序由MATLAB和Python编写，通过VISA接口连接示波器及其它类似设备。用户可以访问测量仪器的完整数据，或通过图形化界面远程设置仪器功能。

![Running Example](<Assets/Running Example.png>)
![Usage Example](<Assets/Usage Example.jpg>)


- **便捷地访问原始、完整的测量数据。** LongScope允许直接从仪器读取超过10MB（取决于仪器存储深度）的原始数据，并以.CSV等格式保存。
- **直接连接MATLAB/Python程序。** LongScope运行在MATLAB平台上，用户程序可以将其用作透明的仪器接口，实时分析或转发测量数据。
- **支持多种示波器型号。** LongScope使用通用的VISA（Virtual instrument software architecture，虚拟仪器接口）连接示波器，并兼容多个厂商的应用层协议。

LongScope是面对对象的，每种仪器的方法封装在仪器型号对应的类中，这些类继承自一个统一的抽象类InstDev，抽象类规定了每种仪器必须实现的方法（例如波形读取）以及必须维护的属性（例如当前的触发电平）。虽然每种仪器使用的命令格式可能不同，不同仪器类的方法是以相同格式调用的，各种属性也以相同格式存储。因此，与仪器的通信对于应用层（LongScope的GUI或其它用户程序）是透明的。

## 当前支持的型号

- [x] RIGOL DS1000Z Series (verified on DS1202Z-E)
- [ ] SIGLENT SDS1000X Series (to be verified on SDS1202X-C)
- [ ] Keysight InfiniiVision 1000 X-Series (to be verified on DSOX1204A)


## 更新计划

- [x] Matlab GUI
- [ ] Python Lib *(Ongoing)*
- [ ] Python GUI  

## 环境配置（开发者）

1. **下载LongScope**

        git clone https://github.com/Pieski/LongScope.git

2. **配置虚拟环境** *(Recommended)*

        python -m venv .
        ./Scripts/activate

3. **安装环境** 
   
    [![Static Badge](https://img.shields.io/badge/Github-pyvisa-blue)](https://github.com/pyvisa/pyvisa)
    [![Static Badge](https://img.shields.io/badge/Github-numpy-green)](https://github.com/numpy/numpy)
    [![Static Badge](https://img.shields.io/badge/PyPI-PyQt-blue)](https://pypi.org/project/PyQt6/)

        pip install -r ./requirements.txt

4. **安装Matlab Instrument Control Toolbox**

5. **下载并安装NI-VISA**
   
   [![Static Badge](https://img.shields.io/badge/Click%20to%20Download-NI%20VISA-green)](https://www.ni.com/zh-cn/support/downloads/drivers/download.ni-visa.html#521671) 

   目前版本由NI-VISA提供用于SCPI命令的VISA协议驱动。

6. **安装各厂商的IVI驱动**（如果有）

        Rigol：https://www.rigolna.com/download/
   
   
## 环境配置（非开发者）

**现阶段建议所有用户按上述开发者方法下载并配置LongScope，因为Matlab和Python程序的封装都尚未完成。**

1. **下载LongScope**

    在Github Releases中找到最新版本的安装文件（非Source code.zip）