 <span style="color: silver;">

<div style="float: left; width: 64%; padding: 1%;">

# <span style="color: Gold;">主M

<ul>

## <span style="color: silver;"> <span style="color: Gold;">S</span> <span style="color: GreenYellow;">R</span><span style="color: DarkRed;">A</span>M <span style="color: LimeGreen;">D</span> ~
<span style="font-size: 12px;"> Static random access memory;Dynamic random access memory

<ul>

- 半导体存储器
  - 随机存储器（RAM）
    - 静态随机存储器（SRAM）
      - 用于实现靠近处理器的<span style="color: purple;">Cache</span>
      - 易失性存储器
    - 动态随机存储器（DRAM）
      - 用于实现 <span style="color: Gold;">主</span>存储器
      - 易~
  - 只读存储器（ROM）
    - 非易失性存储器

### <span style="color: silver;"> <span style="color: Gold;">S</span>RAM

<ul>

- 基本概念
  - 存储<span style="color: LightSkyBlue;">元</span>：
    - 存放 一个二进制位的物理器件 
    - (M'最基本 构件
  - 存储<span style="color: gray;">单元</span>：地址码相同' 多个存储<span style="color: LightSkyBlue;">元</span>
  - 存储<span style="color: deepskyblue;">体</span>：集合 of 存储<span style="color: gray;">单元</span>s 

- 工作特点
  - use双稳态触发器（六晶体管MOS）记忆信息
  - 静态特性：信息读出后保持原状态，无需再生（<span style="color: gray;">非破坏</span>性读出）
  - 性能特征：
    - 存取速度快
    - 集成度低
    - 功耗较大
    - 价格昂贵
  - 用途：高速缓冲存储器<span style="color: SlateBlue;">cache

</ul>

### <span style="color: silver;"> <span style="color: LimeGreen;">D</span>RAM

<ul>

- 存储原理：
  - 利用存储元电路中栅极电容上的电荷存储信息
- 基本结构：
  - usually only一个  <span style="color: Gold;">晶体</span><span style="color: LightSkyBlue;">管
- 与SRAM对比优势：
  - 密度更高
  - 集成度高
  - 位价低
  - 功耗低
- 缺点：
  - 存取速度较慢
  - 需要定时刷新和读后再生
- 用途：
  - 大容量主存系统

> pro：需要刷新的存储芯片：SDRAM（2015）  

#### 🌟<span style="color: Gold;">特点

<ul>

- 电荷维持时间：
  - 持续$1\sim2\mathrm{ms}$
- 读操作特性：
  - 破坏性读出
  - need 读后再生
- 🌟刷新周期：
  - 定义：相邻两次刷新的时间间隔
  - 典型值：$2\mathrm{ms}$

</ul>

#### 🌟<span style="color: silver;"> <span style="color: GreenYellow;">刷新</span>方式

<ul>

##### <span style="color: silver;"> <span style="color: LimeGreen;">集中</span>~

<ul>

- 特点：
  - 在固定时间内<u>逐一</u>对所有行再生
  - 刷新期间 停止读/写操作（死时间/访存<span style="color: gray;">死</span> 区）
- 缺点：刷新期间不能访问存储器

</ul>

##### <span style="color: silver;"> <span style="color: Gold;">分散</span>~

<ul>

- 工作方式：<u>后半</u>部分用于刷新
- 影响：增加系统存取周期（如$0.5\mu\mathrm{s}$到$1\mu\mathrm{s}$）
- 优点：<u>没有</u> 死区
- 缺点：加长系统存取周期

</ul>

##### <span style="color: SlateBlue;">异</span><span style="color: silver;">步~

<ul>

- 原理：结合集中和分散刷新方法
- 实现方式：
  - 刷新周期 ÷ 行数
  - 按间隔时间产生刷新请求
- 优势：
  - <span style="color: gray;">死</span>时间分布更分散，减少CPU等待时间

</ul>

<br>

- (add)

|    |  <span style="color: LimeGreen;">集中</span>        |  <span style="color: Gold;">分散</span>      | <span style="color: purple;">异步</span>         |
|---------------------|------------------|------------------|------------------|
| time        | 集中period  | 分散到 T   | bus 空闲时间 |
| <span style="color: gray;">死</span>区       | 集中出现长~   | <b> \ </b> <br> (T 小延迟) |  分布更分散      |
| <span style="font-size: 10px;"> application scenario     | 可容忍间歇停顿   | need均匀延迟     | 高带宽利用率     |

#### <span style="color: silver;">attention
(对所有刷新ways而言)
<ul>

- 特性：
  - 对CPU透明，不依赖外部访问
- 执行：
  - 以  <span style="color: Gold;">行</span> 为单位进行
  - 由芯片内部自动生成行地址
- 操作：
  - 类似读操作但存在区别
  - 刷新时<span style="color: gray;">无需</span>选片
  - 所有芯片可<u>同时</u>进行刷新

> attention：  

- 刷新&再生'  <span style="color: Gold;">区别</span>：
  - both恢复数据，but过程不完全相同
  -  <span style="color: GreenYellow;">刷新</span>：
     - 以 <span style="color: Gold;">行</span>为单位进行
     - 需要<u>逐 <span style="color: Gold;">行</span></u>恢复数据
  - 再生：
    - 只针对被读出的单元
    - 仅恢复 <u>被读出</u> 单元的数据

> pro：DRAM芯片行缓冲器容量的计算（2022）  

</ul>

</ul>

#### 🌟<span style="color: silver;"><span style="color: LightSkyBlue;">S</span><span style="color: LimeGreen;">D</span>RAM

<ul>

- 工作方式：与CPU<span style="color: LightSkyBlue;">同步</span>交换数据
- 与传统DRAM区别：
  - 传统DRAM：
    - 采用<span style="color: purple;">异</span>步方式
    - CPU需 <span style="color: Gold;">等待</span>读/写完成
  - SDRAM：
    - 采用<span style="color: LightSkyBlue;">同步</span>方式
    - 锁存地址和控制信号
    - CPU可<u>同时</u>进行其他操作
- 操作特点：
  - 在系统时钟控制下进行
  - 支持 <span style="color: Gold;">突发</span>传输
    - 首次给出 首地址
    - 整行数据送入行缓冲器
    - 每个时钟连续输出数据
- <span style="color: LimeGreen;">行</span><span style="color: gray;">缓冲器</span>：
  - 功能：
    - 缓存 指定行中<span style="color: gray;">整行</span>数据
  - 大小：
    - 列数×位平面数
  - 实现方式：
    - <span style="color: Gold;">S</span>RAM

</ul>

#### <span style="color: silver;">读/写$T$ <span style="color: GreenYellow;">时序</span>图

<ul>

- 芯片信号时间关系要求：
  - 需符合特定要求以确保正确接收行列地址和读写操作

- 读/写$T$ $t$：
  - 读周期时间($t_{\mathrm{{RC}}}$)：两次连续读操作的必要间隔时间
  - 写周期时间($t_{\mathrm{{wc}}}$)：两次连续写操作的必要间隔时间

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/ac49c5139324c976bef95c5760eecc986130d9c6997bdc4b888ceda236371d26.jpg)  
图3.4DRAM芯片读/写周期时序图  
<span style="font-size: 12px;"> “ <span style="color: LimeGreen;">R</span>ow Address Strobe”，  <span style="color: LimeGreen;">行</span> 地址 选通脉冲
“<span style="color: LightSkyBlue;">C</span>olumn Address Strobe”， <span style="color: LightSkyBlue;">列</span> 地址 选通脉冲
“Write  <span style="color: Gold;">E</span>nable”，写 使能 

- <span style="color: Gold;">R</span> $T$：
  - <span style="color: LimeGreen;">行</span>：
    - 在 <span style="color: LimeGreen;">R</span>AS有效前送到芯片地址引脚
  - 时序：
    - <span style="color: LightSkyBlue;">C</span>AS必须滞后RAS一段时间
  - <span style="color: LightSkyBlue;">列</span>：
    - 在CAS有效前送到芯片地址引脚
  - 持续时间要求：
    - RAS至少保持$t_{\mathrm{RAS}}$时间
    - CAS..$t_{\mathrm{CAS}}$..
  - W<span style="color: Gold;">E</span>信号要求：
    - 保持高电平
    - 在CAS有效前建立

- <span style="color: LimeGreen;">W</span> $T$：
  - 行列选通信号的时序关系
    - 与读周期相同
  - $\overline{W\color{gold}E}$
    - 保持低电平
    - 在CAS有效前建立
  - 写数据
    - 必须在CAS有效前在数据总线上保持稳定
    - 目的：确保数据可靠写入

</ul>

</ul>

### 🌟<span style="color: silver;">compare

<ul>

- 表3.1详细列出了SRAM和DRAM各自的特点

表3.1SRAM DRAM
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/247e4075afae5a6921141e41eb4721eb9e64db737333bbae6ebd4d1ecd2c7aab.jpg)  

</ul>

### <span style="color: silver;"><span style="color: Gold;">存储</span>器 <span style="color: LimeGreen;">芯</span><span style="color: LightSkyBlue;">片

<ul>

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/2516f94b368ccd12877ec553c7401ec98c5b18224a062f7a42b548d1c7b596b4.jpg)  
图3.5存储器芯片结构图  

#### 🌟<span style="color: silver;">存储体（存储<span style="color: LightSkyBlue;">矩阵</span>）

<ul>

- 存储体是存储单元的集合
- 存储单元选择方式：
  - 行选择线（X）选择
  - 列选择线（Y）选择
- 读写特点：
  - <u>相同行列</u>上的多位同时操作
  - <span style="color: gray;">位平面</span>数 决定 同时操作 的<span style="color: gray;">位数</span>
  - 支持的操作：
    - 读出
    - 写入

</ul>

#### <span style="color: silver;">地址<span style="color: gray;">译码</span>器

<ul>

- 地址转换：
  - 地址信号--> 译码输出线上的高电平
- 目的：
  - 驱动相应的读/写电路
- 译码方式：

##### <span style="color: silver;"> <span style="color: LimeGreen;">单</span>译码法（一维译码）

<ul>

- only一个行译码器
  - 特点：
    - 同一行中所有存储单元的<span style="color: gray;">字线</span>连在一起
    - 同一行中的各单元构成一个<span style="color: gray;">字</span>
      - 被同时读出或写入
  - 问题：
    - 地址译码器的输出线数过多

</ul>

##### <span style="color: silver;"><span style="color: SlateBlue;">双</span>译码法（二维译码）

<ul>

- 2 direction：
  - X方向译码器
  - Y方向~
- 存储单元选择：
  - 行列<span style="color: gray;">交叉点</span>定位
  - 精确确定 单个存储单元位置
- 现状：
  - DRAM芯片的<span style="color: gray;">主流</span>译码结构

</ul>

</ul>

#### <span style="color: silver;">I/O <span style="color: Gold;">控制</span>电路

<ul>

- 控制操作：
  - 控制被选中单元的 <span style="color: Gold;">R</span>/ <span style="color: LimeGreen;">W</span>操作
- 信号处理：
  - 具有信号放大功能
  - 增强信息的可靠性

</ul>

#### <span style="color: silver;"><span style="color: LightSkyBlue;">片</span><span style="color: LimeGreen;">选</span>控制信号

<ul>

- 必要性：
  - <span style="color: LimeGreen;">单个</span>芯片容量限制：
    - 容量太小
    - 无法满足计算机存储需求
  - 存储器扩展需求：
    - 需要<span style="color: SlateBlue;">多个</span>芯片组合
  - 访问控制要求：
    - 必须选中 <span style="color: Gold;">目标</span><span style="color: gray;">字</span>所在芯片
    - 其他芯片保持非选中状态
  - thus：
    - need ~

</ul>

#### <span style="color: silver;"> <span style="color: Gold;">读</span>/ <span style="color: LimeGreen;">写</span>控制信号

<ul>

- 根据CPU给出的读命令或写命令，控制被选中单元进行读或写

</ul>

</ul>

</ul>

## <span style="color: Gold;">R</span><span style="color: silver;">O</span><span style="color: LimeGreen;">M</span>  

<ul>

### <span style="color: Gold;">特点  

<ul>

> pro：RAM和ROM的区别（2010）  

- <span style="font-size: 12px;">both支持随机访问
- <span style="color: GreenYellow;">R</span><span style="color: DarkRed;">A</span>M (SRAM和DRAM)：
  - 属于 <span style="color: GreenYellow;">易失</span>性半导体存储器
- <span style="color: Gold;">R</span><span style="color: silver;">O</span><span style="color: LimeGreen;">M</span> ：
  - 信息一旦写入<span style="color: gray;">不易</span>改变
  - 掉电不会丢失信息
  - 主要优点：
    - 结构简单，位密度高于可读/写存储器
    - 非易失性，可靠性高

</ul>

### <span style="color: LimeGreen;">类型</span>  

<ul>

#### <span style="color: silver;"><span style="color: green;">M</span>ROM

<ul>

- 内容由半导体制造厂写入
  - 按用户提出的要求在芯片生产过程中直接写入
  - 写入后内容<u>无法改变</u>
- 优点：
  - 可靠性高
  - 集成度高
  - 价格便宜
- 缺点：
  - 灵活性差

</ul>

#### <span style="color: silver;"><span style="color: LightSkyBlue;">P</span>ROM  

<ul>

- 定义：可以实现一次性编程的只读存储器
- 特点：
  - 允许用户利用专门的设备（编程器）写入自己的程序
  - 一旦写入，内容就无法改变

</ul>

#### <span style="color: silver;"> <span style="color: GreenYellow;">E</span><span style="color: LightSkyBlue;">P</span>ROM  

<ul>

- EPROM特点：
  - 可由用户利用编程器写入信息
  - 可对内容进行多次改写
- 局限性：
  - 编程次数有限
  - 写入时间过长
  - <u>不能取代</u>RAM

</ul>

#### <span style="color: silver;"><span style="color: LightSkyBlue;">Flash</span> M 

<ul>

> pro：Flash存储器的特点（2012）  

- 在EPROM基础上发展
- 特点：
  - 兼有ROM和RAM的优点
  - 可在不加电情况下长期保存信息
  - 能在线进行快速擦除与重写
  - 价格便宜
  - 集成度高
  - 擦除重写速度快

</ul>

#### <span style="color: silver;">固态硬盘（Solid State Drive，<span style="color: Goldenrod;">S</span>SD）

<ul>

- 基本组成：
  - 控制单元
  - 存储单元（Flash芯片）
- 特点：
  - 保留Flash存储器优点
  - 读/写速度快
  - 低功耗
- 缺点：
  - 价格较高

</ul>

</ul>

## <span style="color: silver;"> <span style="color: Gold;">主</span><span style="color: LimeGreen;">M</span>的基本组成  

<ul>

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/32d7adac4f2bd43918e63a15cb75067abfdb78b3072fd13466d39b41b1a285a2.jpg)  
图3.6主存储器的基本组成框图  

### <span style="color: silver;">存储<span style="color: LightSkyBlue;">矩阵

<ul>

- 由 存储<span style="color: gray;">元件</span>（ <span style="color: Gold;">记忆</span>单元）构成
  - 具有两种稳态的 能表示二进制0和1的 物理器件
- 编址方式：
  - 可按<span style="color: gray;">字</span>/<span style="color: LightSkyBlue;">字节</span>编址
  - 现代计算机通常采用<span style="color: LightSkyBlue;">字节</span>编址

</ul>

### <span style="color: silver;">存储器 <span style="color: GreenYellow;">访问</span>过程

<ul>

- CPU操作：
  - 将被访问单元地址送到MAR
  - 主存地址-<span style="color: DarkRed;">地址</span> <span style="color: Gold;">线</span>->主存<span style="color: DarkRed;">地址</span> <span style="color: LimeGreen;">R</span>
  - 发送 <span style="color: Gold;">R</span>/ <span style="color: LimeGreen;">W</span>信号 to 控制电路
- <span style="color: LimeGreen;">W</span>：
  - CPU将数据送到MDR
  - --数据线-> 选中单元
- <span style="color: Gold;">R</span>：
  - 主存读出选中单元内容
  - --数据线-> MDR

</ul>

### <span style="color: silver;"><span style="color: green;">硬件</span><span style="color: Gold;">特性

<ul>

- M<span style="color: LightSkyBlue;">D</span>R<span style="color: gray;">位数</span>与<span style="color: LightSkyBlue;">数据</span>线~相同
- M<span style="color: DarkRed;">A</span>R..与<span style="color: DarkRed;">地址</span>线位..
- 地址空间范围：0~2^地址线位数-1

> attention：  

<ul>

- <span style="color: LightSkyBlue;">数据</span>线的<span style="color: gray;">位数</span>通常= <span style="color: Gold;">存储</span>字长
  - M<span style="color: LightSkyBlue;">D</span>R的位数通常=存储字长
- 若~的位数 ≠  <span style="color: Gold;">存储</span>字长
  - ~由数据线的<span style="color: gray;">位数</span>决定  

</ul>

</ul>

#### <span style="color: silver;"> <span style="color: LimeGreen;">D</span>RAM芯片特性

<ul>

##### 🌟<span style="color: silver;"><span style="color: DarkRed;">地址</span>引脚复用技术

<ul>

- 背景：
  - DRAM芯片容量较大，地址位数较多
- 目的：
  - 减少芯片的地址引脚数
- 实现方式：
  - 行地址和列地址通过相同的引脚分先后两次输入
- 效果：
  - 地址引脚数 可<span style="color: gray;">减少</span>一半

> pro：DRAM芯片行、列数的优化原则（2018）  

</ul>

##### <span style="color: silver;"><span style="color: LimeGreen;">行</span><span style="color: LightSkyBlue;">列</span>数优化原则

<ul>

- 基本参数：
  - 存储容量：$2^{n}{\times}b$ 位
  - 行数：r
  - 列数：c
  - 关系：$2^{n}=r\times\!c$
- 地址位数：
  - 总地址位数：n
  - 行地址位数：$\log_{2}r$
  - 列地址位数：$\log_{2}c$
  - 关系：$n=\log_{2}r+\log_{2}c$
- 优化要求：
  - 减少地址引脚数：$|r–c|$ 最小
  - 减少刷新开销：$r\leqslant c$

</ul>

</ul>

## 🌟<span style="color: silver;"><span style="color: SlateBlue;">多</span>模块M

<ul>

- 一种空间并行技术
- 目的：
  - 提高存储器的吞吐率
- 实现方式：
  - 利用多个结构完全相同的存储模块并行工作
- 常见类型：
  - 单体多字存储器
  - 多体低位交叉存储器

> attention：  

- CPU的速度比存储器快得多
- 若同时从存储器中取出 $n$ 条指令
  - 就可以充分利用CPU资源，提高运行速度

多体交叉存储器就是基于这种思想提出的。  

### 🔎<span style="color: silver;"> <span style="color: LimeGreen;">单体</span><span style="color: SlateBlue;">多</span>字M
> is 单体
<ul>

- 基本特点：
  - 每个存储单元存储 <span style="color: gray;">m</span> 个字
  - 总线宽度为 ~
  - 一次并行读出 ~
- process：
  - 一个存取T 内
    - 从同一地址取出m条指令
  - 将指令逐条送至CPU执行
    - 每隔1/m存取周期，CPU向主存取一条指令
- 缺点：
  - only 指令和数据 <span style="color: gray;">连续</span>存放时有效
  - meet转移指令 or 操作数 不连续时 not obvious

</ul>

### <span style="color: silver;"><span style="color: purple;">多</span>体 <span style="color: LimeGreen;">并行</span>M

<ul>

- 基本组成：
  - 由多个相同容量和存取速度的<span style="color: gray;">模块</span>组成
  - 每个模块具有独立的：
    - 读/写控制电路
    - 地址寄存器
    - 数据寄存器
  - 可并行工作也可交叉工作

#### <span style="color: silver;"><span style="color: LightSkyBlue;">高位</span>交叉编址~（<span style="color: LightSkyBlue;">顺序</span>方式）

<ul>

- 地址划分：
  - <span style="color: LightSkyBlue;">高</span>位表示模块号（体<span style="color: gray;">号</span>）
  - <span style="color: green;">低</span>位表示模块内地址（体内<span style="color: DarkRed;">地址</span>）

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/75d2ac2a627c5bcdace95fe592ef3010583976cec7fbd37807fc2eed52d25b78.jpg)  
图3.7高位交叉编址的多体存储器  

- 工作特点：
  - 低位体内地址送到高位体号确定的模块内译码
  - 连续访问特性：
    - 在一个模块内完成
    - 各模块不能并行访问
  - 性能影响：
    - <span style="color: gray;">不能</span>提高存储器吞吐率

> attention：  

- 模块内特点：
  - 地址是连续的
  - 存取方式是串行的
- 结论：
  - 这种存储器仍是顺序存储器

</ul>

#### ♟️<span style="color: silver;"><span style="color: green;">低位</span>交叉编址（ <span style="color: Gold;">交叉</span>方式）

<ul>

> pro：交叉存储器中数据的存放方式（2017）  

- 地址划分：
  - <span style="color: green;">低</span>位为模块号（体<span style="color: gray;">号</span>）
  - 高位为模块内地址（体内<span style="color: DarkRed;">地址</span>）
- 编址规则：
  - 每个模块按"模<span style="color: gray;">m</span>"交叉编址
  - 模块号 = 单元地址 % <span style="color: gray;">m</span>

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/b4f48c1df4011710c3242e64f98016fdf9a431c95108f08cf1745946d0aec796.jpg)  
图3.8低位交叉编址的多体存储器  

- 工作特点：
  - 高位体内地址送到低位体号确定的模块内译码
  - 程序连续存放在相邻模块中

##### <span style="color: silver;">(1) <span style="color: LightSkyBlue;">轮流</span> <span style="color: silver;"><span style="color: LimeGreen;">启动</span> <span style="color: silver;">方式

<ul>

- 条件要求：
  - 每个模块 读/写位数 = 数据总线位数
  - 模块数m ≥ T/r（T为存取周期，r为总线周期）

> pro：交叉存储器存取时间和带宽的计算（2012、2013）  

- 工作特点：
  - 每隔1/m个存取T轮流启动各模块
  - 存取速度提高m倍
  - 连续存取m个字时间：t₁ = T + (m-1)r
  - 顺序方式时间：t₂ = mT

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/357a8d6b3c8858f8e0445d4f33ec790e4dc9c97914e01f04c3acc061319ce47a.jpg)  
图3.9低位交叉轮流启动的存取时间示意图  

> pro：交叉存储器中访存冲突的分析（2015）  

- 访存冲突：
  - 发生条件：相邻m次访问的地址在同一模块
  - 处理方法：延迟发生冲突的访问请求

</ul>

##### <span style="color: silver;">(2) <span style="color: Gold;">同时 <span style="color: silver;">~

<ul>

- 条件要求：
  - 所有模块 并行读/写的总位数 = 数据总线位数
- 工作示例：
  - 每模块读/写16位
  - 模块数m=4
  - 数据总线64位
  - 4个模块同时启动并行读/写

</ul>

</ul>

</ul>

</ul>

</ul>

</ul>

</ul>



</div>
<div style="float: right; width: 26%; padding: 1%;">


</div>
<div style="clear: both;"></div>
