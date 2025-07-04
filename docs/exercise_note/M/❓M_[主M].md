<span style="color: silver;">

<div style="float: left; width: 64%; padding: 1%;">

#  <span style="color: silver;">concept
<ul>

##  <span style="color: silver;">M <span style="color: LimeGreen;">分类</span>


<ul>

###  <span style="color: silver;"><span style="font-size: 16px;">1. 随机存储器 什么情况下 信息不会丢失?

<details>
<summary> </summary>

- 半导体RAM是易失性RAM，但只要电源不断电，所有信息是不丢失的 
</details>

###  <span style="color: silver;"><span style="font-size: 16px;">2. RAM和ROM 是否统一编址?

<details>
<summary> </summary>

- 统一编址  
- 访问随机存储器时，访问时间与存储单元的物理位置无关  
- both can随机存取信息
  - RAM断电后信息会丢失  
  - ROM断电后信息不会丢失  
</details>

###  <span style="color: silver;"><span style="font-size: 16px;">3. 半导体存储器 存储unit 宽度 if must 相同?

<details>
<summary> </summary>

- 同一个M中，每个存储单元的宽度必须相同，即evry存储单元存储的bit位数must same
- "编址"，指给每个存储单元一个编号  
- 存储器的核心部分
  - 存储<span style="color: RoyalBlue;">阵</span><span style="color: LightSkyBlue;">列</span>
    - 由若干存储<span style="color: gray;">单元</span>构成  
      - ~ 存储<u>元件</u>构成
        - 一个bit位 
</details>

###  <span style="color: silver;">other
<ul>

####  <span style="color: silver;"><span style="font-size: 16px;">1. Cache 的M类型 ()

<details>
<summary> </summary>

-  易失M
</details>

####  <span style="color: silver;"><span style="font-size: 16px;">🌟2. U盘属于（ ）类型的M

<details>
<summary> </summary>

- 采用 Flash存储器技术 ← ROM
  - 常用作辅存
</details>

####  <span style="color: silver;"><span style="font-size: 16px;">3. 闪存flash w 和 r which 速度快?

<details>
<summary> </summary>

- as a type of ROM，
  - $V_{\text{写}}$要比$V_{\text{读}}$ <span style="color: Gold;">慢</span>
  - 写入时 must 先擦除原有数据 
</details>

####  <span style="color: silver;"><span style="font-size: 16px;">🌟4. 某OS 保存于硬盘上，其内存储器应该采用（ ）。
<details>
<summary> </summary>

- OS 保存于硬盘上，thus need  <span style="color: Gold;">BIOS</span> 的 引导程序将操作系统引导到 主存(RAM)中
  - 引导<span style="color: LightSkyBlue;">程序</span> 则固化于ROM中

</details>

####  <span style="color: silver;"><span style="font-size: 16px;">5.EPROM 能否取代RAM

<details>
<summary> </summary>

- EPROM (可擦可编程ROM) is 可改写的，但不能取代RAM 
</details>

####  <span style="color: silver;"><span style="font-size: 16px;">🌟6. <span style="color: GreenYellow;">D</span>RAM 每隔一段时间 将 ( ) 内容重新写入一遍? this operation 几次访存?

<details>
<summary> </summary>

- 每隔一定的时间，根据<span style="color: gray;">原</span>存内容重新写入一遍 ←  <span style="color: GreenYellow;">D</span>RAM
-  <span style="color: GreenYellow;">刷新</span> just 把信息读出，after through a 刷新放大器 又重新存回存储单元
   -  however 刷新<span style="color: gray;">放大</span>器 集成在 RAM上
   -  → 只进行了一次访存 only 1 $T_{\text 存取}$
</details>

####  <span style="color: silver;"><span style="font-size: 16px;">🌟 7. <span style="color: GreenYellow;">D</span>RAM 与<span style="color: gray;">S</span><span style="color: GreenYellow;">D</span>RAM 与 CPU 交换数据 的区别? <span style="color: gray;">S</span><span style="color: GreenYellow;">D</span>RAM 的 行缓冲器 用() 实现?

<details>
<summary> </summary>

- 与CPU交换数据ways
  - 传统<span style="color: GreenYellow;">D</span>RAM <span style="color: purple;">异</span>步
  - S<span style="color: GreenYellow;">D</span>RAM <span style="color: gray;">同</span>步
- all need 刷新
- S<span style="color: GreenYellow;">D</span>RAM 的 行缓冲器
  - 用来缓存指定行中整行的数据
  - usaully 用 SRAM实现
</details>


####  <span style="color: silver;"><span style="font-size: 16px;"> 8. R<span style="color: DarkRed;">A</span>M 和 R<span style="color: Gold;">O</span>M if both use 随机存取way?
</ul>
</ul>


##  <span style="color: silver;"> <span style="color: Gold;">S</span>RAM  <span style="color: GreenYellow;">D</span>RAM比较


<ul>

###  <span style="color: silver;"><span style="font-size: 16px;">1. <span style="color: Gold;">S</span>RAM  <span style="color: GreenYellow;">D</span>RAM 的V、集成度、成本 which高？ which use <span style="color: gray;">双稳态</span>电路 which use  <span style="color: LimeGreen;">电容</span>暂存电荷 来store 0 1？

<details>
<summary> </summary>

-  <span style="color: GreenYellow;">D</span>RAM芯片的成本比SRAM芯片的低 
   - ~ 速度比SRAM芯片的 <span style="color: Gold;">慢</span> 
   - <span style="color: GreenYellow;">D</span>RAM芯片工作时需要刷新，SRAM芯片工作时不需要刷新  
<br>

-  <span style="color: Gold;">S</span>RAM依靠<span style="color: gray;">双稳态</span>电路的两个稳定状态
   - 来分别存储0和1
-   <span style="color: GreenYellow;">D</span>RAM依靠 <span style="color: LimeGreen;">电容</span>暂存电荷来存储信息
    - 电容上有电荷为1,无电荷为0
</details>

</ul>


##  <span style="color: silver;"> <span style="color: GreenYellow;">D</span>RAM_ <span style="color: LimeGreen;">集中</span>_ <span style="color: Gold;">分散</span> _ <span style="color: purple;">异步</span> 刷新


<ul>

###  <span style="color: silver;"><span style="font-size: 16px;">1. <span style="color: GreenYellow;">D</span>RAM的刷新是以（ ）为单位的。 

###  <span style="color: silver;"><span style="font-size: 16px;">2. <span style="color: GreenYellow;">D</span>RAM采用哪种刷新方式时，不存在死时间（ ）。 

###  <span style="color: silver;"><span style="font-size: 16px;">🌟3. <span style="color: GreenYellow;">D</span>RAM  <span style="color: GreenYellow;">刷新</span> if 为了给 存储<span style="color: LimeGreen;">电容</span> 重新充电? 刷新 if 影响CPU?

<details>
<summary> </summary>

-  刷新是以行为单位的  
   - 为了给<span style="color: GreenYellow;">D</span>RAM存储单元中的存储电容重新充电  
   - 对存储单元进行"读但不输出数据"，即"假读"的操作来实现的  ← 重新写入
- 存在死时间, 影响CPU
</details>

</ul>


##  <span style="color: silver;"> <span style="color: LimeGreen;">单体</span>多字M&<span style="color: SlateBlue;">多</span>模块M



<ul>

###  <span style="color: silver;"><span style="font-size: 16px;">1.  <span style="color: LimeGreen;">单体</span>多字M  主要解决 () 问题? whether can 地址跳跃?
<details>
<summary> </summary>

  - 主要解决访存速度的问题
  - need 地址连续
</details>

###  <span style="color: silver;"><span style="font-size: 16px;"> 2. <span style="color: purple;">多</span>模块M能提高存储器的访问速度的原因()

<details>
<summary> </summary>

- 各模块有独立的读/写电路
  - can realize  <span style="color: LimeGreen;">并行</span>操作
</details>
</ul>


</ul>



#  <span style="color: silver;">count
<ul>

##  <span style="color: silver;">已知M  <span style="color: LimeGreen;">容量</span>_问 地址线 数据线&<span style="color: GreenYellow;">D</span>RAM地址<span style="color: gray;">复用</span>


<ul>

###  <span style="color: silver;">base
<ul>

####  <span style="color: silver;"><span style="font-size: 16px;">1. 某一SRAM芯片，容量为1024×8位，该芯片的地址引脚和数据引脚总数至少是（ ）。  

####  <span style="color: silver;"><span style="font-size: 16px;">2. 某存储器容量为32K×16位，则地址线 和 数据线（ ）。

</ul>

###  <span style="color: silver;"> <span style="color: GreenYellow;">D</span>RAM地址<span style="color: gray;">复用</span>

<ul>

####  <span style="color: silver;"><span style="font-size: 16px;">1. 某一<span style="color: GreenYellow;">D</span>RAM芯片，采用地址复用技术，容量为1024×8位，该芯片的地址引脚和数据引脚总数至少是（ ）。 

####  <span style="color: silver;"><span style="font-size: 16px;">2. 每推出新一代<span style="color: GreenYellow;">D</span>RAM芯片，地址线至少增1根，则容量至少提高到原来的（ ）倍。  

####  <span style="color: silver;"><span style="font-size: 16px;">3. 256MB 的存储器由若干 4M×8 位的 <span style="color: GreenYellow;">D</span>RAM 芯片构成 → <span style="color: GreenYellow;">D</span>RAM 芯片的<span style="color: DarkRed;">地址</span>引脚和<span style="color: LightSkyBlue;">数据</span>引脚总数是（ ） 
</ul>

</ul>

##  <span style="color: silver;"> <span style="color: GreenYellow;">刷新</span>时间计算_~ 开销


<ul>

###  <span style="color: silver;"><span style="font-size: 16px;">🌟🌟⚠️ 1. 采用64K×1位的<span style="color: GreenYellow;">D</span>RAM芯片构成256K×8位的存储器，if异步刷新，每单元刷新间隔不超过2ms → 生成的刷新信号的间隔时间是（ ）；if 集中刷新 ，则存储器刷新一遍最少用（ ）个读/写周期。

<details>
<summary> tip </summary>

- <span style="color: GreenYellow;">D</span>RAM隐含条件: 地址复用 → r=c & r×c=word
- $64K=2^16=2^8×2^8$ → 256行256列 (各自 8 根地址线)
- 按行刷新
  - evry单元的every行里的evry位 都要刷新 $2/ms \div 256 ≈ 7.8μs$
  - 集中一行里的 每个位 都要停下来 来一遍 thus256 $T_读写$
</details>


###  <span style="color: silver;"><span style="font-size: 16px;"> 2. assume <span style="color: GreenYellow;">D</span>RAM 芯片中存储阵列的行数为 r，列数为 c，对于一个 2K×1 位的 <span style="color: GreenYellow;">D</span>RAM 芯片，为保证其地址引脚数最少，并尽量减少刷新开销 →  r、c 的取值分别是（ ）? 

- 2048, 1  
- 1, 2048 
- 64, 32  
- 32, 64  


</ul>


##  <span style="color: silver;">存储<span style="color: RoyalBlue;">阵</span><span style="color: LightSkyBlue;">列</span>_M容量

<ul>

###  <span style="color: silver;"><span style="font-size: 16px;">1. one 内存条中有16个<span style="color: GreenYellow;">D</span>RAM芯片，每个芯片中有4个位平面，每个位平面的存储阵列为4096行×4096列，则内存条的总容量为（ ）MB。

</ul>

##  <span style="color: silver;"> 访存 <span style="color: Gold;">冲突</span>

<ul>

###  <span style="color: silver;"><span style="font-size: 16px;"> 1. 某计算机使用<span style="color: RoyalBlue;">四体</span>交叉编址存储器，假定在存储器总线上出现的主存地址（十进制）序列为 8005, 8006, 8007, 8008, 8001, 8002, 8003, 8004, 8000，则可能发生访存冲突的地址对是（ ）。

<details>
<summary> </summary>
- 冲突condition: addr%m 相同
- 选最有问题的(相邻)

</details>

</ul>

##  🌟⚠️<span style="color: silver;"> <span style="color: green;">低位</span>交叉编址_${\color{skyblue}T}_{存取}$& ${\color{skyblue}T}_{\color{gold}总线}$ _存储体数计算


<ul>

###  <span style="color: silver;"> 存储体数
<ul>

####  <span style="color: silver;"> <span style="font-size: 16px;">△ 1. 单个存储体的存储周期为110ns，总线传输周期为10ns，采用低位交叉编址的多模块存储器时，存储体数应（ ）。  

<details>
<summary> tip </summary>

 $$T_{\text {单 \color{skyblue}实际}} = T_{\text {单\color{gold}origin}} \div m$$
   - 存储体数 越多 , 实际的 单个存储周期 越短

- 低位交叉编址
  - realize 并行访问
  - 请求被分散到多个存储体上 
</details>
</ul>

###  <span style="color: silver;">⚠️ ${\color{skyblue}T}_{存取}$& ${\color{skyblue}T}_{\color{gold}总线}$
<ul>

####  <span style="color: silver;"><span style="font-size: 16px;">1. one <span style="color: RoyalBlue;">四体</span> <span style="color: Gold;">并行</span>低位交叉M，每个模块的容量是64K×32位，存取周期为200ns，总线周期为50ns → 1个$T_{\text{{总线}}}$ 内 every模块能向 CPU提供 () 位二进制信息; 4个$T_{\text{{总线}}}$内 M总共能~()

####  <span style="color: silver;"><span style="font-size: 16px;"> ⚠️❓ 2. <span style="color: RoyalBlue;">四体</span>低位交叉M，分别执行 → ①读取6个连续地址单元中存放的存储字，重复80次；②读取8个连续地址单元中存放的存储字，重复60次 → ①、②所花费的时间之比为（ ）。

#### <span style="color: silver;"><span style="font-size: 16px;"> ⚠️⚠️❓ 3.主存按字节编码，由 4 个 64M×8 位的 <span style="color: GreenYellow;">D</span>RAM 芯片采用交叉编址方式构成，并与宽度为 32 位的存储器总线相连，主存每次最多读/写 32 位数据。若 double 型变量 x 的主存地址为 804 001AH  → 读取 x 需要的 存储<span style="color: LightSkyBlue;">周期</span> <span style="color: LimeGreen;">数</span> 是（ ）。  
</ul>

###  <span style="color: silver;">min<span style="color: BurlyWood;">地址</span>
<ul>

####  <span style="color: silver;"><span style="font-size: 16px;"> 1. 若干16K×8位的存储芯片 组成一个 64K×8位的存储器， 交叉编址方式 → 地址BFFFH所在的芯片的最小地址为（ ）。 

</ul>


###  <span style="color: silver;"><span style="color: green;">编</span><span style="color: DarkRed;">址</span>方式 判断 & 行 <span style="color: Gold;">缓冲</span>bit
<ul>

####  <span style="color: silver;"><span style="font-size: 16px;"> 🌟1. 某内存条包含 8 个 8192×8192×8 位的 <span style="color: GreenYellow;">D</span>RAM 芯片，按字节编码，支持突发（burst）传送方式，对应存储器总线宽度为 64 位，每个 <span style="color: GreenYellow;">D</span>RAM 芯片内有一个行缓冲区（row buffer） → 内存条的 <span style="color: GreenYellow;">容量</span> ()?采用 () <span style="color: green;">编</span><span style="color: DarkRed;">址</span>方式? 芯片 地址引脚() ? 芯片内 行缓冲 有()bit? 

<details>
<summary> </summary>
- MB=$2^13$bit
- every 芯片一次只能传输 8bit
  - 存储器总线宽度64=8×8bit
- 引脚复用
- 芯片内行数是8192,一行的大小是8192×8bit

</details>

</ul>

</ul>


</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">


</div>
<div style="clear: both;"></div>
