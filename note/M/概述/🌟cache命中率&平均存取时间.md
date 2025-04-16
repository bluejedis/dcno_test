zhuanti
<div style="float: left; width: 64%; padding: 1%;">

# Cache命中率和命中次数

## 命中次数（Cache Hits）
- 从缓存中成功获取数据的次数
  - 当CPU需要读取或写入数据时，首先会检查缓存，如果数据在缓存中找到，就称为一次"命中"。

## 命中率（Cache Hit Rate）
- 缓存命中的次数占总访问次数的比例
  - H = N<span style="color: purple;">c</span>/(N<span style="color: purple;">c</span>+N<span style="color: Gold;">m</span>)


## 影响因素
缓存命中率受多种因素影响：
1. 缓存大小：通常缓存越大，命中率越高
2. 缓存替换策略（如LRU、FIFO等）
3. 程序的局部性（时间局部性和空间局部性）
4. 缓存映射方式（直接映射、组相联、全相联）

高命中率（如90%以上）通常表示缓存系统效率良好，而低命中率可能意味着需要优化缓存策略或增加缓存容量。


<br>
<br>
---

## 题目重述
在 Cache 和主存构成的两级存储体系中：
- Cache 存取时间 = 100 ns
- 主存存取时间 = 1000 ns
- Cache 和主存是**同时访问**的（即并行访问）
- 要求**有效（平均）存取时间 ≤ Cache 存取时间的 115%**（即 ≤ 115 ns）
- 问：Cache 的命中率至少应为多少

---

### 解题思路
#### 1. 理解并行访问的 Cache-主存系统
在**同时访问（并行访问）**的存储系统中：
- CPU **同时**向 Cache 和主存发出访问请求。
  - 如果数据在 Cache 中命中（概率 = $ H $），则直接使用 Cache 的数据（时间 = 100 ns），**忽略主存的访问**。
  - 如果数据未命中（概率 = $ 1 - H $），则需要等待主存的访问完成（时间 = 1000 ns），因为 Cache 的访问结果无效。

因此，平均访问时间（Effective Access Time, EAT**
$$
T = {\bold{\color{gray}H}} \times T_{\text{{\color{purple}{c}}ache}} + (1 - {\bold{\color{gray}H}}) \times T_{{\text{\color{gold}m}ain}}
$$
其中：
- $ H $ = 命中率
- $ T_{\text{cache}} = 100 \text{ ns} $
- $ T_{\text{main}} = 1000 \text{ ns} $

#### 2. 题目约束条件
题目要求：
$$
EAT \leq 115\% \times T_{\text{cache}}
$$
即：
$$
EAT \leq 1.15 \times 100 = 115 \text{ ns}
$$

#### 3. 建立不等式并求解
将 $ EAT $ 的表达式代入约束条件：
$$
H \times 100 + (1 - H) \times 1000 \leq 115
$$

展开并解这个不等式：
$$
100H + 1000 - 1000H \leq 115 \\
-900H + 1000 \leq 115 \\
-900H \leq -885 \\
H \geq \frac{885}{900} \\
H \geq 0.9833 \text{（即 98.33\%）}
$$

---

### 关键点
1. **并行访问**的 $ EAT $ 公式：
   $$
   EAT = H \times T_{\text{cache}} + (1 - H) \times T_{\text{main}}
   $$
2. 解不等式时注意方向（$ H \geq \frac{885}{900} $）。
3. 选项需要严格满足“至少”，因此选 **D. 99%**。



</div>
<div style="float: right; width: 26%; padding: 1%;">


</div>
<div style="clear: both;"></div>