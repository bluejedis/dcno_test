<div style="float: left; width: 64%; padding: 1%;">
## ~ <span style="color: silver;"><span style="color: green;">操作</span>举例  

<ul>

- 总线是一组共享的传输信号线
  - 它不能存储信息
  - 任一时刻也只能有一个部件把信息送到总线上

<span style="font-size: 14px;">以图5.8所示的单总线数据通路为例
- 常见操作的流程及控制信号

>pro：指令执行的节拍及有效控制信号（2009、2015）：指令在取数和执行阶段所用到的部件（2019）  

###  <span style="color: silver;">通用<span style="color: LimeGreen;">R</span>之间传送<span style="color: LightSkyBlue;">数据  

<ul>

- 寄存器和总线之间的控制信号
  - 两种控制信号
    - Rin信号
      - 功能：控制将总线上的信息存到寄存器R中
    - Rout信号
      - 功能：控制将寄存器R的内容送至总线
  - 操作示例：将PC内容送至MAR
    - 流程及控制信号
      - (PC)→MAR
      - PC out MARin
      - PC内容→MAR

</ul>

###  <span style="color: silver;">从<span style="color: Gold;">主</span><span style="color: LimeGreen;">存</span>  <span style="color: GreenYellow;">读取</span>数据  

<ul>

>pro：取指令阶段所需时钟周期分析（2022）  

- 从主存中读取的信息可能是数据或指令
- 以CPU从主存中取指令为例，说明数据在单总线数据通路中的传送过程：
  - 实现该操作的流程及控制信号：
    - 第一步：
      - （PC）→MAR
      - PC out MARin
      - 现行指令地址→MAR
      - 需要1个时钟周期
    - 第二步：
      - MEM（MAR)→MDR
      - （PC)+1→PC
      - MDRin有效
      - CU发出读命令
      - 取出指令后PC+1
      - 需要1个主存周期
    - 第三步：
      - (MDR）→IR 
      - MDR out IR in
      - 现行指令→IR
      - 需要1个时钟周期
</ul>

###  <span style="color: silver;">将数据 <span style="color: black;">写入</span> <span style="color: Gold;">主<span style="color: LimeGreen;">存  

<ul>

- 将寄存器R1的内容写入寄存器R2所指的主存单元：
  - 步骤1：将R1内容送入MDR
    - 控制信号：R1 out MDR in
    - 操作：(R1)→MDR
  - 步骤2：将R2内容送入MAR
    - 控制信号：R2 out MAR in
    - 操作：(R2)→MAR
  - 步骤3：将MDR内容写入主存
    - 控制信号：MDR out有效，CU发出写命令
    - 操作：MDR→MEM(MAR)
</ul>

###  <span style="color: silver;">执行 <span style="color: LimeGreen;">算术</span>或<span style="color: Gold;">逻辑</span>运算  

<ul>

> pro: ALU中设置暂存器的原因（2015、2022）  
  - 在单总线数据通路中：
    - 每一时刻总线上只有一个数据有效
    - ALU运算的特殊要求：
      - ALU是无存储功能的组合逻辑元件
      - 执行运算时需要两个输入端同时有效
      - 解决方案：
        - 第一个操作数：经内部总线送入暂存器Y保存，Y的内容在ALU左输入端始终有效
        - 第二个操作数：经内部总线直接送到ALU右输入端
      - ALU输出的特殊处理：
        - 不能直接与总线相连
        - 原因：输出会通过总线反馈到输入端，影响运算结果
        - 解决方案：将运算结果暂存在暂存器乙中

  - 加法指令ADDACC，R1的执行过程：
    - 功能：将ACC的内容和R1的内容相加并写回ACC
    - 执行步骤：
      - 第一步：
        - 操作：(R1)→Y
        - 控制信号：Rl out Yin
        - 作用：操作数→Y
      - 第二步：
        - 操作：(ACC) $^+$ (Y）→Z
        - 控制信号：ACC out ALU in，CU ALU
        - 作用：结果→Z
      - 第三步：
        - 操作：(Z)→ACC
        - 控制信号：Z out ACC in
        - 作用：结果→ACC

</ul>

>pro：分析减法和自增指令执行所需的时钟周期数（2015）  

<ul>

- 以上3步不能同时执行，否则会引起总线冲突，因此该操作需要3个时钟周期  

</ul>

###  <span style="color: silver;">修改<span style="color: LightSkyBlue;">P</span><span style="color: LimeGreen;">C</span>的值  

<ul>

- 转移指令的作用：
  - 通过修改程序计数器PC的值实现程序的跳转

- 转移指令JMPaddr的操作：
  - 假设转移指令为JIMPaddr：
    - addr是目标转移地址
  - 操作流程：
    - 将指令寄存器IR中的地址字段写入PC
  - 控制信号：
    - Ad(IR)→PC
    - IR out
    - PC in

- 数据通路结构的影响：
  - 直接影响CPU内各种信息的传送路径
  - 数据通路不同：
    - 指令执行过程的微操作序列安排也不同
    - 影响微操作信号形成部件的设计
</ul>

</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
