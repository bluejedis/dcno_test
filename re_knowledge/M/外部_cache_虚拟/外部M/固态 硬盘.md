<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: LightSkyBlue;">磁盘</span> <span style="color: silver;">M

<ul>

磁盘存储器是以磁盘为存储介质的存储器，其主要优点：
- 存储容量大，位价格低
- 记录介质可重复使用
- 记录信息可长期保存而不丢失，甚至可脱机存档
- 非破坏性读出，读出时不需要再生

缺点：
- 存取速度慢
- 机械结构复杂
- 对工作环境要求较高

> pro：磁盘存储器的相关概念（2019）

### <span style="color: Goldenrod;">组成

<ul>

#### <span style="color: silver;">组件
- 磁盘存储器由以下组成：
  - 磁盘 <span style="color: GreenYellow;">驱动</span>器
  - 磁盘 <span style="color: Gold;">控制</span>器 
  - <span style="color: gray;">盘片

#### <span style="color: silver;">磁盘<span style="color: GreenYellow;">驱动</span>器
- 驱动磁盘转动并在盘面上通过磁头进行读/写操作的装置，如图3.14所示

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/949e3320f633db83d48f7dfbb5d87ac3e37d71935bede8ce35981b7926da2bb7.jpg)`  
图3.14磁盘 <span style="color: GreenYellow;">驱动</span> 器示意图

#### <span style="color: silver;">磁盘<span style="color: Gold;">控制</span>器
- 磁盘驱动器与主机的 <span style="color: GreenYellow;">接口</span>
- 主要功能：
  - 接收并解释CPU发来的命令
  - 向磁盘驱动器发出各种控制信号
  - 负责检测磁盘驱动器的状态

#### <span style="color: Gold;">存储</span> <span style="color: silver;">区域
- 组成结构：
  - 多个记录面
  - 每个记录面划分为若干圆形磁道
  - 每条磁道划分为若干扇区
- 存取特点：
  - 扇区（也称块）是磁盘读/写的最小单位
  - 磁盘按块存取

#### <span style="color: LimeGreen;">参数
- 磁<span style="color: gray;">头</span>数（Heads）：
  - 即记录面数
  - 表示磁盘共有多少个磁头
  - 用于读取/写入盘片上记录面的信息
  - 一个记录面对应一个磁头
- 柱<span style="color: gray;">面</span>数（Cylinders）：
  - 表示磁盘每面盘片上有多少条磁道
  - 不同记录面的相同编号（位置）的诸磁道构成一个圆柱面
- <span style="color: LightSkyBlue;">扇</span>区数（Sectors）：
  - 表示每条磁道上有多少个扇区

#### <span style="color: LightSkyBlue;">物理</span> <span style="color: Gold;">特性
- 磁道<span style="color: gray;">间隔</span>：
  - 相邻磁道及相邻扇区间通过间隙分隔
  - 目的是避免精度错误
- 位密度特点：
  - 从最外道向里道增加
  - 磁盘存储能力受限于最内道的最大记录密度

#### <span style="color: silver;">磁盘 <span style="color: Gold;">高速</span>缓存
- 实现方式：
  - 在 <span style="color: Gold;">内存</span>中开辟一部分区域
  - 缓冲 将要被送到磁盘上的<span style="color: LightSkyBlue;">数据</span>
- 优点：
  - 写磁盘时按" <span style="color: GreenYellow;">簇</span>"进行，避免频繁小块数据写盘
  - 中间结果数据在写回磁盘前可快速再次使用

</ul>

### <span style="color: Gold;">原理

<ul>

#### <span style="color: silver;"><span style="color: LightSkyBlue;">编码</span>方法
- 按特定方案将二进制信息转换为磁化翻转状态序列
- 要求读/写控制电路容易、可靠地实现转换

#### <span style="color: silver;">磁<span style="color: LimeGreen;">记录</span>方式
- 通常采用：
  - 调频制（FM）
  - 改进型调频制（MFM）

</ul>

### <span style="color: Gold;">性能</span><span style="color: LimeGreen;">指标

<ul>

#### <span style="color: silver;">记录<span style="color: gray;">密度
- 定义：盘片单位面积上记录的二进制信息量
- 表示方式：
  - 道密度：沿磁盘半径方向单位长度上的磁道数
  - 位密度：磁道单位长度上能记录的二进制代码位数
  - 面密度：位密度和道密度的乘积

#### <span style="color: silver;">磁盘 <span style="color: LimeGreen;">容量
- 非格式化容量：
  - 定义：磁记录表面可利用的磁化单元总数
  - 计算：记录面数 × 柱面数 × 每条磁道的磁化单元数
- 格式化容量：
  - 定义：按特定记录格式所能存储信息的总量
  - 计算：记录面数 × 柱面数 × 每道扇区数 × 每个扇区的容量
  - 特点：比非格式化容量小

> pro：磁盘存取时间的计算（2013、2015、2022）

#### <span style="color: silver;">存取<span style="color: gray;">时间
- 组成部分：
  - 寻道时间：磁头移动到目的磁道的时间
  - 旋转延迟时间：磁头定位到要读/写扇区的时间
  - 传输时间：传输数据所花费的时间
- 时间计算：
  - 平均寻道时间：从最外道移动到最内道时间的一半
  - 平均旋转延迟时间：旋转半周的时间

#### <span style="color: silver;"><span style="color: LightSkyBlue;">数据</span>传输<span style="color: RoyalBlue;">速率
- 定义：单位时间内向主机传送数据的字节数
- 计算公式：Dr = rN
  - r：磁盘转数（转/秒）
  - N：每条磁道容量（字节）

</ul>

### <span style="color: silver;">磁盘<span style="color: DarkRed;">地址

> pro：磁盘地址结构的计算（2022）

<ul>

#### <span style="color: silver;">地址 <span style="color: LimeGreen;">结构
- 主机向磁盘控制器发送寻址信息
- 基本地址结构如图所示

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/63c7621ebd786e99322bc2b3b8f2b7a6108c715c1896f3fefe6388625f9c5d47.jpg)`

#### <span style="color: silver;">eg
- 条件：
  - 16个盘面
  - 每个盘面256个磁道
  - 每个磁道16个扇区
- 结果：
  - 每个扇区地址需16位二进制代码
  - 格式如图所示

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/a05c8eee3f46040951717583967f67c0aa6f299dd9fed653a49b666bc3e3b2b4.jpg)`

</ul>

### <span style="color: silver;">工作 <span style="color: Gold;">过程

<ul>

- 主要操作类型：
  - 寻址
  - 读盘
  - 写盘
- 操作特点：
  - 每个操作对应一个控制字
  - 工作步骤：
    1. 取控制字
    2. 执行控制字

#### <span style="color: silver;">limit
- <span style="color: gray;">机械</span>式部件
- 读/写操作是 <span style="color: Gold;">串</span>行的：
  - 不能同时读写
  - ~两组数据

</ul>

### <span style="color: silver;">磁盘<span style="color: RoyalBlue;">阵列</span> <span style="color: silver;">(  <span style="color: GreenYellow;">R</span><span style="color: RoyalBlue;">A</span><span style="color: gray;">I</span>D

<ul>

独立冗余磁盘阵列

#### <span style="color: Gold;">特点</span> <span style="color: silver;">:
- 组成特点：
  - 将多个独立的物理磁盘组成一个独立的逻辑盘
- 存储特点：
  - 数据分布：
    - 在多个物理盘上分割存储
    - 交叉存储方式
  - 访问方式：
    - 支持并行访问
- 性能优势：
  - 更好的存储性能
  - 更高的可靠性
  - 更强的安全性

> pro：提高RAID可靠性的措施（2013）

#### <span style="color: Gold;">分级
- RAID1～RAID5的共同特点：
  - 磁盘损坏时可随时更换
  - 数据不会损坏
  - 提升系统可靠性

<ul>

##### <span style="color: GreenYellow;">类型
- RAID0：<span style="color: gray;">无冗余</span>和无<span style="color: LightSkyBlue;">校验</span>的磁盘阵列
- RAID1：<span style="color: GreenYellow;">镜像</span>磁盘阵列
- RAID2：采用纠错的海明码的磁盘阵列
- RAID3：位交叉奇偶校验的磁盘阵列
- RAID4：块交叉奇偶校验的磁盘阵列
- RAID5：无独立校验的奇偶校验磁盘阵列

##### <span style="color: silver;">RAID<span style="color: LightSkyBlue;">0
- 特点：
  - 使用条带化技术
  - 连续数据块交替存放在不同物理磁盘扇区
  - 多个磁盘交叉并行读/写
- 优点：
  - 扩大存储容量
  - 提高磁盘存取速度
- 缺点：
  - 无容错能力

##### <span style="color: silver;">RAID<span style="color: GreenYellow;">1
- 工作方式：
  - 两个磁盘同时进行读/写
  - 互为备份
- 优点：
  - 若一个磁盘故障，可从另一磁盘读取数据
- 缺点：
  - 实际容量减少一半

</ul>

#### <span style="color: silver;">优势
- 性能提升
  - 传输速率
    - 多磁盘同时使用提高传输速率
  - 数据吞吐量
    - 通过并行存取提高数据吞吐量
- 可靠性提升
  - 数据安全
    - 通过镜像功能提高安全可靠性
  - 容错能力
    - 通过数据校验提供容错能力

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
