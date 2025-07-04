<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: silver;"><span style="color: SlateBlue;">Cache</span>和 <span style="color: Gold;">主存</span> 的 <span style="color: GreenYellow;">映射</span>方式

- Cache行需要标记位和有效位:
  - 标记位:
    - 指明是主存中哪一块的副本
  - 有效位:
    - 说明Cache行中信息是否有效

- <span style="color: DarkRed;">地址</span> <span style="color: GreenYellow;">映射</span>:
  - 基本定义:
    - 把主存地址空间映射到Cache地址空间
    - 按规则将主存信息装入Cache
  - 映射方法:
    - 共有3种不同的映射方法

<ul>

### <span style="color: gray;">直接 <span style="color: silver;">~

<ul>

#### <span style="color: silver;">concept
- 主存块只能装入Cache唯一位置
  - 每个主存块对应固定的Cache位置
  - 无法选择其他位置存放
- 块冲突情况
  - 若对应位置已有内容则产生冲突
  - 需要替换已有块
- 特点分析
  - 实现方面
    - 硬件实现简单
    - 映射规则固定不灵活
  - 性能方面
    - 块冲突概率最高
    - Cache空间利用率最低

> pro：直接映射的地址结构及映射关系的分析（2010、2011、2015）

#### <span style="color: silver;">映射 <span style="color: GreenYellow;">关系
- 公式:
  - Cache行号 $=$ mod Cache
- 规则:
  - 假设Cache有$2^c$行,主存有$2^m$块
  - 主存块映射规律:
    - 第0块、第$2^c$块、第$2^{c+1}$块映射到Cache第0行
    - 第1块、第$2^c+1$块、第$2^{c+1}+1$块映射到Cache第1行
  - 主存块号低$c$位即为Cache行号
  - Cache行需设置$t=m-c$位标记

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/0d4d9150e1b74972905e0f2411e001d19ac079c052b685d6319df172fd1f46af.jpg)`  
图3.18Cache和主存之间的直接映射方式

#### <span style="color: DarkRed;">地址</span> <span style="color: silver;">结构
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/1a310ec397e1e430790891edc7b4fe7034517d79896535099a72318e362d5cfc.jpg)`

#### <span style="color: LimeGreen;">访</span><span style="color: Gold;">存
- 根据访存地址 中间c位 找到Cache <span style="color: LimeGreen;">行</span>
- <span style="color: Gold;">compare</span> Cache行 标记 & 主存地址高t位 标记:
     - <span style="color: gray;">=</span> & 有效位为 <span style="color: LimeGreen;">1</span>:
       - 命中
       - 根据块内地址在Cache行中存取
     - <span style="color: purple;">≠</span> || 有效位为<span style="color: purple;">0</span>:
       - 不命中
       - 从主存读块到Cache行
       - 设置有效位和标记
       - 将内容送CPU

</ul>

### <span style="color: Gold;">全</span> <span style="color: GreenYellow;">相</span><span style="color: LightSkyBlue;">联</span> <span style="color: silver;">~

<ul>

#### <span style="color: silver;">concept
- 主存块可装入Cache任何位置

- 每行标记指示来自主存的哪一块

- 优点:
  - Cache块冲突概率低
  - 空间利用率高
  - 命中率高

- 缺点:
  - 标记比较速度慢
  - 实现成本高

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/a8989ceb071e5ad8c8d6dca134a27f62a4c6286c510cc52ef891f745bf53aba0.jpg)`  
图3.19Cache和主存之间的全相联映射方式

#### <span style="color: DarkRed;">地址</span> <span style="color: LimeGreen;">结构
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/d778483358bb5cfaa81acdb4053dea9aacce5ec9ea238257e705ba9e2fca92cd.jpg)`

#### <span style="color: LimeGreen;">访</span><span style="color: Gold;">存
- <span style="color: Gold;">compare</span>主存地址高位标记与Cache各行标记
- 命中情况:
  - 有相等且有效位为1时:
    - 命中
    - 根据块内地址取信息
  - 都不相等时:
    - 不命中
    - 从主存读块到空闲行
    - 设置有效位和标记
    - 将内容送CPU

> pro：根据地址结构和比较器数量判断映射方式（2018）

#### <span style="color: green;">硬件</span> <span style="color: Gold;">实现
- 比较器配置:
  - 每个Cache行设置一个比较器
  - 比较器位数等于标记字段位数
- 存取方式:
  - 采用"按内容访问"的存取方式
- 大容量Cache限制:
  - 不适合使用，原因:
    - 时间开销大
    - 硬件开销大

</ul>

### <span style="color: gray;">组</span><span style="color: GreenYellow;">相</span><span style="color: LightSkyBlue;">联 ~

> pro：组相联映射方式的原理（2009、2016、2018～2020、2023）

<ul>

#### <span style="color: silver;">concept
将Cache分成Q个大小相等的组
- <span style="color: Gold;">主存</span><span style="color: LightSkyBlue;">块</span> 映射:
     - 每个主存块可以装入固定组中的任意一行
     - 映射方式
       - 组间：采用直接映射
       - 组内：采用全相联映射
- <span style="color: silver;">映射</span><span style="color: Gold;">特性</span>
    - 是对直接映射和全相联映射的折中
    - 特殊情况
      - Q=1时变为全相联映射
      - Q=Cache行数时变为直接映射
- <span style="color: gray;">路数</span><span style="color: Gold;">特点</span>
  - 基本关系
    - 路数越大，每组Cache行数量越大
    - 块冲突概率越低，但相联比较电路越复杂
  - 性能权衡
    - 适当路数可使性能接近全相联
    - 成本接近直接映射

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/705d35296eca71ed8eded974c3d677da76008d584c3b528fa5e8971962c6d880.jpg)`  
图3.20Cache和主存之间的二路组相联映射方式

#### <span style="color: LimeGreen;">映射</span> <span style="color: silver;">关系
- Cache组号 = mod Cache 组数（Q）
- 地址结构：
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/16468247b7f68d80ea35bf713452faaeaab1af0cc4620f1f67e90b71bd4d66a4.jpg)`

> pro：组相联映射的访存过程及Cache缺失处理过程（2020）

#### <span style="color: LimeGreen;">访</span><span style="color: Gold;">存
- according to访存地址中间组号 find 对应Cache组
- compare<span style="color: gray;">组内</span>每行标记 & <span style="color: Gold;">主存</span>地址高位标记
- 命中:
  - = & 有效位为1
    - 命中
      - 根据块内地址在Cache行中存取
  - ≠ || 有效位为0
    - 不命中
      - 从主存读块到对应组空闲行
      - 设置有效位和标记
      - 将内容送CPU

> pro：组相联映射中比较器的个数和位数（2022）

#### <span style="color: green;">硬件</span> <span style="color: silver;">实现
- 比较器需求
  - 直接映射：1个比较器
  - r路组相联：r个比较器

> pro：直接映射、组相联映射相关标记位及总容量的分析（2010）

#### <span style="color: silver;">eg
主存条件：
- 地址空间：256MB
- 按字节编址
- 数据Cache：8个Cache行
- 行长：64B

##### <span style="color: silver;">q&a:
1. Cache总 <span style="color: LimeGreen;">容量</span>计算
   - 总容量 = 存储容量 + 标记阵列容量
   - 不考虑脏位和替换算法位

> pro：直接映射相关标记位的分析（2015、2021）

> attention：

###### <span style="color: silver;"> <span style="color: GreenYellow;">标记</span>阵列结构
- 每Cache行对应一个标记项
  - 包括：有效位、脏位、替换算法位、标记位
- 组相联特点
  - 每组各行标记项排成一行
  - 各组从上到下排列成二维标记阵列

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/57f1a99d258e755109902e23acf15b394fc66b1b280f1f9dca674653a358810b.jpg)`  
图3.21二路组相联的标记阵列示意图

###### <span style="color: silver;">存储 <span style="color: LimeGreen;">容量</span>计算
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/683ed3f03365e410bb54f631a3aa7975ef5c257a5d5fb4a06bc06596f36764f8.jpg)`  
图3.22Cache行的存储容量示意图

- 标记字段长度计算
  - 主存地址：28位(256MB=2^28B)
  - 块内地址：6位(2^6B=64B)
  - 行号：3位(2^3=8)
  - 标记字段：19位(28-6-3)
- 总容量：8×(1+19+512)=4256位

2. 主存<span style="color: DarkRed;">地址</span>3200映射分析
   - 直接映射：Cache行号为2
   - 二路组相联：组号2(行号4或5)

3. <span style="color: LimeGreen;">访</span> <span style="color: Gold;">存</span>过程(地址0123456H)
     - 地址划分
       - 主存标记位：19位
       - 块号：3位
       - 块内地址：6位
     - 访问步骤
       - 根据块号查Cache对应行
       - 比较主存标记位
       - 检查有效位
       - 根据结果进行相应操作

##### <span style="color: silver;"> <span style="color: LimeGreen;">映射</span>方式 <span style="color: Gold;">比较
- 映射范围
  - 直接映射：固定行
  - 全相联映射：所有行
  - N路组相联：N行
- 性能对比
  - 命中率：全相联>组相联>直接映射
  - 判断开销：直接映射<组相联<全相联
  - 空间开销：直接映射<组相联<全相联

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
