<div style="float: left; width: 64%; padding: 1%;">

# <span style="color: LightSkyBlue;">指令</span> <span style="color: silver;">流水线  

<ul>

- 指令执行方式对比：
  - 单周期处理机：
    - 采用串行方法执行指令
    - 同一时刻CPU只执行<span style="color: gray;">一条</span>指令
    - 功能部件使用率低
  - 现代计算机：
    - 采用<span style="color: LightSkyBlue;">指令</span>流水线技术
      - <u>同一时刻</u>多条指令在不同功能部件中 <span style="color: LimeGreen;">并发</span>执行
    - 优点：
      - 提高功能部件的并行性
      - 提高程序的执行效率

</ul>

##  <span style="color: silver;">基本概念

<ul>

###  <span style="color: silver;"><span style="color: green;">并行</span>性提升方法

<ul>

- 时间维度:
  - 流水线技术
    - 任务<span style="color: gray;">分解</span>为子阶段
    - 子阶段在不同功能部件上执行
    - 可同时执行多个任务的不同阶段
- 空间~:
  - <span style="color: purple;">超</span> <span style="color: Gold;">标量</span>处理机
    - 设置多个<u>相同</u>功能部件
      - 多个功能部件并行工作
    - 实现同类任务的<span style="color: gray;">并行</span>处理

</ul>

###  <span style="color: silver;">指令<span style="color: LimeGreen;">执行</span>阶段

<ul>

- 指令执行过程
  - 分解为若干阶段
    - 每个阶段由相应功能部件完成
  - 各阶段 --构成--> 指令流水线
    - 将各阶段视为流水<span style="color: gray;">段</span>
    - 组合形成完整流水 <span style="color: Gold;">线</span>

- 5个基本流水<span style="color: gray;">段</span>
  - 取指(<span style="color: LightSkyBlue;">I</span><span style="color: GreenYellow;">F</span>)
    - 从指令存储器或Cache中取指令
  - 译码/读寄存器(I<span style="color: deepskyblue;">D</span>) 
    - 操作控制器译码
    - 从寄存器堆取操作数
  - 执行/计算地址( <span style="color: LimeGreen;">EX</span>)
    - 执行运算
    - 计算地址
  - 访存(<span style="color: gray;">MEM</span>)
    - 对存储器进行读/写操作
  - 写回(<span style="color: gray;">W</span><span style="color: GreenYellow;">B</span>)
    - 将执行结果写回寄存器堆

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/4e4d3b2fd28bf010d15ebe5c04890299db4e9d522cfa5616dd58c870df156a3c.jpg)  

>pro：流水线对指令集的要求（2011）  

</ul>

###  <span style="color: silver;"><span style="color: LightSkyBlue;">指令</span><span style="color: GreenYellow;">集</span>要求

<ul>

- 指令长度一致性
  - 应尽量保持一致
  - 有利于简化取指令和译码操作
  - 避免取指时间不一致导致部件复杂
- 指令格式规整性
  - 源寄存器位置应保持相同
  - 便于在指令未知时取寄存器操作数
- LOAD/STORE型指令设计
  - 其他指令不访问存储器
  - 有利于规整地址计算和运算步骤
- 存储对齐要求
  - 数据和指令需"按边界对齐"存放
  - 有利于减少访存次数

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
