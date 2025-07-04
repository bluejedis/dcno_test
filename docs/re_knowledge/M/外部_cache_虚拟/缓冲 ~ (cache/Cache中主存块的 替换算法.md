<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: silver;">Cache中<span style="color: Gold;">主存</span>块的 <span style="color: LimeGreen;">替换</span>算法

<ul>

### <span style="color: silver;">concept
- 替换算法使用场景：
  - 需要使用替换算法的映射方式：
    - 全相联映射
    - 组相联映射
  - 不需要使用替换算法的映射方式：
    - 直接映射
      - 原因：主存块只能放到唯一固定Cache行

### <span style="color: GreenYellow;">type

<ul>

#### <span style="color: silver;">随机( <span style="color: Gold;">RAND</span>)
- 随机确定替换的Cache行
- 特点：
  - 实现简单
  - 未依据局部性原理
  - 命中率可能较低

#### <span style="color: silver;">先进先出(<span style="color: gray;">F</span>I<span style="color: gray;">F</span>O)
- 选择最早调入的Cache行进行替换
- 特点：
  - 容易实现
  - 未依据局部性原理
  - 最早进入的块可能仍常用

> pro：组相联映射中LRU算法的命中分析（2012、2021）

#### <span style="color: silver;">近期最少使用( <span style="color: Gold;">L</span><span style="color: gray;">R</span><span style="color: green;">U</span>)
- 基本原理：
  - 依据程序访问的局部性原理
  - 选择近期未访问的Cache行替换
  - 属于堆栈类算法
  - 平均命中率高于FIFO

> pro：LRU替换位及其位数的计算（2018、2020）

<ul>

##### <span style="color: silver;">(1) <span style="color: GreenYellow;">细节
- 计数器设置：
  - 每个Cache行设置计数器(LRU替换位)
  - 计数值记录主存块使用情况
  - 位数与Cache组大小相关：
    - 二路：1位LRU位
    - 四路：2位LRU位

- 替换过程示例：
  - 条件：
    - 四路组相联
    - 5个主存块{1,2,3,4,5}映射到同一组
    - 访问序列{1,2,3,4,1,2,5,1,2,3,4,5}

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/172e58f1cfb7469387af458dc7e49c1ea931605bc2c9081f5e57a4932c9604de.jpg)`  
图3.23LRU算法的替换过程示意图

- 计数器变化规则：
  - 命中时：
    - 命中行计数器清零
    - 比其低的计数器加1
    - 其余不变
  - 未命中且有空闲行：
    - 新装入行计数器置0
    - 其余全加1
  - 未命中且无空闲行：
    - 计数值为3的行被替换
    - 新装入行计数器置0
    - 其余全加1

##### <span style="color: silver;">(2) <span style="color: LimeGreen;">抖动</span>现象
- 发生条件：集中访问存储区超过Cache组大小
- 示例：
  - 访问序列：1,2,3,4,5,1,2,3,4,5,...
  - Cache每组4行
  - 结果：命中率为0

</ul>

#### <span style="color: silver;">最不<u>经常</u>使用(L <span style="color: Gold;">F</span>U)算法
- 基本原理：
  - 换出一段时间内访问次数最少的Cache行
- 实现方式：
  - 每行设置计数器
  - 新行装入从0开始计数
  - 每次访问计数器加1
  - 替换时选择计数值最小的行

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
