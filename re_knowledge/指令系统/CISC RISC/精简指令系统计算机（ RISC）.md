<div style="float: left; width: 64%; padding: 1%;">

##   <span style="color: silver;"><span style="color: LimeGreen;">精简</span>指令系统计算机（ <span style="color: LimeGreen;">R</span>ISC）</span>
 <span style="color: LimeGreen;">Reduced</span> Instruction Set Computer

<ul>

###  <span style="color: silver;">设计理念

<ul>

- 中心思想：
  - 要求指令系统 <span style="color: LimeGreen;">简化
  -  <span style="color: silver;">尽量使用</span>寄存器-寄存器操作指令
  - 指令格式力求<u>一致</u>

</ul>

###  <span style="color: Gold;">特点</span>

<ul>

- <span style="color: LightSkyBlue;">设计
  -  <span style="color: silver;">选取使用<span style="color: orange;">频率</span><span style="color: black;">最高</span>的 <span style="color: LimeGreen;">简单</span><span style="color: LightSkyBlue;">指令</span>
  - <span style="color: purple;">复杂</span>~ 由  <span style="color: LimeGreen;">简单</span>~ <span style="color: green;">组合</span> <span style="color: Gold;">实现

-  <span style="color: Gold;">特性
   - <span style="color: LightSkyBlue;">长度</span>fix
   -  <span style="color: LimeGreen;">格式</span><span style="color: green;"> 种类</span>少
   - <span style="color: green;">寻址</span>方式~

- 内存<span style="color: green;">访问
  - 只有LOAD/STORE指令可访存
  - 其余指令在寄存器间进行

-  <span style="color: GreenYellow;">硬件</span> <span style="color: Gold;">特点</span>
   - CPU中通用寄存器数量多
   - 采用指令流水线技术
   - 大部分指令在一个时钟周期内完成
   - 以硬布线控制为主
   - 不用或少用微程序控制

- 编译优化
  - 特别重视编译优化工作
  - 以减少程序执行时间

</ul>

###   <span style="color: silver;"><span style="color: Gold;">兼容性</span>问题

<ul>

-  <span style="color: silver;"><span style="color: purple;">C</span>ISC <span style="color: black;">大多能</span>实现软件兼容
-   <span style="color: silver;"><span style="color: LimeGreen;">R</span>ISC简化指令系统，与老机器 <span style="color: black;">不</span>~
-  <span style="color: silver;">现状：
   -  <span style="color: black;">Intel</span>几乎一统江湖
   -  <span style="color: black;">早期</span>软件 <span style="color: black;">多</span>基于<span style="color: purple;">C</span>ISC设计
   - <span style="color: LightSkyBlue;">现代</span><span style="color: purple;">C</span>ISC已 <span style="color: black;">融合</span> <span style="color: LimeGreen;">R</span>ISC特性，性能差距缩小

</ul>

</ul>

</ul>
</div>s
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
