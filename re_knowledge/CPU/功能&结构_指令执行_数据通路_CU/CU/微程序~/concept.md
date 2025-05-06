<div style="float: left; width: 64%; padding: 1%;">
## <span style="color: SlateBlue;">微</span><span style="color: LightSkyBlue;">程序</span> <span style="color: silver;">控制器  

<ul>

- 实现方式：
  - 采用 <span style="color: Gold;">存储</span>逻辑实现
- 实现原理：
  - 将微操作信号<span style="color: LightSkyBlue;">代码</span> <span style="color: LimeGreen;">化</span>
  - 每条机器指令转化为一段微程序
  - 将微程序存入控制存储器中
- 控制信号生成：
  - 微操作控制信号由微指令产生
###  <span style="color: silver;">基本概念  

<ul>

- 设计思想：
  - 机器指令与微程序的关系：
    - 每条机器指令对应一个微程序
  - 微程序的组成：
    - 由若干条微指令构成
    - 每条微指令可对应一个或多个微操作命令
  - 指令执行过程：
    - 本质是执行对应微程序的过程
  - 存储位置：
    - 所有微程序存放在控制存储器中
  - 应用现状：
    - 目前大多数计算机都采用此技术
####  <span style="color: silver;"><span style="color: purple;">微</span><span style="color: LightSkyBlue;">命令</span>与微 <span style="color: LimeGreen;">操作

<ul>

- 微命令：
  - 控制部件向执行部件发出的各种控制命令
  - 是构成控制序列的最小单位
  - 例如：打开/关闭控制门、寄存器打入脉冲
- 微操作：
  - 执行部件收到微命令后进行的操作
  - 与微命令一一对应
- 微命令分类：
  - 相容性微命令：可同时出现完成某些微操作
  - 互斥性微命令：不允许同时出现

</ul>

>attention:  
硬布线控制器中也有微命令与微操作的概念，并非微程序控制器的专有概念。  

#### <span style="color: silver;"><span style="color: purple;">微</span><span style="color: RoyalBlue;">指令</span>与微$T$

<ul>

- 微指令组成：
  - 操作控制字段（微操作码字段）：产生操作控制信号
  - 顺序控制字段（微地址码字段）：控制下一条微指令地址
- 微周期：
  - 取出并执行一条微指令所需的全部时间
  - 通常为一个时钟周期

</ul>

####  <span style="color: silver;"> <span style="color: Gold;">主</span><span style="color: orange;">M</span>与控制M

<ul>

>pro：主存储器和控制存储器的区别（2017）  
- 主M：
  - 用途：存放程序和数据
  - 位置：CPU外部
  - 实现：用RAM
- 控制M：
  - 用途：存放微程序
  - 位置：CPU内部
  - 实现：用ROM
  - 单元地址称为微地址

</ul>

####  <span style="color: silver;">程序与<span style="color: purple;">微</span>程序

<ul>

- 程序：
  - 定义：指令的有序集合
  - 目的：完成特定功能
  - 编制者：软件设计人员
  - 存储位置：
    - 主存
    - 辅存
- 微程序：
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
