<div style="float: left; width: 64%; padding: 1%;">

#  <span style="color: silver;"><span style="color: RoyalBlue;">多</span>处理器

<ul>

>pro： 多处理器的基本概念（2022）  

##  <span style="color: silver;">SISD、SIMD、MISD、MIMD

<ul>

- 基于 <span style="color: LightSkyBlue;">I</span> 流和数据流的数量：
  - SISD(单  <span style="color: LightSkyBlue;">I</span> 流 单 数据流)
  - SIMD 
  - MISD
  - MIMD
- 分类对应关系：
  - 常规单处理器 → SISD
  - 常规多处理器 → MIMD

###   <span style="color: silver;"> <span style="color: Lime;">S</span>I<span style="color: Lime;">S</span>D  

<ul>

- SISD是<span style="color: gray;">传统</span>的事行计算机结构
  - 特点：
    - 仅包含一个处理器和一个存储器
    - 一段时间内仅执行一条 <span style="color: LightSkyBlue;">I</span> 
    - 按 <span style="color: LightSkyBlue;">I</span> 流规定的顺序串行执行 <span style="color: LightSkyBlue;">I</span> 流中的若干 <span style="color: LightSkyBlue;">I</span> 
  - 优化方式：
    - 流水线方式提高速度
    - 多个功能部件
    - 多模块 交叉方式组织M

</ul>

###  <span style="color: silver;"> <span style="color: Lime;">S</span>I<span style="color: purple;">M</span>D 

<ul>

- SIMD定义：
  - 一个 <span style="color: LightSkyBlue;">I</span> 流同时对多个数据流进行处理
  - (也称 <span style="color: LightSkyBlue;">数据</span><span style="color: Gold;">级</span><span style="color: green;">并行</span>技术
- 结构组成：
  - 一个 <span style="color: LightSkyBlue;">I</span> 控制部件
  - 多个处理单元
    - 每个单元执行相同 <span style="color: LightSkyBlue;">I</span> 
    - 拥有独立的地址  <span style="color: LimeGreen;">R</span> 
    - 处理不同的数据
- 应用效率：
  - 最高效：<span style="color: green;">for</span>循环处理数组
  - 最低效： <span style="color: Gold;">case</span>或 <span style="color: Gold;">switch</span>语句

####  <span style="color: silver;"><span style="color: gray;">向量</span> <span style="color: Gold;">处理</span>器

<ul>

- 定义：
  - SIMID的变体
  - 直接操作一维数组 <span style="color: LightSkyBlue;">I</span> 集的CPU
- 工作原理：
  - 将数据组 按顺序 放入 向量  <span style="color: LimeGreen;">R</span> 
    - 以流水化方式依次操作
  - 结果写回  <span style="color: LimeGreen;">R</span> 
- 应用优势：
  - 特定工作环境中性能提升显著
  - 尤其在数值模拟等领域

</ul>

</ul>

###  <span style="color: silver;"><span style="color: purple;">M</span>I<span style="color: Lime;">S</span>D 

<ul>

- 定义：
  - 同时执行多条 <span style="color: LightSkyBlue;">I</span> ，处理同一个数据
- 实际上不存在这样的计算机

</ul>

###  <span style="color: silver;"><span style="color: purple;">M</span>I<span style="color: purple;">M</span>D 

<ul>

- 定义：同时执行多条 <span style="color: LightSkyBlue;">I</span> 分别处理多个不同的数据

####  <span style="color: silver;">多<span style="color: gray;">计算机</span>系统

<ul>

- 特点：
  - 每个节点have私有M
  - 独立主M地址空间
  - through 消息传递进行数据传送
    - 也称 消息传递MIMD

</ul>

####  <span style="color: silver;">多<span style="color: Gold;">处理器</span>系统

<ul>

- 特点：
  -  <span style="color: LimeGreen;">共享</span>M多处理器( <span style="color: LimeGreen;">S</span><span style="color: Gold;">M</span>P)系统
     - have共享的 <span style="color: LimeGreen;">单一</span><span style="color: DarkRed;">地址</span>空间
  - through存取 <span style="color: LightSkyBlue;">I</span> 访问所有存储器
    - 也称共享存储MIMD

</ul>

</ul>

###  <span style="color: silver;">并行计算模式对比( <span style="color: Lime;">S</span>I<span style="color: purple;">M</span>D vs <span style="color: purple;">M</span>I<span style="color: purple;">M</span>D)

<ul>

- SIMD： 
  - <span style="color: LimeGreen;">数据</span>级并行模式
- MIMD： 
  - <span style="color: Gold;">线程</span>级或更高级别的并行计算模式

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
