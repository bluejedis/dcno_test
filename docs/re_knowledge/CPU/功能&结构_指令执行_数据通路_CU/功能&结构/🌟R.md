<div style="float: left; width: 64%; padding: 1%;">

##  <span style="color: silver;">CPU的 <span style="color: LimeGreen;">R 

<ul>

>pro：汇编程序员可见的寄存器（2010、2015、2021）  

- C按汇编语言（或机器语言）程序whether <span style="color: black;">可</span><span style="color: green;">访问</span>，分为两类：
  - 用户 <span style="color: black;">可</span><span style="color: LimeGreen;">见</span>寄存器
    - 特点：
      - 可对这类寄存器编程
      - 可通过使用这类寄存器减少对主<span style="color: Gold;">M</span>的访问次数
    - 包括：
      - 通用寄存器组（含基址/变址寄存器）
      - 程序状态字寄存器
<br>
      - 程序计数器
<br>
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
      - <span style="color: LightSkyBlue;">I</span> 寄存器
      - 暂存寄存器
>pro：CPU中各种寄存器的作用（2013）  

###  <span style="color: silver;"><span style="color: LightSkyBlue;">A</span><span style="color: LimeGreen;">L</span>U中的 <span style="color: LimeGreen;">R</span>

<ul>

####  <span style="color: silver;">通用<span style="color: LimeGreen;">R</span>组（GPRs）

<ul>

- function：
  - 存放 操作数：
    - 源 操作数
    - 目的 ~
    - 中间结果
  - ~ 地址信息：
    - 常见寄存器如：
      - AX
      - BX
      - CX
      - DX
      - SP
- 访问方式：
  - <span style="color: LightSkyBlue;">I</span> 中指定寄存器 <span style="color: black;">编号</span>
  - through 编号 确定访问的具体寄存器
- SP特点：
  - 堆栈指针
  - 指示栈顶地址
</ul>

####   <span style="color: silver;"><span style="color: GreenYellow;">累加</span><span style="color: LimeGreen;">R</span>（ACC）

<ul>

暂存结果

- function：
  - 通用寄存器
  - 存储：
    - 暂时 存放ALU运算的 结果
</ul>

####  <span style="color: silver;"><span style="color: green;">移</span>位~（<span style="color: green;">S</span>R）

<ul>

- function：
  - 存储：
    - 存放 操作数
  - 移位操作：
    - 在 控制信号 作用下
    - 寄存器中的数据可：
      - 向左移位
      - 向右移~
</ul>

####  <span style="color: silver;">暂<span style="color: Gold;">存</span>~

<ul>

- function：
  - 暂存数据：
    - 来源：
      - 数据Bus
      - 通用R
    - 目的：
      - 在取出下一个操作数时将其同时送入ALU
  - 可见性：
    - 对应用程序员是透明的（不可见）
</ul>

####  <span style="color: silver;"><span style="color: LightSkyBlue;">程序</span> <span style="color: Gold;">状态</span>字~（<span style="color: LightSkyBlue;">P</span><span style="color: Gold;">S</span>W）

<ul>

- function和组成：
  - 保留 由算术/逻辑运算<span style="color: LightSkyBlue;">I</span>  或 测试<span style="color: LightSkyBlue;">I</span>  的运行 结果 
  - 而建立的各种 <span style="color: Gold;">状态</span><span style="color: gray;">信息</span>
  - 包含的标志位：
    -  <span style="color: LimeGreen;">溢出</span>标志（ <span style="color: LimeGreen;">O</span>F）
    -  <span style="color: Gold;">符号</span>标志（ <span style="color: Gold;">S</span>F） 
    - <span style="color: LightSkyBlue;">零</span>标志（<span style="color: LightSkyBlue;">Z</span>F）
    - <span style="color: green;">进位</span>标志（<span style="color: green;">C</span>F）
  - 存储方式：
    - 每个标志位
      - 由一位触发器来保存
    - all标志位组合在一起构成 PSW
</ul>

</ul>

###  <span style="color: silver;"> <span style="color: Gold;">C</span>U中的 <span style="color: LimeGreen;">R

<ul>

>pro：PC和<span style="color: LightSkyBlue;">I</span><span style="color: LimeGreen;">R</span>的位数与主<span style="color: Gold;">M</span>空间和<span style="color: LightSkyBlue;">I</span> 字长的关系（2016、2021）  

####  <span style="color: silver;">程序计数器（<span style="color: LightSkyBlue;">P</span><span style="color: LimeGreen;">C</span>）

<ul>
show <span style="color: LightSkyBlue;">指令</span><span style="color: DarkRed;">地址</span>

- function：
  - 指出 
    - 欲执行<span style="color: LightSkyBlue;">I</span>  in 主<span style="color: Gold;">M</span>中的 存放<span style="color: DarkRed;">地址</span>

-  <span style="color: LimeGreen;">位数</span>：
   - when PC和主<span style="color: Gold;">M</span> both 按<span style="color: LightSkyBlue;">Byte</span>编址时
     -  = 主<span style="color: Gold;">M</span><span style="color: DarkRed;">地址</span>  <span style="color: LimeGreen;">位数</span>

   - 按 <span style="color: gray;">word</span> 编址时
     - = 主<span style="color: Gold;">M</span><span style="color: DarkRed;">地址</span>  <span style="color: LimeGreen;">位数</span>-$log_2(Byte_{{\color{skyblue}指令}字长})$
   - (both can 边界<span style="color: Gold;">对齐</span>的方式存放)
     - data'存储位置must is its 数据类型大小'<span style="color: DarkSeaGreen;">整数</span>倍

- <span style="color: LightSkyBlue;">I</span> 获取：
  - from主<span style="color: Gold;">M</span>中取<span style="color: LightSkyBlue;">I</span> 
  - <span style="color: LightSkyBlue;">I</span> → <span style="color: LightSkyBlue;">I</span><span style="color: LimeGreen;">R</span>
- <b>+1</b> function：
  - <span style="color: LightSkyBlue;">I</span> usually 顺序执行
  - PC will +1 [^1]
    - "1": 
      - 一条<span style="color: LightSkyBlue;">I</span> 的<span style="color: LightSkyBlue;">Byte</span>数

- special：
  - meet Jcc[^2] <span style="color: LightSkyBlue;">I</span> 时
  - PC的新值 由<span style="color: LightSkyBlue;">I</span> 计算得到



</ul>



####  <span style="color: silver;"><span style="color: LightSkyBlue;">I</span> ~（<span style="color: LightSkyBlue;">I</span>R）

<ul>

- function：
  - 用于保存当前正在执行的<span style="color: LightSkyBlue;">I</span> 
- 规格：
  - IR的位数 = <span style="color: LightSkyBlue;">I</span> 字长
</ul>

####  <span style="color: silver;">存储器地址~（M<span style="color: DarkRed;">A</span>R）

<ul>

- 存放要访问的 <span style="color: gray;">主memory</span>单元的<span style="color: DarkRed;">地址</span>
- MAR的位数
  - 等于主<span style="color: Gold;">M</span>地址线数
  - 反映了最多可寻址的存储单元的个数
</ul>

####  <span style="color: silver;">存储器数据~（M<span style="color: LightSkyBlue;">D</span>R）

<ul>

  - function：
    - 存放向 I/O 主<span style="color: Gold;">M</span>' <span style="color: gray;">信息</span>
  - 规格：
    - MDR的位数等于存储字长
  - 使用场景：
    - CPU和主<span style="color: Gold;">M</span>交换信息时
      - 需要同时使用MAR和MDR
</ul>

</ul>

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>

[^1]:“1”实际上代表的是指令的长度，而不是固定值1。
    - PC+ ? ← <span style="color: LightSkyBlue;">指令</span>字长 & 编<span style="color: DarkRed;">址</span>方式

    - eg，
      - if定长指令字结构
        - <span style="color: LightSkyBlue;">指令</span>字长=16位（M按byte编址）
          - PC + 2（因为16位等于2个byte）
        - if 32位
          - PC + 4..

[^2]: Jcc时need judge 转移whether成功
    - if成功
      - →  <span style="color: LimeGreen;">目标</span>地址
    - if else
      - PC自增后'~