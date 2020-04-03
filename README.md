# 《油气生产敏捷计算SDK V7.2》用户手册

## 软件介绍 

AgileCalculation SDK V7.2版（以下简称SDK）提供http接口服务，采用post请求模式，json数据格式，实现分布式并行云计算。功能包括：功图诊断、功图计产、全井分析、功图平衡、功率平衡、电功图反演、转速计产、通信计算、时率计算、能耗计算、全井汇总及采集处理和转直角坐标插件等。

## 章节目录

* [第一章：功图软件](./Chapter1/Chapter1.md)
* [第二章：功图平衡](./Chapter2/Chapter2.md)
* [第三章：功率平衡](./Chapter3/Chapter3.md)
* [第四章：电功图反演](./Chapter4/Chapter4.md)
* [第五章：转速计产](./Chapter5/Chapter5.md)
* [第六章：通信计算](./Chapter6/Chapter6.md)
* [第七章：时率计算](./Chapter7/Chapter7.md)
* [第八章：能耗计算](./Chapter8/Chapter8.md)
* [第九章：全井汇总](./Chapter9/Chapter9.md)
* [第十章：插件](./Chapter10/Chapter10.md)

## 版本更新

**SDK V7.2**  
（1）修改了接口URL。  
（2）增加功图软件专业版（Pro版）。  

**SDK V7.1**  
（1）取消MongoDB数据库。  
（2）电参时率、电参能耗、通信计算不再依赖MongDB数据库。  

**SDK V6.7.7**  
（1）功图诊断&计产中增加功图诊断（精简版），只需要功图数据即可对功图工况进行诊断；增加功图诊断（精简版）接口URL。  
（2）修改电参反演输入、输出结构体。更新电参反演接口URL。  

**SDK V6.7**  
（1）增加电参反演计算模块；  
（2）增加通过转速对螺杆泵产量计算。

**SDK V6.6**  
（1）更新单井全天汇总接口URL；  
（2）更新单井全天汇总输入、输出接口格式；  
（3）功图诊断&计产模块中新增有功功率曲线和电流曲线。

**SDK V6.5.3**  
（1）更新电参时率&能耗计算、电参时率&能耗汇总、电参诊断接口URL；  
（2）新增电参时率&能耗计算、电参时率&能耗汇总接口；  
（3）新增通信实时计算、通信汇总接口；  
（4）更新电参诊断接口格式。

**SDK V6.5.2**  
（1）增加采集数据处理模块，将采集的载荷-角度原始数据，经校验、截取、滤波、排序后，转换为载荷-位移数据。同时对于未符合目标采集要求的数据请求，给出采集诊断结果代码和下一步采集的原始数据点数和采集间隔；  
（2）对平衡计算方法进行了修改，采用两种数据源（地面功图、有功功率）、三种计算方法（最大值法、均方根法、平均功率法）。

**SDK V6.5.1**  
（1）新增计算结果状态，包括-44：请求数据读取失败，-55：请求数据json解码失败，-66：井数许可超限，-77：计算异常，-88：响应数据json编码失败；  
（2）功图诊断&计产模块中新增吨液百米耗电量计算、功图面积计算；  
（3）产量汇总计算模块中新增吨液百米耗电量汇总计算；  
（4）新增煤层气井功图诊断及产水量计算、煤层气井诊断结果代码表、煤层气井数据收集表。

**SDK V6.5**  
（1）增加电参智能诊断模块；  
（2）增加电参智能诊断模块配套的MongoDB数据库。

**SDK V6.3**  
（1）增加产量汇总计算模块；  
（2）增加平衡周期性评价模块。

**SDK V6.2**  
（1）增加平衡计算扭矩法（扭矩最大值法、净扭矩均方根法）；  
（2）增加平衡计算功率法。

# 环境要求

本软件适用于Windows、Linux、Mac 64位及32位操作系统，请在购买时注明所需部署机器的版本型号、IP地址以及网卡物理地址。

# 公有云资源

示例：**http://39.98.64.56:18200**

试用：**39.98.64.56:18100**

# 接口模式

| **序号** | **模块**             | **接口URL**                                                   |
|----------|----------------------|---------------------------------------------------------------|
| 1        | 功图软件精简版       | http://IP:端口/api/calc/rpc/fesdiagram/lite                   |
| 2        | 功图软件标准版       | http://IP:端口/api/calc/rpc/fesdiagram/classic                |
| 3        | 功图软件专业版       | http://IP:端口/api/calc/rpc/fesdiagram/pro                    |
| 4        | 功图平衡             | http://IP:端口/api/calc/rpc/fsdiagram/balance/back            |
| 5        | 功率平衡             | http://IP:端口/api/calc/rpc/esdiagram/balance/back            |
| 6        | 电功图反演（自动）   | http://IP:端口/api/calc/rpc/esdiagram/inversion/motorauto     |
| 7        | 电功图反演（半自动） | http://IP:端口/api/calc/rpc/esdiagram/inversion/motorsemiauto |
| 8        | 电功图反演（角位移） | http://IP:端口/api/calc/rpc/esdiagram/inversion/beam          |
| 9        | 转速计产             | http://IP:端口/api/calc/pcp/rpm                               |
| 10       | 通信计算             | http://IP:端口/api/calc/comm                                  |
| 11       | 时率计算             | http://IP:端口/api/calc/run                                   |
| 12       | 能耗计算             | http://IP:端口/api/calc/energy                                |
| 13       | 全井汇总             | http://IP:端口/api/analy/total/well                           |
| 14       | 采集处理             | http://IP:端口/api/plugin/fea2fes                               |
| 15       | 转直角坐标           | http://IP:端口/api/plugin/2xyz                                |

# 软件使用

AgileCalculation软件运行后在指定端口提供http服务，通过post模式进行访问。

![程序图标](./Image/1.png?raw=true)  
*图1 运行程序图标(Windows)*

![状态窗口](./Image/2.png?raw=true)  
*图2 运行状态窗口(Windows)*

# 端口配置说明

软件安装完成之后，在本机防火墙中将**18100** (**SDK端口**)端口设置例外。如果涉及外网访问SDK端口，还需映射端口18100，映射对应的外部端口与内部端口一致。  

# 联系我们 
**名称**：北京科斯奇石油科技有限公司  
**地址**：北京市海淀区安宁庄路26号楼7层705  
**邮编**：100085  
**电话**：010 - 82921872  
**网址**：http://www.cosogoil.com