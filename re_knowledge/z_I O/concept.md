<div style="float: left; width: 64%; padding: 1%;">

# <span style="color: silver;">\*concept

<ul>

## <span style="color: silver;">\* I/O系统

<ul>

- 输入/输出是以主机为中心而言的
  - 将信息从外部设备传送到主机称为输入，反之称为输出
  - 输入/输出系统解决的主要问题是对各种形式的信息进行输入和输出的控制

### <span style="color: silver;">concept

<ul>

- 外部设备
  - 包括输入/输出设备及通过输入/输出接口才能访问的外存储设备
- <span style="color: GreenYellow;">接口</span>
     - 在各个外设与主机之间传输数据时进行各种协调工作的逻辑部件
     - 协调包括传输过程中速度的匹配、电平和格式转换等
- <span style="color: LightSkyBlue;">I</span>
  - 用于向计算机系统输入命令和文本、数据等信息的部件
  - 键盘和鼠标是最基本的输入设备
- <span style="color: Gold;">O</span>
     - 用于将计算机系统中的信息输出到计算机外部进行显示、交换等的部件
     - 显示器和打印机是最基本的输出设备
- <span style="color: silver;">外M
     - 指除计算机内存及CPU缓存等外的存储器，如硬磁盘、光盘等

</ul>

### <span style="color: silver;"> <span style="color: LimeGreen;">构成</span>

<ul>

- I/O<span style="color: LightSkyBlue;">指令</span>：实现CPU与I/O设备的信息交换
- I/O<span style="color: green;">硬件</span>
  - 包括外部设备、设备控制器和接口、I/O总线等
  - 通过设备控制器来控制I/O设备的具体动作
  - 通过I/O接口与主机（总线）相连

</ul>

### <span style="color: silver;"> <span style="color: Gold;">控制</span>方式

<ul>

- 程序 <span style="color: LimeGreen;">查询</span>方式
  - 由CPU通过程序不断查询I/O设备是否已做好准备
- 程序<span style="color: SlateBlue;">中断</span>方式
  - 只在I/O设备准备就绪并向CPU发出中断请求时才予以响应
- <span style="color: DarkRed;">DMA</span>方式
  - 主存和I/O设备之间有一条直接数据通路
  - 无须调用中断服务程序
- <span style="color: LightSkyBlue;">通道</span>方式
  - 在系统中设有通道控制部件
  - 每个通道都挂接若干外设
  - 主机只需启动有关通道，通道将执行通道程序完成I/O操作

</ul>

### <span style="color: silver;">外部设备

<ul>

#### <span style="color: silver;"><span style="color: LightSkyBlue;">I

<ul>

##### <span style="color: silver;">键盘

<ul>

- 最常用的输入设备，通过它可发出命令或输入数据

</ul>

##### <span style="color: silver;">鼠标

<ul>

- 常用的定位输入设备
- 把用户的操作与计算机屏幕上的位置信息相联系

</ul>

</ul>

#### <span style="color: silver;"> <span style="color: Gold;"> O

<ul>

##### <span style="color: silver;">显示器

<ul>

- 主要参数：
  - 屏幕大小
    - 以对角线长度表示，单位为英寸
    - 常用的有12~32英寸等
  - 分辨率
    - 能表示的像素个数
    - 如800×600、1024×768和1280×1024等
  - 灰度级
    - 表示像素点的亮暗差别或颜色的不同
    - 典型的有8位（256级）、16位等
  - 刷新
    - 在光点消失之前重新扫描显示
  - 刷新频率
    - 单位时间内扫描整个屏幕内容的次数
    - 通常为60~120Hz
  - 显示存储器（VRAM）
    - 也称刷新存储器
    - 存储容量计算：
      - VRAM容量=分辨率×灰度级位数
      - VRAM带宽=分辨率×灰度级位数×帧频

</ul>

##### <span style="color: silver;">printer

<ul>

- 用于将计算机的处理结果打印在相关介质上

<ul>

###### <span style="color: silver;">针式~

<ul>

- 擅长"多层复写打印"
- 工作原理简单，造价低廉
- 耗材便宜
- 打印分辨率和速度不够高

</ul>

###### <span style="color: silver;">喷墨式~

<ul>

- 基于三基色原理
- 可实现高质量彩色打印

</ul>

###### <span style="color: silver;">激光~

<ul>

- 结合激光技术和电子显像技术
- 打印质量高、速度快、处理能力强

</ul>

</ul>

</ul>

#### <span style="color: silver;">外部M（辅存）

<ul>

##### <span style="color: silver;"><span style="color: SlateBlue;">磁</span>表面M

<ul>

- 把磁性材料涂在金属铝或塑料表面上作为载磁体
- 包括磁盘存储器、磁带存储器和磁鼓存储器

</ul>

##### <span style="color: silver;">固态硬盘（SSD）

<ul>

- 采用高性能Flash存储器作为硬盘
- 需要其他硬件和软件的支持

</ul>

##### <span style="color: silver;">光盘M

<ul>

- 利用光学原理读/写信息的存储装置
- 采用聚焦激光束对盘式介质以非接触方式记录信息
- 系统组成：
  - 光盘片
  - 光盘驱动器
  - 光盘控制器

</ul>

</ul>

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
