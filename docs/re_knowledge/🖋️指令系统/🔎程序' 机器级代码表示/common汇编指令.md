<div style="float: left; width: 64%; padding: 1%;">

#  <span style="color: silver;">程序' 机器级<span style="color: LightSkyBlue;">代码</span>表示  

<ul>

>pro：涉及过汇编代码的真题的年份（2012、2014、2015、2017、2019、2023）  

-  <span style="color: silver;">本节是2022年才新增的考点
     - 历年统考真题曾多次以综合题的形式考查过
     - 难度较大
     - 不少跨考生对此无从下手
     - 通过本节的学习后，应能从容应对
-  <span style="color: silver;">统考大纲没有指定具体指令集
     - 历年统考真题主要考查的是 <span style="color: black;">x86</span>汇编指令
     - 因此本节主要介绍x86汇编指令 

</ul>

##  <span style="color: silver;">common<span style="color: green;">汇编</span><span style="color: LightSkyBlue;">指令</span>

<ul>

###  <span style="color: silver;">相关</span><span style="color: green;">R</span> 

<ul>

-  <span style="color: silver;">x86处理器有 <span style="color: black;">8个32位</span>的通用R
   - <span style="color: gray;">E</span><span style="color: DarkRed;">A</span>X、<span style="color: gray;">E</span><span style="color: LightSkyBlue;">B</span>X、<span style="color: gray;">E</span><span style="color: LimeGreen;">C</span>X和<span style="color: gray;">E</span><span style="color: deepskyblue;">D</span>X
     - 高两位字节和低两位字节可独立使用
     - E表示 <span style="color: black;">Extended</span>，表示 <span style="color: black;">32位</span><span style="color: green;">R</span> 
-  <span style="color: silver;">R <span style="color: LimeGreen;">命名</span>规则:
   - 以<span style="color: gray;">E</span><span style="color: DarkRed;">A</span>X为例:
    - 低两位字节称为<span style="color: DarkRed;">A</span>X
      - AX又可分为:
        - <span style="color: DarkRed;">A</span><span style="color: LightSkyBlue;">H</span> (高字节8位寄存器)
        - <span style="color: DarkRed;">A</span> <span style="color: LimeGreen;">L</span> (低字节8位寄存器)

![image](https://bluejedis.github.io/picx-images-hosting/test/image.491byvfcdd.webp)
 <span style="color: silver;">x86处理器中的主要寄存器及说明  
    
-  <span style="color: silver;">除E<span style="color: LightSkyBlue;">B</span><span style="color: GreenYellow;">P</span>和E<span style="color: LimeGreen;">S</span><span style="color: GreenYellow;">P</span>
   - 其他几个寄存器的用法比较灵活

</ul>

###  <span style="color: silver;">格式</span>  

<ul>

-  <span style="color: silver;">使用不同编程工具开发程序时，用到的汇编程序不同
   - 两种不同的汇编格式
     - AT&T格式 
     -  <span style="color: black;">Intel</span>格式（统考要求掌握）

</ul>

####  <span style="color: silver;">*主要 <span style="color: Gold;">区别</span>

<ul>

 <span style="color: silver;">

- 大小写要求
  - AT&T格式：指令只能用小写字母
  - Intel格式：指令对大小写不敏感

- 操作数顺序
  - AT&T格式：第一个为源操作数，第二个为目的操作数，方向从左到右
  - Intel格式：第一个为目的操作数，第二个为源操作数，方向从右向左

- 前缀使用
  - AT&T格式：寄存器需加前缀"$\omega_{0}$"，立即数需加前缀"$\S$"
  - Intel格式：寄存器和立即数都不需要加前缀

- 内存寻址符号
  - AT&T格式：使用"（"和")"
  - Intel格式：使用"["和"]"

- 复杂寻址方式
  - AT&T格式：disp(base,index,scale)
    - 如"8(%edx,%eax,2)"表示$\mathrm{M}[\mathrm{R}[\mathrm{edx}]+\mathrm{R}[\mathrm{eax}]^{*}2+8]$
  - Intel格式：对应为'$^{*}[\mathrm{edx+ex}^{*}2+8]$

- 数据长度指定
  - AT&T格式：操作码后加字符
    - "b"表示byte（字节）
    - "w"表示word（字）
    - "l"表示long（双字）
  - Intel格式：使用ptr
  *(pointer缩写)*
    - byte ptr
    - word ptr
    - dword ptr

>attention: 

由于32或64位体系结构都是由16位扩展而来的
因此用word（字）表示16位。  

- 汇编指令格式对比
  - mov指令
    - 功能：在内存和寄存器之间或者寄存器之间移动数据
  - lea指令
    - 功能：将一个内存地址（而不是其所指的内容）加载到目的寄存器

- 格式对比表
  - 表4.2 AT&T格式指令和Intel格式指令的对比

  ![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/49dd1199e96b48c53ff69b24837136b50fa7439742b0d9afe5606d78dc87dc74.jpg)  

- 符号说明
  - R[：表示寄存器r的内容
  - M[addr]：表示主存单元addr的内容
  - →或$\leftarrow$：表示信息传送方向

- 注意事项
  - 两种汇编格式可以相互转换，转换过程不复杂
  - 历年统考真题采用的均是 <span style="color: black;">Intel</span>格式
</span>

</ul>

</ul>

###  <span style="color: silver;">常用<span style="color: LightSkyBlue;">指令  

<ul>

 <span style="color: LimeGreen;">分类</span>：
- <span style="color: LightSkyBlue;">数据</span> <span style="color: LimeGreen;">传送</span>指令
- <span style="color: LightSkyBlue;">算术</span>和 <span style="color: Gold;">逻辑</span> <span style="color: LimeGreen;">运算</span>指令  
- <span style="color: orange;">控制</span><span style="color: LightSkyBlue;">流</span>指令

 <span style="color: silver;">以Intel格式为例:

####  <span style="color: LimeGreen;">操作</span><span style="color: LightSkyBlue;">数</span> <span style="color: silver;">标记说明

<ul>

 <span style="color: silver;">

-  <span style="color: black;">\<reg></span>： <span style="color: LimeGreen;">R</span>
   - \<reg32>：32位寄存器(eax,ebx,ecx,edx,esi,edi,esp或ebp)
   - \<reg16>：16位寄存器(ax,bx,cx或dx)
   - \<reg8>：8位寄存器(ah,al,bh,bl,ch,cl,dh,dl)
-  <span style="color: black;">\<mem></span>： <span style="color: Gold;">内存</span><span style="color: green;">地址</span>
   -  (如[eax]、[var + 4]或dword ptr[eax + ebx])
-  <span style="color: black;">\<con></span>：<span style="color: gray;">常数</span>
   - \<con8>：8位常数
   - \<con16>：16位常数
   - \<con32>：32位常数

</ul>

>pro：分析汇编指令对应的二进制代码（2010）  

#### x86<span style="color: LightSkyBlue;">指令</span><span style="color: silver;">机器码

<ul>

 <span style="color: silver;">

- 长度  <span style="color: black;">1Byte
- 同一指令有 <span style="color: black;">多种</span><span style="color: LightSkyBlue;">编码</span>方式
  - 如mov指令有28种机器编码
    - mov ax,\<con16> #机器码为B8H 
    - mov al,\<con8> #机器码为BOH
    - mov \<reg16>,\<reg16>/\<mem16> #机器码为89H
    - mov\<reg8>/\<mem8>,\<reg8> #机器码为8AH
    - mov\<reg16>/\<mem16>,\<reg16> #机器码为8BH

</ul>

>pro：模仿写出简单语句的机器级指令（2012）  

#### <span style="color: LightSkyBlue;">数据</span> <span style="color: LimeGreen;">传送</span> <span style="color: silver;">指令

<ul>

 <span style="color: silver;">

#####  <span style="color: LimeGreen;">mov
- 功能：将第二个操作数<span style="color: LightSkyBlue;">复制</span>到第一个操作数
- 语法：
  - mov\<reg>,\<reg>
  - mov\<reg>,\<mem>
  - mov\<mem>,\<reg>
  - mov\<reg>,\<con>
  - mov\<mem>,\<con>
- 举例：
  ```nasm
   mov eax,ebx ;将ebx 值复制到eax
   mov byte ptr [var],5 ;将5保存到 var值指示的内存地址的一字节中
- 注意：
  - 双OP 不能都是内存
    - 即 mov 指令can't 直接从内存复制to内存
      - can M →R→M

##### <span style="color: RoyalBlue;">push
- 功能：将操作数压<span style="color: RoyalBlue;">入</span><span style="color: Gold;">栈</span>
  - 常用于 函数调用
    - ESP is 栈顶
    - 入栈前先将 ESP - 4
- 语法：
  - push \<reg32>
  - push \<mem>
  - push \<con32>
- 举例：
  ```nasm
  push eax ;将 eax值入栈
  push [var] ;将 var值指示的内存地址'4Byte 值入栈
##### <span style="color: LightSkyBlue;">pop
- 功能：执行 <span style="color: LimeGreen;">出</span><span style="color: Gold;">栈</span>工作
  - 将 ESP指示的地址
中的内容出栈
  - ESP + 4
- 举例：
  
   ```nasm
    pop eax ;弹出栈顶元素送到eax
    pop [ebx] ;弹出栈顶元素送到ebx值指示的内存地址'4 Byte 中
  ```
</ul>

#### <span style="color: LightSkyBlue;">算术</span> <span style="color: silver;">和<span style="color: Gold;">逻辑</span> <span style="color: LimeGreen;">运算</span>指令

<ul>

 <span style="color: silver;">

#####  <span style="color: Gold;">add</span> <span style="color: silver;">/<span style="color: gray;">sub
- 功能：
  -  <span style="color: Gold;">add</span>：两操作数 <span style="color: Gold;">+
  - <span style="color: gray;">sub</span>：两操作数 <span style="color: gray;">-
- 语法：
  - add/sub\<reg>,\<reg>
  - add/sub\<reg>,\<mem>
  - add/sub\<mem>,\<reg>
  - add/sub\<reg>,\<con>
  - add/sub\<mem>,\<con>
- 举例：
  ```nasm
  sub eax,10 ;eax-eax-10
  add byte ptr[var],10 ;
  ```
#####  <span style="color: Gold;">inc</span> <span style="color: silver;">/<span style="color: gray;">dec
- 功能：
  - inc：自 <span style="color: Gold;">加</span>1
  - dec：自<span style="color: gray;">减</span>1
- 语法：
  - inc/dec\<reg>
  - inc/dec\<mem>
- 举例：
  - dec eax
  - inc dword ptr[var]

##### <span style="color: Goldenrod;">imul
- 功能：有符号整数<span style="color: Goldenrod;">乘</span>法
- 语法：
  - imul\<reg32>,\<reg32>
  - imul\<reg32>,\<mem>
  - imul\<reg32>,\<reg32>,\<con>
  - imul\<reg32>,\<mem>,\<con>
- 举例：
  - imul eax,[var]
  - imul esi,edi,25

##### <span style="color: RoyalBlue;">idiv
- 功能：有符号整数<span style="color: RoyalBlue;">除</span>法
- 语法：
  - idiv\<reg32>
  - idiv\<mem>
- 举例：
  - idivebx
  - idiv dword ptr[var]

#####  <span style="color: black;">and/or/xor
与 或 异或
- 功能： <span style="color: black;">位</span>操作
- 语法：
  - and/or/xor\<reg>,\<reg>
  - and/or/xor\<reg>,\<mem>
  - and/or/xor\<mem>,\<reg>
  - and/or/xor\<reg>,\<con>
  - and/or/xor\<mem>,\<con>
- 举例：
  - andeax,OfH
  - xoredx,edx

##### <span style="color: SlateBlue;">not
- 功能：位<span style="color: SlateBlue;">翻转
- 语法：
  - not\<reg>
  - not\<mem>
- 举例：
  - not byte ptr[var]

##### <span style="color: gray;">neg
- 功能：取<span style="color: gray;">负
- 语法：
  - neg\<reg>
  - neg\<mem>

#####  <span style="color: silver;">sh<span style="color: LimeGreen;">l</span>/sh<span style="color: LightSkyBlue;">r</span>
- 功能：
  - shl：逻辑 <span style="color: LimeGreen;">左</span>移
  - shr：逻辑<span style="color: LightSkyBlue;">右</span>移
- 语法：
  - shl/shr\<reg>,\<con8>
  - shl/shr\<mem>,\<con8>
  - shl/shr\<reg>,\<cl>
  - shl/shr\<mem>,\<cl>
- 举例：
  - shl eax,1
  - shr ebx,cl

</ul>

####  <span style="color: Gold;">控制</span><span style="color: LightSkyBlue;">流</span> <span style="color: silver;">指令

<ul>

 <span style="color: silver;">

- x86处理器维持着指令指针(IP)
  - IP自动指向下一条指令
  - 可用标签指示程序中的指令地址

>pro：无条件转移指令的指令格式（2021）  

#####  <span style="color: Gold;">jmp
- 功能：无条件跳转
- 语法：
  - jmp\<label>
- 举例：
  ```nasm
  jmp begin ;转跳到begin标记的指令执行
  ```
>pro：条件转移指令与标志位的结合（2013）  

##### j<span style="color: LimeGreen;">condition
- 功能： <span style="color: Gold;">条件</span><span style="color: green;">转移</span>
- 语法：
  - je\<label>  when equal ; =
  - jz\<label> ..last result was zero; = 0
  - jne\<label> ..not equal ;≠
  - jg\<label> .. greater than ; >
  - jge\<label> ..greater than or equal to ; ≥
  - jl\<label> ..less than; <
  - jle\<label> ..less than or equal to ; ≤
- 举例：
  ```nasm
  cmp eax,ebx
  jle done ;若eax值<=ebx值，则跳转到done 执行；
           ;否则执行NEXT指令
  ```
#####  <span style="color: Gold;">cmp</span> <span style="color: silver;">/<span style="color: Goldenrod;">test
- 功能：
  - cmp： <span style="color: Gold;">比较</span>操作
  - test：<span style="color: gray;">逐位</span><span style="color: orange;">与</span><span style="color: LimeGreen;">运算
- 语法：
  - cmp/test\<reg>,\<reg>
  - cmp/test\<reg>,\<mem>
  - cmp/test\<mem>,\<reg>
  - cmp/test\<reg>,\<con>
- cmp和 test指令
  - usually 与 jcondition指令搭配使
- 举例：
  ```nasm
  cmp dword ptr[var],10 ;将 var指示的主存地址的4字节内容，与10比较
  jne loop ;若相等则继续顺序执行：否则跳转到loop处执行
  test eax,eax ;测试eax是否为零
  jz xxxx ;为零则置标志 ZF为1,转跳到xxxx处执行
  ```
#####  <span style="color: LimeGreen;">call</span> <span style="color: silver;">/<span style="color: green;">ret
>pro：call指令的功能（2019）  
- 功能：
  - call：子程序 <span style="color: LimeGreen;">调用</span>
  - ret：子程序<span style="color: green;">返回
- 语法：
  - call\<label>
  - ret
- 特点：
  - call保存调用前地址
  - ret实现返回机制

</ul>

</ul>

</ul>

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
