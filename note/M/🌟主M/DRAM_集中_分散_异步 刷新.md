<span style="color: silver;">

<div style="float: left; width: 60%; padding: 1%;">

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

</div>
<div style="float: right; width: 36%; padding: 1%;">

|    |  <span style="color: LimeGreen;">集中</span>        |  <span style="color: Gold;">分散</span>      | <span style="color: purple;">异步</span>         |
|---------------------|------------------|------------------|------------------|
| time        | 集中period  | 分散到 T   | bus 空闲时间 |
| <span style="color: gray;">死</span>区       | 集中出现长~   | <b> \ </b> <br> (T 小延迟) |  分布更分散      |
| <span style="font-size: 10px;"> application scenario     | 可容忍间歇停顿   | need均匀延迟     | 高带宽利用率     |

- DRAM均 按  <span style="color: Gold;">行</span> 刷新

</div>
<div style="clear: both;"></div>
