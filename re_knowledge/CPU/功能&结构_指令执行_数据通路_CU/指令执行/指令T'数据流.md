<div style="float: left; width: 64%; padding: 1%;">
##  <span style="color: silver;"><span style="color: LightSkyBlue;">指令</span>T'<span style="color: LightSkyBlue;">数据</span><span style="color: silver;">流  

<ul>

### <span style="color: LightSkyBlue;">数据</span><span style="color: silver;">流  

<ul>

- 数据流
  - 定义：
    - 根据指令要求依次访问的<span style="color: LightSkyBlue;">数据</span> <span style="color: LimeGreen;">序列</span>
  - 特点：
    - 在指令执行的不同阶段，数据序列是不同的
    - 不同指令的数据流往往也是不同的
</ul>

### <span style="color: green;">取</span><span style="color: LightSkyBlue;">指</span><span style="color: silver;">T 

<ul>

####  <span style="color: silver;">任务

<ul>

- 根据PC中的内容从主存中 <span style="color: black;">取出</span><span style="color: LightSkyBlue;">指令</span>代码→存放在<span style="color: LightSkyBlue;">I</span><span style="color: LimeGreen;">R</span>中

</ul>

####  <span style="color: silver;">~'<span style="color: LightSkyBlue;">数据</span><span style="color: silver;">流  

<ul>

- PC中存放的是指令的<span style="color: DarkRed;">地址
- 取指令
  - <span style="color: black;">取出</span><span style="color: LightSkyBlue;">指令</span>代码→存放在<span style="color: LightSkyBlue;">I</span><span style="color: LimeGreen;">R</span>中
- PC更新
  - PC+1 
    - 以指向下一条指令
</ul>

#### <span style="color: silver;">~'<span style="color: LightSkyBlue;">数据</span><span style="color: silver;">流向

<ul>

- PC到存储器的数据流向:
  - <span style="color: LightSkyBlue;">P</span><span style="color: LimeGreen;">C</span> → MAR → <span style="color: DarkRed;">地址</span>bus → <span style="color: Gold;">M</span>

- CU发出读命令的流向:
  - CU读命令 →  <span style="color: Gold;">控制</span>bus →  <span style="color: Gold;">M

- 获取指令的流向:
  - 主存 → <span style="color: LightSkyBlue;">数据</span>bus → M<span style="color: LightSkyBlue;">D</span>R → IR（存放指令）

- PC更新流向:
  - CU发出控制信号 → <span style="color: LightSkyBlue;">P</span><span style="color: LimeGreen;">C</span>+1
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/f75084f25f382c3b663c9acfe77f401b2ea0ef4abcdf6fe2e458bbf2de1010ae.jpg)  
图5.4取指周期的数据流  
</ul>

</ul>

###  <span style="color: silver;">间<span style="color: DarkRed;">址</span>T

<ul>

####  <span style="color: silver;">任务

<ul>

- 取操作数<span style="color: LightSkyBlue;">E</span><span style="color: DarkRed;">A</span>
- 以一次间址为例
  - step1:
    - 将指令中的地址码送到MAR
    - 将MAR中的地址码送至地址总线
  - step2:
    - CU向存储器发出读命令
    - 获取有效地址
    - 将有效地址存至MDR
</ul>

#### <span style="color: silver;">~'<span style="color: LightSkyBlue;">数据</span><span style="color: silver;">流向

<ul>

- Ad(IR)(或MDR)到存储器的数据流向:
  - Ad(<span style="color: LightSkyBlue;">I</span><span style="color: LimeGreen;">R</span>)(或MDR) → M<span style="color: DarkRed;">A</span>R → <span style="color: DarkRed;">地址</span>bus →  <span style="color: Gold;">M
- CU发出读命令的流向:
  - CU读命令 →  <span style="color: Gold;">控制</span>bus →  <span style="color: Gold;">M
- 获取有效地址的流向:
  -  <span style="color: Gold;">M</span> → <span style="color: LightSkyBlue;">数据</span>bus → MDR(存放有效地址)
 <span style="font-size: 14px;">[Ad（IR）表示取出IR中存放的指令字的地址字段。

![image](https://bluejedis.github.io/picx-images-hosting/test/image.2yyeudx8js.webp)  
图5.5一次间址周期的数据流  
</ul>

</ul>

###  <span style="color: LimeGreen;">执行</span><span style="color: silver;">T

<ul>

- 任务
  - 取操作数
  - 根据IR中的指令字的操作码通过ALU操作产生执行结果
- 特点
  - 不同指令的执行周期操作不同
  - 因此没有统一的数据流向
</ul>

###  <span style="color: Gold;">中断</span> <span style="color: silver;">T 

<ul>

####   <span style="color: silver;">任务

<ul>

- 处理中断请求
- 假设程序断点存入堆栈中
- 用SP指示栈顶地址
- 进栈操作是先修改栈顶指针，后存入数据

</ul>

#### <span style="color: LightSkyBlue;">数据</span><span style="color: deepskyblue;">流</span><span style="color: green;">向</span>

<ul>

-  <span style="color: Gold;">C</span>U控制将 SP-1
     - SP ① M<span style="color: DarkRed;">A</span>R ② <span style="color: DarkRed;">地址</span>bus ③ 存储器
- CU发出 <span style="color: LimeGreen;">写</span>命令
  - 写命令 ④ 控制总线 ⑤ 存储器
- 程序<span style="color: gray;">断点</span>存入存储器
  - PC ⑥ MDR ⑦ 数据总线 ⑧ 主存
-  <span style="color: Gold;">C</span>U<u>处理</u>中断服务
     - CU(中断服务程序的入口地址) ⑨ PC

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/c5e774da7c287935949863c45b6d8ed1c27c81c7ecb099690202cb499289d6e4.jpg)  
图5.6中断周期的数据流
</ul>

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
