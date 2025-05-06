<div style="float: left; width: 64%; padding: 1%;">

###  <span style="color: silver;"><span style="color: deepskyblue;">编码</span>方式  

<ul>

- 目的：
  - 保证速度的情况下缩短微指令字长
- 作用：
  - 对微指令控制字段编码
  - 形成控制信号

####  <span style="color: silver;"><span style="color: gray;">直接</span>~

<ul>

- 特点：
  - 无须译码
  - 每位代表一个微命令
  - 1/0表示选用/不选用
- 优点：
  - 简单直观
  - 执行速度快
  - 操作并行性好
- 缺点：
  - 微指令字长过长
  - 控制存储器容量大

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/c6e197e941e2f1058a37b511cbaa37823f47acc90dd408d7e4f2e9e15c655007.jpg)  
图5.12直接编码方式  
</ul>

####  <span style="color: LightSkyBlue;">字段</span><span style="color: gray;">直接~

<ul>

>pro：字段直接控制的编码方法（2012）  
- 基本方法：
  - 操作控制字段分成<span style="color: gray;">若干</span>小字段
    - <span style="font-size: 12px;">将整个操作控制字段划分为多个独立的小字段
  -  <span style="color: Gold;">互斥</span>性微命令在<span style="color: gray;">同一</span>字段
      - <span style="font-size: 12px;">不能同时执行的微命令放在一个字段中
  - <span style="color: gray;">相容</span>性微命令在<u>不同</u>字段
    - <span style="font-size: 12px;">可以同时执行的微命令分配到不同字段中
  - 每个字段 <span style="color: LimeGreen;">独立</span>编码
    - <span style="font-size: 12px;">各个字段可以单独进行编码
    - <span style="font-size: 12px;">编码方式可以不同
  - 各字段编码含义 <span style="color: GreenYellow;">单独</span>定义
    - 每个字段的编码都有其特定的含义
    - 编码含义相互独立


![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/a8f2b917f211c35fb07f59a18310c4809c207a77d2f9e952f169ab68cecd9625.jpg)  
图5.13字段直接编码方式  

- 分段原则：
  - 命令:
    - 互斥性微命令分在同一段
    - 相容性微命令分在不同段
  - 每段信息位<u>不能太多</u>
  - 每段留出<span style="color: gray;">不操作</span>状态（通常000）

</ul>

#### <span style="color: LightSkyBlue;">字段</span> <span style="color: silver;">间接~

<ul>

- 特点：
  - 一个字段的微命令由<span style="color: gray;">另一字段</span>解释
  - 非直接译码发出微命令
  - <span style="color: gray;">隐式</span>编码
- 优缺点：
  - 优点：进一步缩短微指令字长
  - 缺点：<span style="color: LightSkyBlue;">削弱</span>并行控制能力
  - 用途：作为字段直接编码的辅助手段
</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
