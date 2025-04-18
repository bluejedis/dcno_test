 <span style="color: silver;">
 
<div style="float: left; width: 64%; padding: 1%;">

##  <span style="color: silver;">TC1: <span style="color: gray;">内存容量</span>计算
<ul>

###  <span style="color: silver;">通式:容量 = N_片 × N_位 × r × c × bit

(没给 默认1bit)


####  <span style="color: silver;">求解步骤:
1. 确定DRAM芯片数量：16个  
2. 确定每个芯片的位平面数量：4个  
3. 确定每个位平面的行数和列数：4096行 × 4096列  
4. 假设每个存储单元存储1位数据  
5. 计算总容量：  
   总容量 = 16 × 4 × 4096 × 4096 × 1 bit  
   转换为MB：总容量 = (16 × 4 × 4096 × 4096) / (8 × 1024 × 1024) MB  

###  <span style="color: silver;">相关知识点补充:
- **DRAM芯片**：动态随机存取存储器，由多个存储单元组成，每个单元通常存储1位数据。  
- **位平面（Bank）**：DRAM芯片内部可以独立操作的存储区域，多个位平面可以并行工作以提高性能。  
- **存储阵列**：由行和列组成的矩阵结构，行列交叉点是一个存储单元。  
- **容量单位换算**：  
  1 Byte = 8 bits  
  1 KB = 2^10 Bytes  
  1 MB = 2^20 Bytes  

</ul>

---
##  <span style="color: silver;">TC2: DRAM芯片的 <span style="color: Gold;">行</span><span style="color: LightSkyBlue;">列</span>地址划分与刷新开销优化
<ul>

###  <span style="color: silver;">约束条件:
对于容量为 $ N \times 1 $ 位的 DRAM 芯片，行列划分 $ r \times c $ 应满足：
1. $ r \times c = N $（容量匹配）
2. 行列地址引脚数 $ \lceil \log_2 r \rceil + \lceil \log_2 c \rceil $ 最小化
   - （引脚最少）
3. $ r $ 尽量接近 $ c $ 
   - 以减少刷新开销（DRAM 按行刷新）
   - 行数minize, 更少刷新更快



###  <span style="color: silver;">相关知识点补充:
1. **DRAM结构**：DRAM 芯片由存储阵列（行×列）组成，行列地址分时复用以减少引脚数。
2. **刷新开销**：DRAM 需要定期刷新（按行进行），行数越少刷新开销越小，但行列均衡可平衡引脚数和性能。
3. **地址引脚最小化**：行列地址位数之和应最小化，通常选择 $ r $ 和 $ c $ 为 2 的幂次方且接近。

###  <span style="color: silver;">用通式解题:
1. **选项分析**：
   - A: $ 2048 \times 1 $ → 引脚数 = 11 + 0 = 11，刷新开销大（行数过多）。
   - B: $ 64 \times 32 $ → 引脚数 = 6 + 5 = 11，行列接近。
   - C: $ 32 \times 64 $ → 引脚数 = 5 + 6 = 11，行列接近。
   - D: $ 1 \times 2048 $ → 引脚数 = 0 + 11 = 11，刷新开销最小但行列极端不平衡。

2. **优化选择**：B 和 C 引脚数相同且行列均衡，但 DRAM 通常优先减少行数以降低刷新开销（行数更少刷新更快），因此选 **C**（$ r=32 $, $ c=64 $）。
</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

- 容量 = N_片 × N_位 × r × c × bit

对于容量为 $ N \times 1 $ 位的 DRAM 芯片，行列划分 $ r \times c $ 应满足：
1. $ r \times c = N $（容量匹配）
2. 行列地址引脚数 $ \lceil \log_2 r \rceil + \lceil \log_2 c \rceil $ 最小化
   - （引脚最少）
3. $ r $ 尽量接近 $ c $ 
   - 以减少刷新开销（DRAM 按行刷新）
   - 行数minize, 更少刷新更快

</div>
<div style="clear: both;"></div>