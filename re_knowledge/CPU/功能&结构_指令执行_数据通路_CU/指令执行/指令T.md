<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: LightSkyBlue;"><span style="color: LightSkyBlue;">指令</span></span> <span style="color: silver;">周期  

3I_4T
<ul>
 <span style="color: Gold;">时钟</span>~ ->机器~ -> <span style="color: LightSkyBlue;">指令</span>T 

###  <span style="color: silver;">concept

<ul>

- <span style="color: LightSkyBlue;">指令</span>周期
  - 定义：
    - CPU每 <span style="color: black;">取出</span>并<span style="color: green;">执行</span>一条<span style="color: LightSkyBlue;">指令</span>所需的全部时间
  - 特点：
    - 不同<span style="color: LightSkyBlue;">I</span>的<span style="color: LightSkyBlue;">指令</span>T might不同
    - 可用<span style="color: gray;">若干</span> <span style="color: black;">机器</span>T 来表示
      - every<span style="color: LightSkyBlue;">指令</span>T内的机器T数可以不等



![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/4cdf5401a046fb5fe39af366d76c0d8889d1154a1965f8d7673571ffd1641a97.jpg)  
图5.2<span style="color: LightSkyBlue;">指令</span>T和机器T的关系  


</ul>

###  <span style="color: silver;">不同<span style="color: LightSkyBlue;"><span style="color: LightSkyBlue;">指令</span></span>的$T$ <span style="color: Gold;">特点</span>

<ul>


####  <span style="color: silver;">无条件转移<span style="color: LightSkyBlue;">指令</span>JMP X：
  - 执行特点：
    - 不需要访问主存
    - 只包含取指阶段和执行阶段
  - 周期构成：
    -  <span style="color: LimeGreen;">取</span><span style="color: LightSkyBlue;">指</span>T（包括取指和分析）
    -  
    -  <span style="color: green;">执行</span>~

####  <span style="color: silver;">间接寻址<span style="color: LightSkyBlue;">指令</span>：
  - 操作数获取过程：
    - 第一次访存：
      - 有效<span style="color: DarkRed;">地址</span>
    - 第二次访存：
      - <span style="color: LimeGreen;">操作</span>数
  - 周期构成：
    - <span style="color: LimeGreen;">取</span><span style="color: LightSkyBlue;">指</span>T
    - <span style="color: LimeGreen;">间</span><span style="color: DarkRed;">址</span>~
    - <span style="color: green;">执行</span>~
  - 特点：间址周期位于取指周期和执行周期之间

####  <span style="color: silver;">带中断的<span style="color: LightSkyBlue;">指令</span>执行：
  - 中断检查：
    - CPU在每条<span style="color: LightSkyBlue;">指令</span>执行结束前 发出中断查询信号
    - 发现中断请求时 → 中断响应阶段（中断周期）
  - 完整T[^1]：
    -  <span style="color: LimeGreen;">取</span><span style="color: LightSkyBlue;">指</span>T
    -  <span style="color: LimeGreen;">间</span><span style="color: DarkRed;">址</span>~
    - <span style="color: green;">执行</span>~
    -  <span style="color: Gold;">中断</span>~

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/f7ac4456b5579efe301d3c745f4bafd3791739991e765a528a6dd737b49f8fa6.jpg)  
图5.3带有间址周期、中断周期的<span style="color: LightSkyBlue;">指令</span>T  

</ul>

>pro：<span style="color: LightSkyBlue;">指令</span>执行的过程（2011）  

###  <span style="color: silver;"><span style="color: LightSkyBlue;">指令</span>执行的具体过程

<ul>

####  <span style="color: silver;"><span style="color: LimeGreen;">取</span><span style="color: LightSkyBlue;">指</span>T
- 取<span style="color: LightSkyBlue;">指令</span>操作[^2]
  - 从PC指向的主存单元取出<span style="color: LightSkyBlue;">指令</span>(字)
  - 将<span style="color: LightSkyBlue;">指令</span>送至<span style="color: LightSkyBlue;">指令</span>寄存器
- PC更新操作
  - PC加"1"准备下一条<span style="color: LightSkyBlue;">指令</span>地址
  - 对于转移<span style="color: LightSkyBlue;">指令</span>：PC加"1"后会重新计算并更新PC值

####   <span style="color: silver;"><span style="color: LimeGreen;">间</span><span style="color: DarkRed;">址</span>~ (条件执行)
- judge if need 间接寻址
  - if so
    - → 间址T
    - get  <span style="color: LimeGreen;">操作</span>数的有效<span style="color: DarkRed;">地址</span>

####  <span style="color: silver;"><span style="color: green;">执</span>行~

- 取操作数
- 执行运算
- 存储操作数

####  <span style="color: silver;"> <span style="color: Gold;">中断</span>周期(条件执行)
- check if have 中断请求
- if so
  - 关闭中断
    - 保存断点
    - 修改PC值为中断服务程序入口地址
  - turn to 中断服务<span style="color: LightSkyBlue;">程序</span>执行
</ul>

>attention:  

<ul>

- 中断周期中的进栈操作:
  - SP减"1"not加"1"
  - 原因:
    - 计算机中的堆栈都是向低地址方向增长
    - 因此进栈时需要减"1"来指向新的栈顶位置
</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>

[^1]:all 包括 n个机器T

[^2]:双字I、三~ 与单~'
取指<span style="color: LimeGreen;">操作</span>different

[^3]:一次间址、两次~ 和多次~， <span style="color: LimeGreen;">操作</span> 不同

