<div style="float: left; width: 64%; padding: 1%;">

###  <span style="color: silver;"><span style="color: DarkRed;">地址</span>形成方式  

<ul>

后继微地址的形成主要有以下几个基本类型：  

####  <span style="color: silver;">后<span style="color: purple;">继</span>地址字段 point ←directly

<ul>

- 在μ<span style="color: LightSkyBlue;">I</span>格式中set 一个后继地址字段
  - 用于直接指示<span style="color: gray;">下一条</span>μ<span style="color: LightSkyBlue;">I</span>的<span style="color: DarkRed;">地址</span>
- 由μ<span style="color: LightSkyBlue;">I</span>的后继地址字段直接 point 后继μ<span style="color: LightSkyBlue;">I</span>的地址
  - 直接从字段中获取地址信息
  - 无需额外计算或转换
- also called as<span style="color: DarkRed;">断定</span>方式
  - cause地址is确定的
  - 不依赖于其他条件
</ul>

####  <span style="color: silver;">由 机器<span style="color: LightSkyBlue;">指令</span>操作码形成

<ul>

  - 机器指令从IR取出
  - 通过微地址形成部件处理：
    - I： <span style="color: LimeGreen;">操作</span><span style="color: LightSkyBlue;">码</span>
    - O：对应机器指令微程序的首地址
</ul>

####  <span style="color: silver;">增量 <span style="color: LimeGreen;">计数器</span>法

<ul>

- 即 $(\mu\mathrm{PC})+1{\rightarrow}\mu\mathrm{PC}$
- applicable to后继μ<span style="color: LightSkyBlue;">I</span>地址is连续的情况

</ul>

####  <span style="color: Gold;">标志</span> <span style="color: silver;">决定分支转移

<ul>

- according to <span style="color: Gold;">标志</span>
  - decide 下一条μ<span style="color: LightSkyBlue;">I</span>分支转移的地址

</ul>

#### <span style="color: green;">硬件</span> <span style="color: silver;">直接产生

<ul>

- 电源加电后，第一条μ<span style="color: LightSkyBlue;">I</span>的地址 by 专门的<span style="color: green;">硬件</span><span style="color: gray;">电路</span>产生
  - → $\mu\mathrm{PC}$
- this address is
  - 取指T 微程序的入口地址
</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
