<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span> <span style="color: silver;">控制器  

<ul>

- 实现方式：
  - 采用 <span style="color: Gold;">存储</span>逻辑实现
- 实现原理：
  - 将微<span style="color: LimeGreen;">操作</span>信号<span style="color: LightSkyBlue;">代码</span> <span style="color: LimeGreen;">化</span>
    - every机器指令转化为一段<span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>
  - 将 ~ 存入控制存储器中
- 控制信号生成：
  - <span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">指令</span>
###  <span style="color: silver;">基本概念  

<ul>

- 设计思想：
  - <span style="color: gray;">机器</span>指令与<span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>的关系：
    - every 机器指令 correspond 一个<span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>
  - <span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>的组成：
    - 由若干条微指令构成
    - 每条微指令可 correspond 一个或多个微<span style="color: LimeGreen;">操作</span>命令
<br>
  - 指令<span style="color: green;">执行</span>过程：
    - 本质是执行 corresponding<span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>的过程
  - 存储位置：
    - all <span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>stored in 控制M
  - 应用现状：
    - most pc
####  <span style="color: silver;"><span style="color: purple;">微</span><span style="color: LightSkyBlue;">命令</span>与微<span style="color: LimeGreen;">操作</span>

<ul>

- 微命令：
  - 控制部件向 执行部件发出的各种 控制命令
  - 是构成控制序列的 min单位
  - 例如：
    - 打开/关闭控制门、寄存器打入脉冲
- 微<span style="color: LimeGreen;">操作</span>：
  - 执行部件 receive 微命令后进行的操作
  - 与微命令一一对应
- 微命令分类：
  - 相容性~：
    - 可同时出现完成某些微<span style="color: LimeGreen;">操作</span>
  - 互斥性~：
    - can't同时出现

</ul>

>attention:  
硬布线控制器中也有微命令与微<span style="color: LimeGreen;">操作</span>的概念，并非<span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>控制器的专有概念。  

#### <span style="color: silver;"><span style="color: purple;">微</span><span style="color: RoyalBlue;">指令</span>与微$T$

<ul>

- <span style="color: purple;">微</span><span style="color: RoyalBlue;">指令</span>组成：
  - 操作控制字段（微<span style="color: LimeGreen;">操作</span>码字段）：
    - produce 操作控制<span style="color: Gold;">信号</span>
  - 顺序控制字段（微地址码字段）：
    - 控制下一条微指令地址
- 微周期：
  - <span style="color: LightSkyBlue;">取</span>出& <span style="color: LimeGreen;">执行</span> 一条微指令所需'全部t
  - usually 一个时钟T

</ul>

####  <span style="color: silver;"> <span style="color: Gold;">主</span><span style="color: orange;">M</span>与控制M

<ul>

>pro：主存储器和控制存储器的区别（2017）  
- 主M：
  - 用途：存放程序和数据
  - 位置：CPU外部
  - 实现：用RAM
- 控制M：
  - 用途：存放<span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>
  - 位置：CPU内部
  - 实现：用ROM
  - 单元地址称为微地址

</ul>

<br>

####  <span style="color: silver;">程序与<span style="color: purple;">微</span>程序

<ul>

- 程序：
  - 定义：指令的有序集合
  - 目的：完成特定功能
  - 编制者：软件设计人员
  - 存储位置：
    - 主存
    - 辅存
- <span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span>：
  - 定义：<u>微指令</u>的有序集合
  - 功能：
    - 描述机器指令
    - 是指令的实时解释器
  - 编制者：计算机设计者
  - 存储位置：控制存储器
  - 特点：对程序员透明
</ul>

####   <span style="color: silver;"><span style="color: LimeGreen;">R</span>区分

<ul>

- 地址寄存器（MAR）
  - 功能：存放主存读/写地址

- 微指令地址寄存器（μPC或CMAR）
  - 功能：存放待执行微指令的微地址

- 指令寄存器（IR）
  - 功能：存放从主存读出的指令

- 微指令寄存器（μIR或CMIDR）
  - 功能：存放从控制存储器读出的微指令
</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
