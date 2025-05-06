<div style="float: left; width: 64%; padding: 1%;">

###  <span style="color: silver;"><span style="color: DarkRed;">地址</span>形成方式  

<ul>

后继微地址的形成主要有以下几个基本类型：  

####  <span style="color: silver;">后<span style="color: purple;">继</span>地址字段指出

<ul>

- 在微指令格式中设置一个后继地址字段
  - 用于直接指示<span style="color: gray;">下一条</span>微指令的<span style="color: DarkRed;">地址</span>
- 由微指令的后继地址字段直接指出后继微指令的地址
  - 直接从字段中获取地址信息
  - 无需额外计算或转换
- 也称断定方式
  - 因为地址是确定的
  - 不依赖于其他条件
</ul>

####  <span style="color: silver;">由 机器<span style="color: LightSkyBlue;">指令</span>操作码形成

<ul>

  - 机器指令从指令寄存器取出
  - 通过微地址形成部件处理：
    - 输入：操作码
    - 输出：对应机器指令微程序的首地址
</ul>

####  <span style="color: silver;">增量 <span style="color: LimeGreen;">计数器</span>法

<ul>

- 即 $(\mu\mathrm{PC})+1{\rightarrow}\mu\mathrm{PC}$
- 适用于后继微指令地址是连续的情况

</ul>

####  <span style="color: Gold;">标志</span> <span style="color: silver;">决定分支转移

<ul>

- 根据各种 <span style="color: Gold;">标志</span>决定下一条微指令分支转移的地址

</ul>

#### <span style="color: green;">硬件</span> <span style="color: silver;">直接产生

<ul>

- 电源加电后，第一条微指令的地址可由专门的<span style="color: green;">硬件</span><span style="color: gray;">电路</span>产生
- 并送至 $\mu\mathrm{PC}$
- 这个地址即为取指周期微程序的入口地址
</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
