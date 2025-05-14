<div style="float: left; width: 64%; padding: 1%;">

#  <span style="color: silver;"> <span style="color: Gold;">异常</span>（内中断） 和<span style="color: green;">中断</span>机制  

<ul>

- 现代PC的异常和中断处理系统
  - CPU_data path(内)
    -  <span style="color: Gold;">异常</span>  <span style="color: Gold;">检测</span>/ <span style="color: LimeGreen;">响应</span> 逻辑
  - <span style="color: gray;">外设</span>interface
    - <span style="color: green;">中断</span> <span style="color: gray;">请求</span>/<span style="color: Gold;">控制</span> ~
  - OS
    - 中断服务程序
- process
  - <span style="color: green;">中断</span>硬件电路&~<span style="color: LightSkyBlue;">服务</span>程序 combine


</ul>

##  <span style="color: silver;">基本概念  

<ul>

>pro： 异常事件的性质（2015）  

###  <span style="color: silver;">定义

<ul>

- 异常（内中断）
  - 由CPU内部产生的意外事件
- 中断（<span style="color: green;">外</span>中断）
  - 来自CPU外部的设备向CPU发出的中断请求
  - 通常用于信息的输入和输出
- 区别特点
  - 异常：CPU执行<span style="color: LightSkyBlue;">指令</span>时内部检测到的 <span style="color: LightSkyBlue;">同</span>步 事件
  - 中断：外部设备<span style="color: green;">触发</span>的 <span style="color: SlateBlue;">异</span>步 事件

</ul>

>pro：异常响应的时机（2023）  

###  <span style="color: Gold;">区别

<ul>

1. 关联性
   - 异常：与特定指令相关
   - 中断：与指令无关
2. 检测方式
   - 异常：CPU自身完成
   - 中断：需通过<span style="color: green;">中断</span> <span style="color: LimeGreen;">请求</span> <span style="color: Gold;">线</span>

</ul>

###  <span style="color: silver;">~处理过程

<ul>

- 触发条件
  - 执行第i条指令 <span style="color: Gold;">时</span> 检测到 <span style="color: Gold;">异常</span>
  - 执行第i条指令 <span style="color: gray;">后</span> 发现<span style="color: green;">中断</span>请求
- process
  - CPU<span style="color: gray;">打断</span>当前程序
  - turn to 执行异常/中断处理 程序
- result
  - successfully solved
    - through 异常/中断返回指令
    - 回到第i条或i+1条指令continue执行
  - 致命错误
    - 终止用户程序
- way：通常 OS和driver完成

</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
