<div style="float: left; width: 64%; padding: 1%;">

### <span style="color: LightSkyBlue;">格式</span>  

<span style="color: LightSkyBlue;">水平</span> <b>-</b> ; <span style="color: green;">垂直</span> <b>|</b>
↑ relative to 微程序

μ<span style="color: LightSkyBlue;">I</span>*μP=1 
↑ 要素制衡relation

<ul>

μ<span style="color: LightSkyBlue;">I</span> 格式与μ<span style="color: LightSkyBlue;">I</span> 的 <span style="color: deepskyblue;">编码</span>方式有关， 分为:
- 水平型~ 和 垂直型~
 
>pro： μ<span style="color: LightSkyBlue;">I</span> 后继 地址字段位数与μ<span style="color: LightSkyBlue;">I</span> 条数的关系（2014）  

#### <span style="color: LightSkyBlue;">水平</span> <span style="color: silver;">型~

<ul>

- 编码方式特点：
   - 水平型μ<span style="color: LightSkyBlue;">I</span> 包含以下编码方式：
    - <span style="color: gray;">直接</span>编码
    - <span style="color: LightSkyBlue;">字段</span><span style="color: gray;">直接</span>编码 
    - ~ <span style="color: silver;">间接</span>编码

- 格式结构：

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/b2aedaa58c557759dbd6b0fe7d9c754a7d34a84fc4317965518d9de55c2fb6a1.jpg) 

  - 控制信号<span style="color: LightSkyBlue;">编码</span>：
    - 每<span style="color: gray;">一位</span> <span style="color: Gold;">对应</span><span style="color: gray;">一个</span>控制信号
    - 信号状态：
      - 1 有输出
      - 0 无.
  -  <span style="color: Gold;">feature</span>：
     - <span style="color: gray;">单条 </span>μ<span style="color: LightSkyBlue;">I</span> 可同时：
       - 定义<span style="color: gray;">多个</span>微命令
       - 多个<span style="color: green;">并行</span>操作

 

- 优缺点：
  - 优：
    - 微程序 <span style="color: Gold;">短</span>，<span style="color: green;">并行</span>能力强，执行速度快
   - 缺点：
     - μ<span style="color: LightSkyBlue;">I</span> 长，编写微程序较<span style="color: gray;">麻烦

</ul>

#### <span style="color: green;">垂直</span> <span style="color: silver;">型~

<ul>

- 基本特点：
  - 编码方式：
    - 采用类似<span style="color: gray;">机器</span><span style="color: LightSkyBlue;">指令</span>操作码的 方式
  - μ<span style="color: LightSkyBlue;">I</span> 结构：
     - 在μ<span style="color: LightSkyBlue;">I</span> 字中设置微操作码字段
    - 基本格式参照图5.15
  - 执行特点：
     - 一条垂直型μ<span style="color: LightSkyBlue;">I</span> 通常只能：
      - 定义 执行 <span style="color: black;">一种</span>微命令

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/7065d0c6793931c03ff4fb46419e81a29e8a05e3dc173555b1f656c5aa397918.jpg)  

- 优缺点：
   - 优点：
     - μ<span style="color: LightSkyBlue;">I</span> 短、简单、规整，便于编写微程序
  - 缺点：
    - 微程序长，执行速度慢，效率低

</ul>

####  对比

<ul>

- 并行操作能力：
  - 水平型：强、效率高、灵活性强
  - 垂直型：较差
- 执行时间：
  - 水平型：短
  - 垂直型：长
- 微程序特点：
   - 水平型：μ<span style="color: LightSkyBlue;">I</span> 字较长但微程序短
  - 垂直型：相反
- 掌握难度：
  - 水平型：难以掌握
  - 垂直型：与机器指令比较相似，相对容易掌握
</ul>

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
