<div style="float: left; width: 64%; padding: 1%;">

# <span style="color: silver;"><span style="color: SlateBlue;">虚拟</span>M

<ul>

- 构成
  - 由主存和辅存共同构成
  - 在硬件和系统软件的共同管理下工作
- 透明性
  - 对于应用程序员而言是透明的
- 特点
  - 具有主存的速度
  - 具有辅存的容量

## <span style="color: silver;">concept

<ul>

### <span style="color: DarkRed;">地址</span> <span style="color: silver;">空间

<ul>

#### <span style="color: SlateBlue;">虚拟</span> <span style="color: silver;">~
- 地址空间统一编址
  - 将主存和辅存地址空间合并
  - 形成庞大的统一地址空间
- 用户编程自由度
  - 无需关注硬件限制
    - 不受主存容量限制
    - 不受程序存放位置限制
  - 提供透明的编程环境

#### <span style="color: GreenYellow;">type

<ul>

##### <span style="color: silver;"><span style="color: SlateBlue;">虚</span>地址( <span style="color: Gold;">逻辑</span>地址)
- 用户编程允许涉及的地址
- 对应的存储空间称为：
  - 虚拟空间
  - 程序空间

##### <span style="color: silver;"><span style="color: green;">实</span>地址(<span style="color: LightSkyBlue;">物理</span>地址)
- 实际的主存单元地址
- 对应的是主存地址空间(实地址空间)
- 虚地址比实地址要大很多

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/3f30148f78a751f6de56c12ee740b690d95cef0f05379cb11a3386b06baf0ec8.jpg)`  
图3.24虚拟存储器的三个地址空间

</ul>

</ul>

### <span style="color: silver;">CPU <span style="color: LimeGreen;">访问</span>机制
- CPU使用<span style="color: SlateBlue;">虚</span>地址时process：
  - 判断虚地址对应内容whether已装入主存
  - if 在主存中：
    - 通过地址变换直接访问主存指示的实际单元
  - ..不..：
    - 把包含这个字的一页或一段调入主存
      - 调入主存后再访问
    - 若主存已满：
      - 采用替换算法
      - 置换主存中的交换块

> pro：虚拟存储器只能采用回写法的原因（2016）

### <span style="color: silver;"> <span style="color: LimeGreen;">技术</span>特点
- 类似Cache技术：
  - 将辅存中经常访问的数据副本--> 主存
- 特殊机制：
  - 全相联映射：
    - 每个虚页面可存放到对应主存区域的任何空闲页位置
  - 回写法处理一致性：
    - 原因：缺页访问辅存代价大
    - 结果：不能每次写操作都同时写回磁盘

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
