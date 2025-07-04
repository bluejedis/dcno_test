 <span style="color: silver;">

<div style="float: left; width: 64%; padding: 1%;">

##  <span style="color: silver;"><span style="font-size: 14px;"> orginal

### <span style="color: silver;">按在计算机中的<span style="color: gray;">作用</span>（层次）

<ul>

- 主存储器
  - 简称主存，也称内存储器（内存）
  - 用途：存放计算机运行期间所需的程序和数据
  - 特点：
    - CPU可以直接随机访问
    - 可与Cache及辅助存储器交换数据
    - 容量较小
    - 存取速度较快
    - 每位价格较高

- 辅助存储器
  - 简称<span style="color: RoyalBlue;">辅</span>存，也称 <span style="color: gray;">外</span>存储器或外存
  - 用途：存放当前暂时不用的程序和数据，以及需要永久性保存的信息
  - 特点：
    - 需要调入主存后才能被CPU访问
    - 容量大
    - 存取速度较慢
    - 单位成本低

- 高速缓冲存储器
  - 简称Cache
  - 位置：位于主存和CPU之间
  - 用途：存放当前CPU经常使用的指令和数据
  - 特点：
    - 存取速度可与CPU速度匹配
    - 存储容量小
    - 价格高
    - 现代计算机通常将其制作在CPU中

</ul>

### <span style="color: silver;">按存储<span style="color: SlateBlue;">介质</span> 

<ul>

- 磁表面存储器
  - 磁盘
  - 磁带
- 磁芯存储器
- 🌟半导体存储器 (R<span style="color: DarkRed;">A</span>M R <span style="color: Gold;">O</span>M)
  - MOS型存储器
  - 双极型存储器
- 光存储器
  - 光盘

</ul>

### 🌟<span style="color: silver;">按<span style="color: Gold;">存</span><span style="color: LimeGreen;">取</span>方式分类  

<ul>

> pro：采用随机存取的存储器（2011）  

####  <span style="color: silver;"><span style="color: LimeGreen;">随机</span>存储器（R<span style="color: DarkRed;">A</span>M)
  - 特点：
   - 任何存储单元都可以随机存取
   - 存取时间与存储单元物理位置 <u>无关</u>
  - 优点：读/写方便、使用灵活
  - 用途：主要用作主存或高速缓冲存储器
  - 分类：
   -  <span style="color: Gold;">S</span>RAM
   -  <span style="color: LimeGreen;">D</span>RAM

####  <span style="color: silver;">只读存储器（R<span style="color: Gold;">O</span>M）
  - 特点：
    - 内容只能随机读出不能写入
    - 断电内容不会丢失
    - 写入速度比读取速度慢得多
  - 用途：存放固定不变的程序、常数和汉字字库等
  - 功能：可与随机存储器共同作为主存的一部分

<ul>

##### <span style="color: silver;"><span style="color: green;">M</span>ROM

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

##### <span style="color: silver;"><span style="color: LightSkyBlue;">P</span>ROM  

<ul>

- 定义：可以实现一次性编程的只读存储器
- 特点：
  - 允许用户利用专门的设备（编程器）写入自己的程序
  - 一旦写入，内容就无法改变

</ul>

##### <span style="color: silver;"> <span style="color: GreenYellow;">E</span><span style="color: LightSkyBlue;">P</span>ROM  

<ul>

- EPROM特点：
  - 可由用户利用编程器写入信息
  - 可对内容进行多次改写
- 局限性：
  - 编程次数有限
  - 写入时间过长
  - <u>不能取代</u>RAM

</ul>

##### <span style="color: silver;"><span style="color: LightSkyBlue;">Flash</span> M 

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

##### <span style="color: silver;">固态硬盘（Solid State Drive，<span style="color: Goldenrod;">S</span>SD）

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

####  <span style="color: silver;"> <span style="color: Gold;">串</span>行访问存储器
  - 特点：需按<span style="color: gray;">物理</span>位置先后顺序寻址
  - 类型：
    - <span style="color: gray;">顺序</span>存取存储器（如磁带）
      - 特点：存取速度慢，按顺序存取
    - <span style="color: gray;">直接</span>存取存储器（如<span style="color: gray;">磁盘</span>、光盘）
      - 特点：介于RAM和顺序存取之间
      - 存取方式：先寻找小区域，再在区域内顺序查找

</ul>

### <span style="color: silver;">按信息的<span style="color: gray;">可</span><span style="color: Gold;">保存</span>性分类  

<ul>

- <span style="color: GreenYellow;">易</span><span style="color: LimeGreen;">失</span>性存储器
  - 特点：<span style="color: gray;">断电</span>后信息消失
  - 示例：RAM

- <span style="color: SlateBlue;">非</span>~
  - 特点：~ <span style="color: Gold;">保持</span>
  - 类型：
    - ROM
    - 磁表面存储器
    - 光存储器

</ul>


</div>
<div style="float: right; width: 26%; padding: 1%;">

##  <span style="color: silver;"><span style="font-size: 14px;"> self

###  <span style="color: silver;">半导体 M
<ul>

####  <span style="color: silver;">R<span style="color: DarkRed;">A</span>M    <span style="font-size: 14px;">  (随机存取)</span>

← 易失
   -   <span style="color: Gold;">S</span>RAM
   -   <span style="color: GreenYellow;">D</span>RAM

####  <span style="color: silver;">R<span style="color: Gold;">O</span>M  <span style="font-size: 14px;">  (also can随机存取)</span>
← 非~
 - Mask ROM（掩模~ ）
 - PROM（可编程~ ）
 - EPROM（可擦除可编程 ~ ）
 - EEPROM（电可擦除可编程 ~ ）
 - Flash ROM（闪存 ~ ）



###  <span style="color: silver;">串行访问M

<ul>

####  <span style="color: silver;">顺序存取M
- 磁带
####  <span style="color: silver;">直接存取M
- 硬盘 光盘

add:
  - 非半导体
    - 磁M（硬盘、磁带）
    - 光M（如CD、DVD
</ul>

###  <span style="color: silver;"> add: 
<ul>

####  <span style="color: silver;">随机 顺序 串行
- 随机存取（RAM：像书柜，可直接抽取任意一本书（地址）。  
- 顺序存取（如磁带：像录音带，必须快进/倒带到目标位置才能读写。  
- 直接存取（如硬盘 ：先定位再顺序读取。  

串行存储器虽速度慢，但成本低、容量大，适合长期存储（如备份磁带、机械硬盘）。


</div>
<div style="clear: both;"></div>
