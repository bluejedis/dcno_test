<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: silver;"> <span style="color: Gold;">虚拟</span>存储器Virtual memory与<span style="color: SlateBlue;">Cache</span>的比较

<ul>

### <span style="color: silver;">same:
- 目标都是提高系统性能
  - 都有容量、速度、价格梯度
- 数据组织方式相似
  - 都划分为信息块作为交换单位
  - 虚存系统信息块更大
- 管理机制相似
  - 都有地址映射
  - 都有替换算法
  - 都有更新策略
- 原理相似
  - 都依据局部性原理
  - 采用"快速缓存"思想
  - 将活跃数据放在高速部件

### <span style="color: silver;">不同
- 解决 <span style="color: Gold;">目标</span>不同
  - Cache解决系统速度
  - 虚拟存储器解决主存容量

- 实现<span style="color: Goldenrod;">方式</span>不同
  - <span style="color: SlateBlue;">Cache</span>全由<span style="color: green;">硬件</span>实现
    - 对所有程序员透明
  - 虚拟存储器由OS和硬件共同实现
    - 对系统程序员不透明
    - 对应用程序员透明

> pro：Cache缺失和缺页的处理开销对比（2016）

- 不命中影响不同
  - CPU速度约为Cache的10倍
  - 主存速度为硬盘的100倍以上
  - 虚拟存储器不命中对系统影响更大

- 访问通路不同
  - CPU与Cache和主存有直接通路
    - Cache不命中时可直接与CPU通信
  - CPU与辅存无直接通路
    - 虚存不命中需先调入主存

</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
