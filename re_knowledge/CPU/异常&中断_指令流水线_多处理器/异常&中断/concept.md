<div style="float: left; width: 64%; padding: 1%;">

#  <span style="color: silver;"> <span style="color: Gold;">异常</span>（内中断） 和<span style="color: green;">中断</span>机制  

<ul>

- 现代计算机的异常和中断处理系统
  - CPU数据通路
    - 异常  <span style="color: Gold;">检测</span>/ <span style="color: LimeGreen;">响应</span> 逻辑
  - <span style="color: gray;">外设</span>接口
    - 中断 <span style="color: gray;">请求</span>/<span style="color: Gold;">控制</span> 逻辑
  - 操作系统
    - 中断服务程序
- 处理过程
  - 中断硬件电路和中断服务程序有机结合
  - 共同完成异常和中断的处理

</ul>

##  <span style="color: silver;">基本概念  

<ul>

>pro： 异常事件的性质（2015）  

###  <span style="color: silver;">定义

<ul>

- 异常（内中断）
  - 由CPU内部产生的意外事件
- 中断（外中断）
  - 来自CPU外部的设备向CPU发出的中断请求
  - 通常用于信息的输入和输出
- 区别特点
  - 异常：CPU执行指令时内部检测到的 <span style="color: LightSkyBlue;">同</span>步 事件
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
  - 执行第i条指令 <span style="color: Gold;">时</span> 检测到异常
  - 执行第i条指令 <span style="color: gray;">后</span> 发现中断请求
- 处理流程
  - CPU<span style="color: gray;">打断</span>当前程序
  - turn to 执行异常/中断处理 程序
- 处理结果
  - 成功解决
    - 通过异常/中断返回指令
    - 回到第i条或i+1条指令继续执行
  - 致命错误
    - 终止用户程序
- 处理方式：通常 OS和driver完成

</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
