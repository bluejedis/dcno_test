<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: silver;">Cache的 <span style="color: Gold;">一致</span>性问题

<ul>

### <span style="color: silver;"><span style="color: LimeGreen;">W</span>操作策略
- 目的：保持Cache和主存内容一致
- 分类：
  - 写命中策略
  - 写不命中策略

### <span style="color: LimeGreen;">W</span> <span style="color: silver;"><span style="color: LightSkyBlue;">命中</span>策略

> pro：直写法的特点（2015）、直写法是否需设修改位（2020）

<ul>

#### <span style="color: silver;"> <span style="color: Gold;">全</span> <span style="color: LimeGreen;">写</span>法(直写法、Write-through)
- 基本原理：
  - CPU同时写入Cache和主存
  - 替换时直接覆盖，无需写回
- 特点：
  - 实现简单
  - 保持主存数据正确性
  - 缺点：增加访存次数
- 写缓冲优化：
  - 位置：Cache和主存之间
  - 工作方式：
    - CPU同时写入Cache和写缓冲
    - 写缓冲再写入主存
  - 局限性：频繁写时可能溢出

> pro：回写法的修改位（2018、2020）

#### <span style="color: silver;"><span style="color: gray;">回</span><span style="color: LimeGreen;">写</span>法(write-back)
- 基本原理：
  - 仅写入Cache
  - 替换时才写回主存
- 特点：
  - 减少访存次数
  - 存在数据不一致风险
- 修改位(脏位)机制：
  - 1：块被修改，需写回
  - 0：块未修改，无需写回

</ul>

### <span style="color: silver;">~ <span style="color: gray;">不</span>~

<ul>

#### <span style="color: silver;"> <span style="color: LimeGreen;">W</span> <span style="color: Gold;">分配</span>法
- 处理步骤：
  - 更新主存单元
  - 调入主存块到Cache
- 特点：
  - 利用空间局部性
  - 缺点：每次需从主存读块

#### <span style="color: silver;"><span style="color: gray;">非</span>~
- 处理方式：
  - 仅更新主存单元
  - 不调入主存块
- 使用搭配：
  - 通常与全写法合用
  - 写分配法通常和回写法合用

</ul>

### <span style="color: silver;">Cache <span style="color: LimeGreen;">结构</span>设计

> pro：采用分离的指令Cache和数据Cache的主要目的（2014）

<ul>

#### <span style="color: silver;"> <span style="color: GreenYellow;">分离</span>Cache结构
- 背景：指令流水技术发展需求
- 优势：
  - 避免指令预取与数据存取冲突
  - 优化不同局部性特征
- 统一Cache特点：
  - 设计实现简单
  - 存在访问冲突

#### <span style="color: silver;"> <span style="color: Gold;">多级</span>Cache设计
- 二级Cache示例：
  - L1Cache（靠近CPU）：
    - 速度快，容量小
    - 指令数据通常分离
    - 采用写分配法和回写法
  - L2Cache：
    - 速度和容量居中
    - L1对L2使用全写法
    - L2对主存使用回写法
  - 优势：避免写缓冲饱和溢出

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/a36a40284b9aa454bc42de878bcab6fe9160cad5f6b92ce9054bac667f2a2cf5.jpg)`

</ul>

</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
