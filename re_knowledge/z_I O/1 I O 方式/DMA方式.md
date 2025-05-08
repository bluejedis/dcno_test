<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: silver;"><span style="color: DarkRed;">DMA</span>方式

<ul>

direct memory access

- 特点：
  - 硬件控制特点：
    - 完全由硬件控制成组信息传送

  - 效率优势：
    - 具有程序中断方式优点
    - CPU与外设并行工作

  - 数据传输特点：
    - 外设与内存间有直接数据通路
    - 信息传送不经过CPU

  - 处理开销：
    - 无需保护恢复CPU现场- 适用场景：
  - 磁盘、显卡、声卡、网卡等高速设备
  - 大批量数据传送
- 硬件开销较大
- 中断仅用于故障和正常传送结束处理

### <span style="color: silver;">concept

<ul>

#### <span style="color: Gold;">特点

<ul>

- <span style="color: Gold;">主存</span>和<span style="color: DarkRed;">DMA</span> <span style="color: GreenYellow;">接口</span>之间有直接<span style="color: LightSkyBlue;">数据</span>通路:
        - 数据传送特点：
     - 数据传送路径：
       - 传送数据不需经过CPU
     - 程序执行：
       - 不必中断现行程序
     - <span style="color: LimeGreen;">并行</span>工作能力：
          - I/O与主机并行工作
          - 程序和传送并行工作
- 特点：
  - 主存与CPU关系：
    - 固定联系脱钩
    - 可同时被CPU和外设访问

  - 数据传送特点：
    - 由硬件电路直接实现块传送
    - 需在主存开辟专用缓冲区
    - 传送速度快
    - CPU和外设可并行工作

  - 程序处理要求：
    - 需要程序预处理
    - 需要中断后处理

</ul>

#### <span style="color: silver;">DMA控制器的 <span style="color: Gold;">组成

<ul>

- 基本功能：
  - 接受外设DMA请求并向CPU发出总线请求
  - 接管总线控制权进入DMA操作周期
  - 确定和修改传送数据的主存地址及长度
  - 规定传送方向并执行数据传送
  - 向CPU报告操作结束

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/8522cd40675adcad448679876eac85a3951fa26a1116a5b156080131b7de7bcf.jpg)
图7.6简单的DMA控制器

- 主要组成部件：
  - 主存地址计数器：存放交换数据的主存地址
  - 传送长度计数器：记录传送数据总长度
  - 数据缓冲寄存器：暂存每次传送数据
  - DMA请求触发器：响应I/O设备准备信号
  - "控制/状态"逻辑：指定传送方向和参数修改
  - 中断机构：数据传送完毕后请求中断

</ul>

</ul>

#### <span style="color: silver;"><span style="color: GreenYellow;">传送</span>方式

<ul>

##### <span style="color: silver;"> <span style="color: LimeGreen;">停止</span>CPU访存

<ul>

- 工作过程：
  - I/O设备发出DMA请求
  - CPU放弃总线控制权
  - DMA传送完成后归还控制权

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/6ec983e624318edc13175044b2d5cebc2b11509fa61e7d5aa190149951d0aa44.jpg)
图7.7停止CPU访存

- 优缺点：
  - 优点：控制简单，适合高速I/O设备
  - 缺点：CPU基本处于不工作状态

</ul>

##### <span style="color: silver;"><span style="color: LightSkyBlue;">周期</span><span style="color: gray;">挪用</span>

<ul>

>pro：周期挪用的特点及挪用次数分析（2012、2020、2022）

- 工作特点：
  - I/O访存优先级高于CPU
  - 单字传送方式
  - 传送完立即释放总线
- 三种情况：
  - CPU不在访存时无冲突
  - CPU正在访存需等待周期结束
  - 同时请求时CPU暂时放弃控制权

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/f1cb1aeae481f0ba9014acc77c9a136f81250ae56fe2f1afdbaaae40727dad9f.jpg)
图7.8周期挪用

- 优缺点：
  - 优点：兼顾I/O传送和系统效率
  - 缺点：频繁申请归还总线控制权

</ul>

##### <span style="color: silver;"><span style="color: DarkRed;">DMA</span> <span style="color: GreenYellow;">CPU</span><span style="color: Goldenrod;">交替</span>访存

<ul>

- 工作方式：
  - CPU工作周期 → 两个时间片
  - CPU和DMA轮流访存
  - 适用于 <span style="color: GreenYellow;">CPU</span>周期 > <span style="color: Gold;">主存</span>周期

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/ffcf3f4a552e1dfafa466c4a36585fb69c056f358e0b653e960ca62e1a3344ba.jpg)
图7.9DMA与CPU交替访存

- 优缺点：
  - 优点：无需申请归还总线，传送速率高
  - 缺点：硬件逻辑复杂

>pro：DMA方式的效率分析及相关计算（2011、2018）

- 【例7.4】问题分析：
  - 计算机主频：500 MHz。
  - CPI（每条指令周期数）：4。
  - 外设数据率：40 MB/s。
  - I/O接口数据端口大小：32位。
  - DMA方式，每次DMA传送块大小：1000B。
  - DMA预处理和后处理总时钟周期数：500。
  - 问题：CPU用于该外设I/O的时间占CPU总时间的百分比是多少？

- 解答思路：
  - 计算外设每秒的DMA次数。
  - 确定DMA方式下CPU处理的总时钟周期数。
  - 计算CPU用于外设I/O的总时间。
  - 计算CPU用于外设I/O的时间占CPU总时间的百分比。

- 计算过程：
  - 外设每秒DMA次数：40MB/s ÷ 1000B = 40000次。
  - CPU用于外设I/O的总时钟周期数：40000次 × 500周期/次 = 2 × 10^7个时钟周期。
  - CPU用于外设I/O的时间占CPU总时间的百分比：2 × 10^7 ÷ 500M = 4%。

</ul>

</ul>

### <span style="color: silver;"><span style="color: DarkRed;">DMA</span>的 <span style="color: GreenYellow;">传送</span>过程

<ul>

>pro：DMA方式的传送过程（2019）

#### <span style="color: silver;">concept

<ul>

图7.10所示为DMA的数据传送流程，分为
- <span style="color: gray;">预</span>处理
- <span style="color: LightSkyBlue;">数据</span>传送
- <span style="color: Gold;">后</span>处理

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/a3b3e6b4a23a187f89eda625719dd33923705cfd841a0f99f9153f246e978d6b.jpg)
图7.10DMA的传送流程

</ul>

#### <span style="color: silver;">steps

<ul>

##### <span style="color: silver;"><span style="color: gray;">预</span>处理

<ul>

- CPU完成必要准备工作
  - 初始化DMA控制器中的有关寄存器
  - 设置传送方向
  - 测试并启动设备
- 后续流程
  - CPU继续执行原程序
  - I/O设备准备好数据时
    - 向DMA控制器发送DMA请求
    - DMA控制器向CPU发出总线请求

</ul>

##### <span style="color: silver;"><span style="color: LightSkyBlue;">数据</span> <span style="color: GreenYellow;">传送</span>

<ul>

- 传送特点
  - 以数据块为基本传送单位
  - 通过循环实现数据输入/输出操作
  - 完全由DMA(硬件)控制

</ul>

##### <span style="color: silver;"> <span style="color: Gold;">后</span>处理

<ul>

- step:
  - DMA控制器向CPU发送中断请求
  - CPU执行中断服务程序
    - 校验数据(出错则转诊断程序)
    - 其他后处理工作
- 效率:
  - 整个数据块传送过程不需CPU参与
  - CPU仅在初始化和结束处理时介入
  - CPU用于I/O的开销非常小

</ul>

</ul>

### <span style="color: silver;"><span style="color: DarkRed;">DMA</span>方式 & 中断方式的区别

<ul>

>pro：中断方式与DMA方式的区别（2013、2023）

- 程序切换与现场保护
  - 中断方式需要程序切换，需保护和恢复现场
  - DMA方式不中断现行程序，无需保护现场
- 响应时机
  - 中断请求：仅在指令执行结束时响应
  - DMA请求：可在任意机器周期结束时响应
- CPU干预程度
  - 中断传送需要CPU干预
  - DMA传送不需CPU干预，传输速率高
- 优先级关系
  - DMA请求优先级高于中断请求
- 处理能力
  - 中断方式可处理异常事件
  - DMA方式仅用于大批数据传送
- 传送方式
  - 中断方式：程序传送
  - DMA方式：硬件传送

>pro：DMA与CPU请求总线的优先级对比（2012、2022）

</ul>

</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
