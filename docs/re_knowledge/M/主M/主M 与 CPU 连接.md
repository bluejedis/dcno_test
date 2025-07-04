<div style="float: left; width: 64%; padding: 1%;">

# <span style="color: silver;"><span style="color: Gold;">主M</span>与 <span style="color: LimeGreen;">CPU</span>' <span style="color: GreenYellow;">连接  

<ul>

## <span style="color: Gold;">原理  

<ul>

- 主存储器与CPU的连接方式：
  - 通过三种总线连接：
    - 数据总线
    - 地址总线 
    - 控制总线
  - 总线特点：
    - 数据总线：位数与工作频率的乘积决定数据传输速率
    - 地址总线：位数决定最大可寻址内存空间
    - 控制总线：指示总线周期类型和I/O操作完成时刻

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/1e1d92cf5473f7cdbefec0c268399f79d298a75bd67083e238876b319130a603.jpg)  
图3.10主存储器与CPU的连接  

- 存储器扩展需求：
  - 单个芯片容量有限
  - 通过扩展技术集成多个芯片
  - 多个内存条和ROM芯片组成主存空间
  - 通过总线与CPU相连

</ul>

## <span style="color: silver;">主M <span style="color: LimeGreen;">容量</span>的 <span style="color: GreenYellow;">扩展  

<ul>

- 扩展需求：
  - 存储芯片容量限制：
    - 单个芯片容量有限
  - 扩展方向：
    - <span style="color: gray;">字</span>的扩充
    - <span style="color: LightSkyBlue;">位</span>~
  - 扩展目标：
    - 满足实际存储容量需求

### <span style="color: silver;"><span style="color: LightSkyBlue;">位</span>扩展法  

<ul>

- 概念：对字长进行扩展
- 应用场景：
  - CPU<span style="color: LightSkyBlue;">数据</span> <span style="color: Gold;">线</span>数 > 存储芯片~<span style="color: gray;">位</span>数
- 连接方式：
  - 各芯片的连接：
    - <span style="color: DarkRed;">地址</span>线 与系统总线并联
    - <span style="color: LightSkyBlue;">片</span><span style="color: LimeGreen;">选</span>线..
    - <span style="color: Gold;">R</span>/ <span style="color: LimeGreen;">W</span>控制线..
  - <span style="color: LightSkyBlue;">数据</span><span style="color: Gold;">线</span>连接：
    - 各芯片数据线 <span style="color: LimeGreen;">单独</span>引出
    - 连接到系统数据线
  - 工作方式：
    - 各芯片<u>同</u>时工作
- 实例：
  - 目标：组成8K×8位存储器
  - 使用：8片8K×1位RAM

![image](https://bluejedis.github.io/picx-images-hosting/test/image.eskko8o6z.webp) 
图3.11位扩展连接示意图  

</ul>

### <span style="color: silver;"><span style="color: gray;">字</span>~

<ul>

- 概念：对存储<span style="color: gray;">字</span>数量进行扩展
- 特点：
  - 存储字位数满足系统要求
- 连接方式：
  - 芯片地址线：
    - 与系统地址<span style="color: green;">低</span>位相连
  - 数据线和读/写控制线：
    - 与系统总线并联
  - 片选信号：
    - 由系统地址高位译码得到
  - 工作方式：
    - 各芯片分时工作

> pro：字扩展（或字位扩展）后存储芯片的地址范围（2010、2016）  

- 实例：用4片16K×8位RAM组成64K×8位存储器
- 地址分配：
  - 第一片：0000000000000000-0011111111111111
  - 第二片：0100000000000000-0111111111111111
  - 第三片：1000000000000000-1011111111111111
  - 第四片：1100000000000000-1111111111111111

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/44f1fe99a9391d96d9aeb0fb8712474bf298dbedaaa36321308e7bb49a6874d2.jpg)  
图3.12字扩展连接示意图  

</ul>

### <span style="color: silver;"><span style="color: gray;">字</span><span style="color: LightSkyBlue;">位</span>同时~

<ul>

- 概念：位扩展和字扩展的组合
- 功能：
  - add 存储<span style="color: gray;">字</span>数量、存储<span style="color: LightSkyBlue;">字长</span>
- 连接方式：
  - 位扩展芯片作为一组
  - 各组连接方式同位扩展
  - 系统地址高位译码产生片选信号
- 实例：用8片16K×4位RAM组成64K×8位存储器
  - 组织方式：
    - 每两片构成16K×8位存储器（位扩展）
    - 4组构成64K×8位存储器（字扩展）

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/1bd0ffee871eff245d8c4e998e914cbf1ee53c30a0465b58592027c9ed8d0501.jpg)  
图3.13字位同时扩展及CPU的连接图  

</ul>

</ul>

## <span style="color: silver;">0 存储芯片的<span style="color: DarkRed;">地址</span> <span style="color: Gold;">分配</span>和<span style="color: LightSkyBlue;">片</span><span style="color: LimeGreen;">选</span>  

<ul>

### <span style="color: silver;">concept

<ul>

- CPU访问存储单元需要两个步骤：

#### <span style="color: silver;"><span style="color: LightSkyBlue;">片</span><span style="color: LimeGreen;">选</span>：

<ul>

- <span style="color: Gold;">存储</span><span style="color: LimeGreen;">芯<span style="color: LightSkyBlue;">片
- ~ <span style="color: Gold;">信号</span>产生方法：
  - 线选法
  - 译码片选法

</ul>

#### <span style="color: silver;"><span style="color: gray;">字</span>选：

<ul>

- 在选定芯片中选择具体 <span style="color: Gold;">存储</span> <span style="color: LimeGreen;">单元
- process：
  - 由CPU送出N条低位地址线完成
  - N由片内存储容量2^N决定

</ul>

</ul>

### <span style="color: Gold;">线</span><span style="color: LimeGreen;">选</span><span style="color: silver;">法  

<ul>

- <span style="color: LightSkyBlue;">高</span>位地址线直接连接至存储芯片<span style="color: LightSkyBlue;">片</span><span style="color: LimeGreen;">选</span>端
  - 地址线为"<span style="color: gray;">0</span>"时选中对应存储芯片
- 每次only有一位有效

#### <span style="color: silver;">eg

<ul>

- 4片2K×8位存储芯片构成8K×8位存储器
- 低位地址线A10~A0作为字选线
- 片选信号分配如下：

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/d3e8ef9e2d826e33c5a04dddaf3613401040af874224f56e1f181b5f42aec2d2.jpg)  

- 优点：
  - <span style="color: gray;">不需要</span>地址<span style="color: gray;">译码</span>器
  - 线路简单
- 缺点：
  - <span style="color: DarkRed;">地址</span><span style="color: gray;">空间</span>不连续
  - 选片地址线必须<span style="color: gray;">分时</span>为<span style="color: green;">低</span>电平
  - 存储器空间 <span style="color: LimeGreen;">利用</span><span style="color: RoyalBlue;">率</span>低

</ul>

</ul>

### <span style="color: gray;">译码</span><span style="color: LightSkyBlue;">片</span><span style="color: LimeGreen;">选</span> <span style="color: silver;">法  

<ul>

- 高位地址线通过地址译码器产生片选信号

#### <span style="color: silver;">eg

<ul>

- 8片8K×8位存储芯片组成64K×8位存储器
  - 地址线16位，数据线8位
  - 需要8个片选信号
  - 使用74LS138作为地址译码器
  - 高3位用于片选：
    - A15A14A13=000选中第一片
    - A15A14A13=001选中第二片
    - 以此类推

</ul>

</ul>

## <span style="color: silver;">1 <span style="color: Gold;">存储器</span>与 <span style="color: LimeGreen;">CPU</span>的连接  

<ul>

### <span style="color: silver;">合理选择存储 <span style="color: LimeGreen;">芯</span><span style="color: LightSkyBlue;">片</span>  

<ul>

> pro：根据要求合理选择存储芯片（2009、2021）  

- 存储芯片 <span style="color: LimeGreen;">类型</span>选择：
  - ROM：存放系统程序、标准子程序和常数
  - RAM：用于用户编程
- 芯片<span style="color: gray;">数量</span>考虑：
  - 追求连线<span style="color: gray;">简单
  - 方便实用

</ul>

### <span style="color: silver;"><span style="color: DarkRed;">地址</span><span style="color: Gold;">线</span>的连接  

<ul>

> pro：地址范围与存储容量的对应关系（2016、2023）  

#### <span style="color: silver;">principle

<ul>

- CPU地址线数usually > 存储芯片
- 连接方式：
  - <span style="color: green;">低</span>位：CPU<span style="color: DarkRed;">地址</span><span style="color: Gold;">线</span>与存储芯片<span style="color: DarkRed;">地址</span><span style="color: Gold;">线</span>相连
    - <span style="color: gray;">字</span><span style="color: LimeGreen;">选</span>
    - 由片<span style="color: gray;">内</span><span style="color: Gold;">逻辑</span> 完成译码
  - <span style="color: LightSkyBlue;">高</span>位：用于 <span style="color: LimeGreen;">扩充</span>存储芯片
    - <span style="color: LightSkyBlue;">片</span><span style="color: LimeGreen;">选</span>
    - 由 <span style="color: GreenYellow;">外接</span><span style="color: gray;">译码器</span>完成译码

</ul>

#### <span style="color: silver;">eg

<ul>

- CPU：16位地址线(A15~A0)
- 存储芯片：1K×4位，10根地址线
- 连接方式：CPU的A9~ A0与存储芯片的A9~ A0相连

</ul>

</ul>

### <span style="color: silver;"><span style="color: deepskyblue;">数据</span><span style="color: Gold;">线</span>的连接  

<ul>

- CPU与存储芯片 <span style="color: deepskyblue;">数据</span><span style="color: Gold;">线</span>数相等：
  - 直接相连
- ..不等：
  - 对存储芯片 <span style="color: black;">扩位
  - 使数据位数 与CPU数据线数相等

</ul>

### <span style="color: silver;"><span style="color: Gold;">读</span>/ <span style="color: LimeGreen;">写</span><span style="color: LightSkyBlue;"> 命令</span>线的连接  

<ul>

- <span style="color: GreenYellow;">单</span>一 ~：
  - <span style="color: black;">直接</span>与存储芯片控制端相连
  - <span style="color: LightSkyBlue;">高</span>电平为 <span style="color: Gold;">读</span>， <span style="color: LimeGreen;">低</span>电平为<span style="color: LimeGreen;">写</span>
- <span style="color: Gold;">分开</span>'~：
  - 读命令线( <span style="color: Gold;">RD</span>)连接芯片 <span style="color: Gold;">读</span>控制端
  - 写命令线( <span style="color: LimeGreen;">WE</span>)连接芯片 <span style="color: LimeGreen;">写</span>控制端
  - 均为<span style="color: green;">低</span>电平<u>有效</u>

</ul>

### <span style="color: silver;"><span style="color: LightSkyBlue;">片</span><span style="color: LimeGreen;">选</span>线的连接  

<ul>

- <span style="color: gray;">决定</span>存储芯片whether被选中
- 取决于片选 <span style="color: Gold;">控制</span><span style="color: LightSkyBlue;">端</span>CS接收到的信号

#### <span style="color: LimeGreen;">M</span><span style="color: Gold;">REQ</span>

<ul>

- CPU要求 <span style="color: LimeGreen;">访</span><span style="color: Gold;">存</span>： <span style="color: LimeGreen;">M</span><span style="color: Gold;">REQ</span>为<span style="color: green;">低</span>电平
- CPU访问<span style="color: LightSkyBlue;">I</span>/ <span style="color: LimeGreen;">O</span>：~<span style="color: LightSkyBlue;">高</span>电平， <span style="color: Gold;">M</span>不工作

</ul>

</ul>

</ul>

</ul>

</ul>


</div>
<div style="float: right; width: 26%; padding: 1%;">



</div>
<div style="clear: both;"></div>
