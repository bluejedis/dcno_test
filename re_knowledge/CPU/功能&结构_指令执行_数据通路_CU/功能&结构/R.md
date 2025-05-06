<div style="float: left; width: 64%; padding: 1%;">

##  <span style="color: silver;">CPU的 <span style="color: LimeGreen;">R 

<ul>

>pro：汇编程序员可见的寄存器（2010、2015、2021）  

- C按汇编语言（或机器语言）程序whether <span style="color: black;">可</span><span style="color: green;">访问</span>，分为两类：
  - 用户 <span style="color: black;">可</span><span style="color: LimeGreen;">见</span>寄存器
    - 特点：
      - 可对这类寄存器编程
      - 可通过使用这类寄存器减少对主存储器的访问次数
    - 包括：
      - 通用寄存器组（含基址/变址寄存器）
      - 程序状态字寄存器
      - 程序计数器
      - 累加寄存器
      - 移位寄存器
  - 用户<span style="color: purple;">不</span><span style="color: black;">可</span><span style="color: LimeGreen;">见</span>寄存器
    - 特点：
      - 对用户是透明的
      - 不可对这类寄存器编程
      - 被控制部件使用，以控制CPU的操作
    - 包括：
      - 存储器地址寄存器
      - 存储器数据寄存器
      - 指令寄存器
      - 暂存寄存器
>pro：CPU中各种寄存器的作用（2013）  

###  <span style="color: silver;"><span style="color: LightSkyBlue;">A</span><span style="color: LimeGreen;">L</span>U中的 <span style="color: LimeGreen;">R</span>

<ul>

####  <span style="color: silver;">通用<span style="color: LimeGreen;">R</span>组（GPRs）

<ul>

- 功能：
  - 存放操作数：
    - 源操作数
    - 目的操作数
    - 中间结果
  - 存放地址信息：
    - 常见寄存器如：
      - AX
      - BX
      - CX
      - DX
      - SP
- 访问方式：
  - 指令中指定寄存器 <span style="color: black;">编号</span>
  - 通过编号 确定访问的具体寄存器
- SP特点：
  - 堆栈指针
  - 指示栈顶地址
</ul>

####   <span style="color: silver;"><span style="color: GreenYellow;">累加</span><span style="color: LimeGreen;">R</span>（ACC）

<ul>

- 功能：
  - 通用寄存器
  - 存储：
    - 暂时存放ALU运算的结果
</ul>

####  <span style="color: silver;"><span style="color: green;">移</span>位~（<span style="color: green;">S</span>R）

<ul>

- 功能：
  - 存储：
    - 可用来存放操作数
  - 移位操作：
    - 在控制信号作用下
    - 寄存器中的数据可：
      - 向左移位
      - 向右移位
</ul>

####  <span style="color: silver;">暂 <span style="color: Gold;">存</span>~

<ul>

- 功能：
  - 暂存数据：
    - 来源：
      - 数据总线
      - 通用寄存器
    - 目的：在取出下一个操作数时将其同时送入ALU
  - 可见性：
    - 对应用程序员是透明的（不可见）
</ul>

####  <span style="color: silver;"><span style="color: LightSkyBlue;">程序</span> <span style="color: Gold;">状态</span>字~（<span style="color: LightSkyBlue;">P</span><span style="color: Gold;">S</span>W）

<ul>

- 功能和组成：
  - 保留 由算术/逻辑运算指令 或 测试指令 的运行结果 而建立的各种 <span style="color: Gold;">状态</span><span style="color: gray;">信息</span>
  - 包含的标志位：
    -  <span style="color: LimeGreen;">溢出</span>标志（ <span style="color: LimeGreen;">O</span>F）
    -  <span style="color: Gold;">符号</span>标志（ <span style="color: Gold;">S</span>F） 
    - <span style="color: LightSkyBlue;">零</span>标志（<span style="color: LightSkyBlue;">Z</span>F）
    - <span style="color: green;">进位</span>标志（<span style="color: green;">C</span>F）
  - 存储方式：
    - 每个标志位由一位触发器来保存
    - 所有标志位组合在一起构成程序状态字
</ul>

</ul>

###  <span style="color: silver;"> <span style="color: Gold;">C</span>U中的 <span style="color: LimeGreen;">R

<ul>

>pro：PC和<span style="color: LightSkyBlue;">I</span><span style="color: LimeGreen;">R</span>的位数与主存储器空间和指令字长的关系（2016、2021）  

####  <span style="color: silver;">程序计数器（<span style="color: LightSkyBlue;">P</span><span style="color: LimeGreen;">C</span>）

<ul>

- 功能：
  - 指出欲执行指令在主存储器中的存放地址

- 位数：
  - 当PC和主存储器均按字节编址时
  - PC的位数等于主存储器地址位数

- 指令获取过程：
  - CPU根据PC的内容从主存储器中取指令
  - 取出的指令送入指令寄存器

- 自动加1功能：
  - 指令通常顺序执行
  - PC会自动加1
    - 这里的"1"指一条指令的字节数

- 特殊情况：
  - 遇到转移类指令时
  - PC的新值由指令计算得到
</ul>

####  <span style="color: silver;">指令~（<span style="color: LightSkyBlue;">I</span>R）

<ul>

- 功能：
  - 用于保存当前正在执行的指令
- 规格：
  - IR的位数等于指令字长
</ul>

####  <span style="color: silver;">存储器地址~（M<span style="color: DarkRed;">A</span>R）

<ul>

- 存放要访问的 <span style="color: gray;">主memory</span>单元的<span style="color: DarkRed;">地址</span>
- MAR的位数
  - 等于主存储器地址线数
  - 反映了最多可寻址的存储单元的个数
</ul>

####  <span style="color: silver;">存储器数据~（M<span style="color: LightSkyBlue;">D</span>R）

<ul>

  - 功能：
    - 存放向 I/O 主存储器' <span style="color: gray;">信息</span>
  - 规格：
    - MDR的位数等于存储字长
  - 使用场景：
    - CPU和主存储器交换信息时
      - 需要同时使用MAR和MDR
</ul>

</ul>

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
