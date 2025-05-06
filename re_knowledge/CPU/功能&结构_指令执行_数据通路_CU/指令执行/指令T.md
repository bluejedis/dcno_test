<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: LightSkyBlue;">指令</span> <span style="color: silver;">周期  

<ul>

###  <span style="color: silver;">concept

<ul>

- 指令周期
  - 定义：
    - CPU每 <span style="color: black;">取出</span>并<span style="color: green;">执行</span>一条指令所需的全部时间
  - 特点：
    - 不同指令的指令周期可能不同
    - 可用<span style="color: gray;">若干</span> <span style="color: black;">机器</span>T 来表示
      - every指令T内的机器T数可以不等



![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/4cdf5401a046fb5fe39af366d76c0d8889d1154a1965f8d7673571ffd1641a97.jpg)  
图5.2指令T和机器T的关系  
  - （a）定长的机器T
  - （b）不定长的机器T

</ul>

###  <span style="color: silver;">不同<span style="color: LightSkyBlue;">指令</span>的$T$ <span style="color: Gold;">特点</span>

<ul>

- 指令周期的类型和特点：
  - 无条件转移指令JMP X：
    - 执行特点：
      - 不需要访问主存
      - 只包含取指阶段和执行阶段
    - 周期构成：
      - 取指周期（包括取指和分析）
      - 执行周期

  - 间接寻址指令：
    - 操作数获取过程：
      - 第一次访存：获取有效地址
      - 第二次访存：获取操作数
    - 周期构成：
      - 取指周期
      - 间址周期
      - 执行周期
    - 特点：间址周期位于取指周期和执行周期之间

  - 带中断的指令执行：
    - 中断检查：
      - CPU在每条指令执行结束前发出中断查询信号
      - 发现中断请求时进入中断响应阶段（中断周期）
    - 完整周期构成：
      - 取指周期
      - 间址周期
      - 执行周期
      - 中断周期
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/f7ac4456b5579efe301d3c745f4bafd3791739991e765a528a6dd737b49f8fa6.jpg)  
图5.3带有间址周期、中断周期的指令周期  

</ul>

>pro：指令执行的过程（2011）  

### 指令执行的具体过程

<ul>

- CPU执行指令的过程：
  -  <span style="color: LimeGreen;">取</span>指周期
       - 取指令操作
         - 从PC指向的主存单元取出指令
         - 将指令送至指令寄存器
       - PC更新操作
         - PC加"1"准备下一条指令地址
         - 对于转移指令：PC加"1"后会重新计算并更新PC值
  
  -  <span style="color: gray;">间</span>址周期(条件执行)
      - 判断是否需要间接寻址
      - 如需要则进入间址周期获取操作数的有效地址
  
  - <span style="color: green;">执</span>行周期
    - 取操作数
    - 执行运算
    - 存储操作数
  
  - 中<span style="color: Gold;">断</span>周期(条件执行)
    - 检测是否有中断请求
    - 如有中断请求则：
      - 关闭中断
      - 保存断点
      - 修改PC值为中断服务程序入口地址
      - 转向中断服务程序执行
</ul>

>attention:  

<ul>

- 中断周期中的进栈操作:
  - SP减"1"而不是加"1"
  - 原因:
    - 计算机中的堆栈都是向低地址方向增长
    - 因此进栈时需要减"1"来指向新的栈顶位置
</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
