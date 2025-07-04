 <span style="color: silver;">

<div style="float: left; width: 64%; padding: 1%;">




##  <span style="color: silver;">❓TC2: 交叉编址多模块存储器的<span style="color: gray;">存储周期数</span>计算

###  <span style="color: silver;">通式:
1. **确定存储模块数量和数据总线宽度**：模块数 = N，总线宽度 = W 位。
2. **确定访问方式**：
   - 同时启动or轮流启动
     - 每个<span style="color: LimeGreen;">模块</span> 读/写位数 = 数据总线位数 → <span style="color: LightSkyBlue;">轮流</span>启动
     - <span style="color: BurlyWood;">一次</span> 并行读/写的<span style="color: gray;">总</span>位数=总线宽度 →  <span style="color: Gold;">同时</span> ~

3. **计算变量占用的存储单元**：
   - 变量大小 / 模块数据位宽 = 占用行数（向上取整）
4. **确定起始模块和跨模块情况**：
   - 根据地址最低 log₂m 位确定起始模块 (m为模块数)
   - 计算跨模块的行数
5. **计算存储周期数**：
   - <span style="color: LightSkyBlue;">轮流</span>启动方式下，周期数 = 总行数
   -  <span style="color: Gold;">同时</span> ~ ，周期数 = 跨模块的行数

###  <span style="color: silver;">用通式解题:
####  <span style="color: silver;">题目重述
- 计算机主存按字节编址
  - 由4个64M×8位的DRAM芯片组成
  - 采用交叉编址方式
  - 存储器总线宽度为32位
  - double型变量x的主存地址为804001AH
- 问读取x需要的存储周期数
####  <span style="color: silver;">求解步骤:
1. **模块数和总线宽度**：
   - 4 个模块
   - 总线宽度 32 位
2. **访问方式**：
   -  4 × 8 位 = 32 位，故为同时启动
3. **变量占用空间**：
   - 此芯片 8bit → 1B
   - double 型占 8B，需占用 8B / 1B（每模块每行）= 8 行
   - 但实际跨模块计算
     - 一个变量的数据量exceed 单个模块的连续存储能力时
     - 数据会自动"跨越"到下一个模块存储
     - 多个模块协同工作才能完整读取
  
4. **起始模块**：地址 804 001AH 最低 2 位为 10（二进制），起始模块为 2（编号 0~3）。

编号依据:
00 0
01 1
10 2
11 3

   <br>

   - 地址的**最低 log₂(模块数) 位**表示模块编号
   - 本题 log₂4 = 2，所以取地址最低2位
  
5. **跨模块行数**：
   模块编号范围始终是0到（模块数-1）
   m=4模块编号循环：
   - 模块 2：存储 2B（地址 1A~1B）。
   - 模块 3：存储 4B（地址 1C~1F）。
   - 模块 0：存储 2B（地址 20~21）。
   - 共需 3 行（模块 2、3、0 各一行）。
6. **存储周期数**：同时启动，每次一行，共 3 周期。



</div>
<div style="float: right; width: 26%; padding: 1%;">




<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>



<br>
← H 表示 16 进制

###  <span style="color: silver;">十六进制转二进制的方法

####  <span style="color: silver;">基本原理

- **1位十六进制数 = 4位二进制数**
- 因为16 = 2⁴，所以每个十六进制数字可以精确对应4个二进制位

####  <span style="color: silver;">转换步骤（以804001AH为例）

1. **拆分每一位十六进制数**：
   ```
   8   0   4   0   0   1   A
   ```

2. **查表转换每个数字**：
   | 十六进制 | 二进制 |
   |----------|--------|
   | 0        | 0000   |
   | 1        | 0001   |
   | 4        | 0100   |
   | 8        | 1000   |
   | A        | 1010   |

3. **逐位转换**：
   ```
   8 → 1000
   0 → 0000
   4 → 0100
   0 → 0000
   0 → 0000
   1 → 0001
   A → 1010
   ```

4. **组合结果**：
   ```
   804001AH → 1000 0000 0100 0000 0000 0001 1010
   ```

###  <span style="color: silver;">四体交叉编址M 模块取$log_{2}M$ 最低2位 ← 编号依据:

根据最低2位编号起始依据:
00 0
01 1
10 2
11 3


</div>
<div style="clear: both;"></div>